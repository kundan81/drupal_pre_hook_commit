# drupal_pre_hook_commit
<h4>Installation instructions.</h4>
<h4>This is covered in the actual script as well, but for the sake of making it easy to find:</h4>
	cd [PATH TO DRUPAL GIT REPO]
	ln -s ../../scripts/pre-commit.sh .git/hooks/pre-commit

<h4> PHP_CodeSniffer is a set of two PHP scripts. the main phpcs script that tokenizes PHP, JavaScript and CSS files to detect violations of a defined coding standard, and a second phpcbf script to automatically correct coding standard violations. PHP_CodeSniffer is an essential development tool that ensures your code remains clean and consistent.</h4>

<h4> Checking the installed <a href="https://github.com/squizlabs/PHP_CodeSniffer">PHP CodeSniffer (phpcs)</a> and PHP 		Code <a href="https://github.com/squizlabs/PHP_CodeSniffer/wiki/Fixing-Errors-Automatically">Beautifier and Fixer 		(phpcbf)</a> program.</h4>
	$ ll ~/.composer/vendor/bin/
		total 8
		drwxrwxr-x  2 neeraj neeraj 4096 Jun  3 14:45 ./
		drwxrwxr-x 13 neeraj neeraj 4096 Jun  6 15:45 ../
		lrwxrwxrwx  1 neeraj neeraj   20 May 11 15:40 drush -> ../drush/drush/drush*
		lrwxrwxrwx  1 neeraj neeraj   24 May 11 15:40 drush.bat -> ../drush/drush/drush.bat*
		lrwxrwxrwx  1 neeraj neeraj   32 May 11 15:40 drush.complete.sh -> ../drush/drush/drush.complete.sh*
		lrwxrwxrwx  1 neeraj neeraj   29 May 11 15:40 drush.launcher -> ../drush/drush/drush.launcher*
		lrwxrwxrwx  1 neeraj neeraj   24 May 11 15:40 drush.php -> ../drush/drush/drush.php*
		lrwxrwxrwx  1 neeraj neeraj   43 Jun  3 14:45 phpcbf -> ../squizlabs/php_codesniffer/scripts/phpcbf*
		lrwxrwxrwx  1 neeraj neeraj   42 Jun  3 14:45 phpcs -> ../squizlabs/php_codesniffer/scripts/phpcs*
		lrwxrwxrwx  1 neeraj neeraj   33 May 11 15:40 php-parse -> ../nikic/php-parser/bin/php-parse*
		lrwxrwxrwx  1 neeraj neeraj   22 May 11 15:40 psysh -> ../psy/psysh/bin/psysh*


<h4>Install the Coder module using Composer.</h4>
	$ composer global require drupal/coder

<h4>However, both programs are not within Bash's program search path. Hence, we have to add it manually.</h4>
	To make it permanent, just put this line into ~/.bashrc or ~/.profile file.
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
		The installed coding standards are PSR1, PHPCS, Squiz, PSR2, Zend, PEAR, MySource, Drupal and DrupalPractice.

<h4>if you are not able to find Drupal & DrupalPractice when fire phpcs -i command then use this command</h4>

	cp -R ~/.composer/vendor/drupal/coder/coder_sniffer/Drupal ~/.composer/vendor/squizlabs/php_codesniffer/CodeSniffer/Standards/
	cp -R ~/.composer/vendor/drupal/coder/coder_sniffer/DrupalPractice ~/.composer/vendor/squizlabs/php_codesniffer/CodeSniffer/Standards/



