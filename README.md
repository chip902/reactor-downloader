# reactor-downloader

> [!NOTE]
> This is a standalone fork of the [@adobe/reactor-downloader](https://github.com/adobe/reactor-downloader) project, which is no longer being maintained. Kudos to @bbythewa and @mikeumus for building the original. Contributions welcome!

Command line tool for downloading a Launch property to a local directory.

## Usage and Installation

Running this tool is currently required to generate your `.reactor-settings.json` file for the Launch Property you want to use in [@adobe/reactor-sync](https://github.com/adobe/reactor-sync).  Before running the downloader tool, you must first have [Node.js](https://nodejs.org/en/) installed on your computer. Your npm version (npm comes bundled with Node.js) will need to be at least 10.15.0. You can check the installed version by running the following command from a command line:

```
npm -v
```


You will also need to be authorized to use the Launch APIs. This is done by first creating an integration through Adobe I/O. Please see the [Access Tokens Guide](https://developer.adobelaunch.com/api/guides/access_tokens/) for detailed steps on creating an integration and procuring api access rights.

Finally, you must first have created a property in Adobe Launch to download.

Once you have a property ready to download and have an integraton created through Adobe I/O that can access the Adobe Launch APIs, you can use the bootstrapper tool in either a question-answer format or by passing information through command line arguments.

### Question-Answer Format

To use the downloader in a question-answer format, run it by executing the following command from the command line:

```
npx @tyssejc/reactor-downloader
```

The tool will ask for any information necessary to download the repository.  If by chance you get an error when trying to run this command that is similar to `sh: reactor-downloader: command not found`, run the following command and try rerunning the script once done:

```
npm i -S @adobe/reactor-downloader
```

### Command Line Arguments

To skip any of the questions the downloader would typically ask, you can pass the respective information as command line arguments. An example is as follows:

```
npx @adobe/reactor-downloader --env=production --private-key=/Users/jane/launchkeys/reactor_integration_private.key --org-id=01C20D883A7D42080A494212@AdobeOrg --tech-account-id=14A533A72B181CF90A44410D@techacct.adobe.com --api-key=192ce541b1144160941a83vb74e0e74d --client-secret=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```

The named parameters are as follows:

##### --private-key (for authentication using an Adobe I/O integration)

The local path (relative or absolute) to the RSA private key. Instructions on how to generate this key can be found in the [Getting Started guide](https://developer.adobelaunch.com/api/guides/access_tokens/#authentication-for-each-session) and should have been used when creating your integration through the Adobe I/O console.

##### --org-id (for authentication using an Adobe I/O integration)

Your organization ID. You can find this on the overview screen for the integration you have created within the [Adobe I/O console](https://console.adobe.io).

##### --tech-account-id (for authentication using an Adobe I/O integration)

Your technical account ID. You can find this on the overview screen for the integration you have created within the [Adobe I/O console](https://console.adobe.io).

##### --api-key (for authentication using an Adobe I/O integration)

Your API key. You can find this on the overview screen for the integration you have created within the [Adobe I/O console](https://console.adobe.io).

##### --client-secret (for authentication using an Adobe I/O integration)

Your client secret. You can find this on the overview screen for the integration you have created within the [Adobe I/O console](https://console.adobe.io).

##### --env (for Adobe internal use only)

Unless you are an Adobe Employee inside of the Adobe Network, this parameter is technically optional.  This flag represents the environment where the property exists. Valid options are `development`, `qe`, `integration`, and `production`. Even if the Property is not hosting production code, always use `production`.

##### --save

A flag indicating whether to save the settings to a file for further use with other tools.  This saves from having to type in the above going forward.

##### --settings-path

The location to save the settings.  The file name should end in ".json".  (defaults to ./reactor-settings.json)

### Programmatic Functionality

Once you have the Reactor Downloader configured to work well on a one time basis, it's encouraged to use programatic functionality so that [@tyssejc](https://github.com/tyssejc)/reactor-sync can function as intended.

In order to facilitate this, you will need to generate keys using the guidelines that are set out by Adobe using this article: [Generating access tokens programmatically](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/#generating-access-tokens-programmatically)

## Suggested Uses

This tool can be used in many ways, but here are a few suggested uses:

- use in conjunction with [reactor-sync](https://github.com/tyssejc/reactor-sync).
- If you are already storing the code that goes into Launch in repositories, this tool will be your best friend.
  - bootstrap your repository with a current Launch Property and all of it's code without having to download everything from Launch manually.
- Run automated tests to ensure that your code doesn't have any obvious errors.
- Run transpiles on your code automatically and then automatically sync it into Launch.
- Run linters or code style enforcement tools to ensure that your code is always clean and you can always point to who is writing code in Launch that doesn't stay to standards.

If you have other use cases, let me know and I can update this list.

### Contributing

Contributions are welcomed! Read the [Contributing Guide](CONTRIBUTING.md) for more information.

## Licensing

This project is licensed under the Apache V2 License. See [LICENSE](LICENSE.md) for more information.
