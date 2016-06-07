# drupal_pre_hook_commit

## PHP_CodeSniffer is a set of two PHP scripts. the main phpcs script that tokenizes PHP, JavaScript and CSS files to 		detect violations of a defined coding standard, and a second phpcbf script to automatically correct coding standard 	violations. PHP_CodeSniffer is an essential development tool that ensures your code remains clean and consistent.

## Checking the installed PHP CodeSniffer (phpcs) and PHP Code Beautifier and Fixer (phpcbf) program.
	ll ~/.composer/vendor/bin/

## Install the Coder module using Composer.
	composer global require drupal/coder

##	However, both programs are not within Bash's program search path. Hence, we have to add it manually.
	$ export PATH=$PATH:$HOME/.composer/vendor/bin

##	To verify our path has been set up correctly.
	$ which phpcs
		~/.composer/vendor/bin/phpcs

## 	To test whether a sample code is adhere to Drupal coding standard. As shown below, the phpcs program can't find the 	Drupal coding standard rules file.
	$ phpcs --standard=Drupal drupal-examples/action_example/action_example.module
		ERROR: the "Drupal" coding standard is not installed. The installed coding standards are PSR1, PHPCS, Squiz, PSR2, Zend, PEAR and MySource

## 	Set the path to the Drupal coding standard rules path and verify again.
	$ phpcs --config-set installed_paths ~/.composer/vendor/drupal/coder/coder_sniffer
		Config value "installed_paths" added successfully

	$ phpcs -i
		The installed coding standards are PSR1, PHPCS, Squiz, PSR2, Zend, PEAR, MySource, Drupal and DrupalPractice

