Execute:

```
rm -f web/typo3conf/LocalConfiguration.php web/typo3conf/PackageStates.php && ./vendor/bin/typo3cms install:setup --database-socket="" --site-name="Site"  --non-interactive

```

`--site-name` is treated as argument to `--database-socket` when `--database-socket` has an empty string added via equals sign. To demonstrate that this demo patches a printf into helhum/typo3-console.
Output of above command on Fedora Linux:


```
[typo3-console-arguments-bug] $ rm -f web/typo3conf/LocalConfiguration.php web/typo3conf/PackageStates.php && ./vendor/bin/typo3cms install:setup --database-socket="" --site-name="Site"  --non-interactive
array(4) {
  [0]=>
  string(13) "install:setup"
  [1]=>
  string(18) "--database-socket="
  [2]=>
  string(16) "--site-name=Site"
  [3]=>
  string(17) "--non-interactive"
}

Welcome to the TYPO3 Console installer!
Array
(
    [databaseSocket] => --site-name
    [nonInteractive] => 1
)

Check environment / create folders:
OK

Connect to database:

 [ Helhum\Typo3Console\Mvc\Cli\FailedSubProcessCommandException ]
 #1485130941: Executing "install:databaseconnect" "'/usr/bin/php' './vendor/bin/typo3cms' 'install:databaseconnect' '--database-socket' '--site-name'" failed (exit code: "1") with message:

"[ TYPO3\CMS\Extbase\Property\Exception ]
 #1297759968: Exception while property mapping at property path "": No converter found which can be used to convert from "boolean" to "string".
 thrown in file typo3/sysext/extbase/Classes/Property/PropertyMapper.php
 in line 127


Exception trace:
#0 TYPO3\CMS\Extbase\Property\PropertyMapper::convert()
   typo3/sysext/extbase/Classes/Mvc/Controller/Argument.php:270
#1 TYPO3\CMS\Extbase\Mvc\Controller\Argument::setValue()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Mvc/Controller/CommandController.php:195
#2 Helhum\Typo3Console\Mvc\Controller\CommandController::mapRequestArgumentsToControllerArguments()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Mvc/Controller/CommandController.php:136
#3 Helhum\Typo3Console\Mvc\Controller\CommandController::processRequest()
   typo3/sysext/extbase/Classes/Mvc/Dispatcher.php:85
#4 TYPO3\CMS\Extbase\Mvc\Dispatcher::dispatch()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Mvc/Cli/RequestHandler.php:80
#5 Helhum\Typo3Console\Mvc\Cli\RequestHandler::handleRequest()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Core/ConsoleBootstrap.php:110
#6 Helhum\Typo3Console\Core\ConsoleBootstrap::run()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Scripts/typo3cms.php:56
#7 {closure}()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Scripts/typo3cms.php:57
#8 require()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Scripts/typo3cms:4


 [ TYPO3\CMS\Extbase\Property\Exception\TypeConverterException ]
 #1476044883: No converter found which can be used to convert from "boolean" to "string".
 thrown in file typo3/sysext/extbase/Classes/Property/PropertyMapper.php
 in line 250


Exception trace:
#0 TYPO3\CMS\Extbase\Property\PropertyMapper::findTypeConverter()
   typo3/sysext/extbase/Classes/Property/PropertyMapper.php:166
#1 TYPO3\CMS\Extbase\Property\PropertyMapper::doMapping()
   typo3/sysext/extbase/Classes/Property/PropertyMapper.php:118
#2 TYPO3\CMS\Extbase\Property\PropertyMapper::convert()
   typo3/sysext/extbase/Classes/Mvc/Controller/Argument.php:270
#3 TYPO3\CMS\Extbase\Mvc\Controller\Argument::setValue()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Mvc/Controller/CommandController.php:195
#4 Helhum\Typo3Console\Mvc\Controller\CommandController::mapRequestArgumentsToControllerArguments()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Mvc/Controller/CommandController.php:136
#5 Helhum\Typo3Console\Mvc\Controller\CommandController::processRequest()
   typo3/sysext/extbase/Classes/Mvc/Dispatcher.php:85
#6 TYPO3\CMS\Extbase\Mvc\Dispatcher::dispatch()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Mvc/Cli/RequestHandler.php:80
#7 Helhum\Typo3Console\Mvc\Cli\RequestHandler::handleRequest()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Core/ConsoleBootstrap.php:110
#8 Helhum\Typo3Console\Core\ConsoleBootstrap::run()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Scripts/typo3cms.php:56
#9 {closure}()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Scripts/typo3cms.php:57
#10 require()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Scripts/typo3cms:4"

and error:

""

 thrown in file /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Mvc/Cli/FailedSubProcessCommandException.php
 in line 44


Exception trace:
#0 Helhum\Typo3Console\Mvc\Cli\FailedSubProcessCommandException::forProcess()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Mvc/Cli/CommandDispatcher.php:165
#1 Helhum\Typo3Console\Mvc\Cli\CommandDispatcher::executeCommand()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Install/CliSetupRequestHandler.php:231
#2 Helhum\Typo3Console\Install\CliSetupRequestHandler::executeActionWithArguments()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Install/CliSetupRequestHandler.php:194
#3 Helhum\Typo3Console\Install\CliSetupRequestHandler::dispatchAction()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Install/CliSetupRequestHandler.php:118
#4 Helhum\Typo3Console\Install\CliSetupRequestHandler::setup()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Command/InstallCommandController.php:90
#5 Helhum\Typo3Console\Command\InstallCommandController::setupCommand()
#6 call_user_func_array()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Mvc/Controller/CommandController.php:252
#7 Helhum\Typo3Console\Mvc\Controller\CommandController::callCommandMethod()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Mvc/Controller/CommandController.php:137
#8 Helhum\Typo3Console\Mvc\Controller\CommandController::processRequest()
   typo3/sysext/extbase/Classes/Mvc/Dispatcher.php:85
#9 TYPO3\CMS\Extbase\Mvc\Dispatcher::dispatch()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Mvc/Cli/RequestHandler.php:80
#10 Helhum\Typo3Console\Mvc\Cli\RequestHandler::handleRequest()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Classes/Core/ConsoleBootstrap.php:110
#11 Helhum\Typo3Console\Core\ConsoleBootstrap::run()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Scripts/typo3cms.php:56
#12 {closure}()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Scripts/typo3cms.php:57
#13 require()
   /home/ben/src/typo3-console-arguments-bug/vendor/helhum/typo3-console/Scripts/typo3cms:4

```
