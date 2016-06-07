# drupal_pre_hook_commit

<h4> PHP_CodeSniffer is a set of two PHP scripts. the main phpcs script that tokenizes PHP, JavaScript and CSS files to detect violations of a defined coding standard, and a second phpcbf script to automatically correct coding standard violations. PHP_CodeSniffer is an essential development tool that ensures your code remains clean and consistent.</h4>

<h4> Checking the installed <a href="https://github.com/squizlabs/PHP_CodeSniffer">PHP CodeSniffer (phpcs)</a> and PHP 		Code <a href="https://github.com/squizlabs/PHP_CodeSniffer/wiki/Fixing-Errors-Automatically">Beautifier and Fixer 		(phpcbf)</a> program.</h4>
	$ ll ~/.composer/vendor/bin/

<h4>Install the Coder module using Composer.</h4>
	$ composer global require drupal/coder

<h4>However, both programs are not within Bash's program search path. Hence, we have to add it manually.</h4>
	$ export PATH=$PATH:$HOME/.composer/vendor/bin

<h4>To verify our path has been set up correctly.</h4>
	$ which phpcs
		~/.composer/vendor/bin/phpcs

<h4>To test whether a sample code is adhere to Drupal coding standard. As shown below, the phpcs program can't find the 	Drupal coding standard rules file.</h4>
	$ phpcs --standard=Drupal drupal-examples/action_example/action_example.module
		ERROR: the "Drupal" coding standard is not installed. The installed coding standards are PSR1, PHPCS, Squiz, PSR2, Zend, PEAR and MySource

<h4>Set the path to the Drupal coding standard rules path and verify again.</h4>
	$ phpcs --config-set installed_paths ~/.composer/vendor/drupal/coder/coder_sniffer
		Config value "installed_paths" added successfully

	$ phpcs -i
		The installed coding standards are PSR1, PHPCS, Squiz, PSR2, Zend, PEAR, MySource, Drupal and DrupalPractice

