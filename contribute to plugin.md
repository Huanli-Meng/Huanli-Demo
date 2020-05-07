This document describes how to submit a plugin to the StreamNative.

# Upload the source of the plugin

# Upload the NAR package of the plugin

# Upload plugin document

If a new plugin is introduced, you should upload the plugin document to the target category. Currently, the StreamNative supports the following categories for the plugin.

- Connector
- Data processing
- Logging
- Monitoring
- Authentication
- Deployment
- Handler
- Offloader
  
If a new category is required, you can create it. For details about how to create a new category, see [create new category](#create-new-category).

## Prepare for uploading plugin document

This section describes items need to be done before creating a PR for a plugin.

- Clone the [pulsar-registry-metadata](https://github.com/streamnative/pulsar-registry-metadata) repository to the local.
- Put the document under this [path](https://github.com/streamnative/pulsar-registry-metadata).
- Put the plugin image under this [path](https://github.com/streamnative/pulsar-registry-metadata/tree/master/images).

## Create new category

To create a new category, follow these steps:

1. Create a branch based on the latest [pulsar-registry-metadata](https://github.com/streamnative/pulsar-registry-metadata) master repository.
2. Create a sub-folder under the `pulsar-registry-metadata` folder in the local. Set the name of the sub-folder to the category name with lower cases. If the category name consists of multiple words, use the en-dash (-) between these words, such as `data-processing`.

## Create plugin document

To create a document for a new plugin, follow these steps:

1. Create a branch based on the latest [pulsar-registry-metadata](https://github.com/streamnative/pulsar-registry-metadata) master repository.
2. Create a document in the target folder for the plugin. For the document template about the plugin, see [plugin document template]().
3. Commit your updates, create a PR (Pull Request), and then publish the PR to the [pulsar-registry-metadata](https://github.com/streamnative/pulsar-registry-metadata) master repository.
4. Update comments, if any.
5. If no more comment, ask reviewers to approve the PR and merge the PR to the master.

