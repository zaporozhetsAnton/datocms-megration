##DatoCMS migration script

Script that migrates all fields/blocks/models from one DatoCMS environment to another.

On the production environment we should only work with content, and we shouldn't update any blocks, models, fields.
Blocks, models, fields should be transferred from sandbox environment to production environment.
This migration code only transfers blocks, models and fields that were created/updated/deleted.
It can be improved, for example transferring content menu structure could be useful.
If you have got an error during the fields migration step most of all you should take a look at the changeFieldValidators function, maybe your field has a validation rule that the current function doesn't handle.

###Installation steps

``npm i -D datocms-client``

Add migration.js to the root folder of your project.

###Migration steps

1 In DatoCMS admin panel, turn on maintenance mode.

2 In DatoCMS admin panel, fork production environment and call it migration-test.

3 Run migration script.

4 In DatoCMS admin panel, check was everything transferred from the development sandbox to the migration-test sandbox.

5 In migration.js file, if test migration finished successfully change productionEnv value to 'production' and run migration again.

6 In DatoCMS admin panel, check production environment.

7 In DatoCMS admin panel, remove migration-test environment.

8 In DatoCMS admin panel, disable maintenance mode.

PS this guide should work if you have at list development and production environments in your DatoCMS project and also DATOCMS_READWRITE_TOKEN variable in your .env.local file that should be added to gitignore.
