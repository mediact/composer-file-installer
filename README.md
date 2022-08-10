[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/mediact/composer-file-installer/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/mediact/composer-file-installer/?branch=master)

# [ABANDONED] composer-file-installer
Install files in a project as part of a `composer install` or `composer update`. Uses the [mediact/file-mapping](https://github.com/mediact/file-mapping) package for moving files according to a source -> destination mapping. The Composer `IOInterface` supplies the file installer with the capability to write the files and supply end-users with output messages.

## Usage example
```php
<?php
// Create a file mapping.
$mappingFilePaths = new UnixFileMapping(
     __DIR__ . '/../folder/files',
     getcwd(),
     ['./dir/one','./dir/two']

 );

// Get a file mapping reader.
$reader = new UnixFileMappingReader($sourceDirectory, $targetDirectory, $mappingFilePaths);

// Get an installer, supply with the file mapping reader.
$installer = new FileInstaller($reader);

// Install according to mapping, supply with Composer IOInterface.
$installer->install($io);
```
