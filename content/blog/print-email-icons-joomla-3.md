Date: 2013-04-12
Title: Print/Email Icons in Joomla 3.0
Tags: code joomla howto
Author: Ben Jacobs

We use [Joomla CMS][joomla] to run several sites at work. In version 3.0 they made the great decision to make the stock templates based on the [Twitter Bootstrap][bootstrap]. I'm a big fan of Bootstrap because it helps me get looking presentable in a short amount of time. I rewrote a couple of our Joomla templates starting with Protostar, the Joomla 3 default template that uses bootstrap.

Joomla's default configuration puts print and email icons on every article. In older versions of Joomla, these were tiny little individual icons, but in Protostar they're "dropdown button group" with a gears icon. This is obtrusive and takes up a decent amount of screen real-estate. It's also very distracting in the blog layout where the icon is displayed over and over again.

Joomla comes with a built-in mechanism for overriding component templates (see [How to override the output from the Joomla! core][override]). Like everything else in Joomla, it hinges on getting the directory structures correct. To override a component template, you need to create a subdirectory in your template in the format `TEMPLATE/html/COMPONENT_NAME/VIEWNAME/`. Then you simple copy the `php` template from the component into this directory. (Also, make sure that your `html` directory is included in your template's `xml` manifest).

The print/email icons appear in three templates, all within `com_content`:

	joomla/components/com_content/views/article/tmpl/default.php
	joomla/components/com_content/views/category/tmpl/blog_item.php
	joomla/components/com_content/views/featured/tmpl/default_item.php

Copy these into the template directory as stated above. You can then edit these files to your choosing. Search for 'show_print_icon' and edit away. I replaced mine with the following

	<div class="pull-right">
		<ul class="unstyled article-icons">
			<?php if ($params->get('show_print_icon')) : ?>
			<li class="print-icon"><?php echo JHtml::_('icon.print_popup', $this->item, $params); ?></li>
			<?php endif; ?>
			<?php if ($params->get('show_email_icon')) : ?>
			<li class="email-icon"><?php echo JHtml::_('icon.email', $this->item, $params); ?></li>
			<?php endif; ?>
			<?php if ($canEdit) : ?>
			<li class="edit-icon"><?php echo JHtml::_('icon.edit', $this->item, $params); ?></li>
			<?php endif; ?>
		</ul>
	</div>

I also added a `.article-icons` class. From my *template.less*:

	ul.article-icons {
		li {
			display: inline;
		}
		a {
			color: @grayLight;
			&:hover {
				color: @grayDarker;
			}
		}
	}

The finished product looks like this. Simple, but much better!

![Joomla Icons Screenshot](./images/joomla-icons-after.png)

[joomla]: http://www.joomla.org
[bootstrap]: http://twitter.github.io/bootstrap/index.html
[override]: http://docs.joomla.org/How_to_override_the_output_from_the_Joomla!_core