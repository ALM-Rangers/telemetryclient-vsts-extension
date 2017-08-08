# Track telemetry data for your Visual Studio Team Services (VSTS) extension ##

![VSTS](https://almrangers.visualstudio.com/_apis/public/build/definitions/7f3cfb9a-d1cb-4e66-9d36-1af87b906fe9/133/badge) | [![NPM](https://nodei.co/npm/telemetryclient-team-services-extension.png?mini=true)](https://www.npmjs.com/package/telemetryclient-team-services-extension)

Get insights in the usage of your extension by leveraging Microsoft Application Insights.
Data will only be tracked for extensions running in Visual Studio Team Services (VSTS). If your extension is installed in TFS On-Premise, the calls to Application Insights will be skipped.

See [How to integrate Application Insights monitoring in your Team Services extension](https://blogs.msdn.microsoft.com/visualstudioalmrangers/2017/05/30/how-to-integrate-application-insights-monitoring-in-your-team-services-extension/), which demonstrates how to integrate Application Insights telemetry in your extension by using this package.

# Getting Started

1. Install the package through npm: `npm install telemetryclient-team-services-extension`
2. In TypeScript, import the component:
    ```
    import * as tc from "TelemetryClient";
    ```
3. Create a configuration object for the telemetryclient. It should contain two values, like this:
    ```
    var settings: tc.TelemetryClientSettings = {
        key: "your-key-here",
        extensioncontext: "your-extension-context-here",
        disableTelemetry : "true" or "false",
        disableAjaxTracking  : "true" or "false",
        enableDebug  : "true" or "false"
    };
    ```
    - The `key` is your Application Insights instrumentation key.
    - The `extensioncontext` is the context for your extension. You can use it to differentiate between multiple extensions in the same Application Insights resource.
    - The `disableTelemetry` for enabled or disabled telemetry
    - The `disableAjaxTracking` for enabled or disabled dependencies Ajax disableAjaxTracking
    - The `enableDebug` for enabled or disabled debuging

    You can see an [sample on our extension](https://github.com/ALM-Rangers/Roll-Up-Board-Widget-Extension/blob/master/src/vsarVSTS-Roll-up-board/scripts/telemetryClientSettings.ts)

    [More info on API configuration](https://github.com/Microsoft/ApplicationInsights-JS/blob/master/API-reference.md#config)

4. Then you can track usage by calling the various methods:
    ```
     tc.TelemetryClient.getClient(settings).trackPageView()
     tc.TelemetryClient.getClient(settings).trackEvent()
     tc.TelemetryClient.getClient(settings).trackException()
     tc.TelemetryClient.getClient(settings).trackMetric()
    ```

# Prerequisites

- Visual Studio Team Services
- Application Insights resource in Azure

## Contributions

### Team

We thank the following contributor(s): **Kees Verhaar** and **Mikael Krief**

### Contributions are welcome

Here is how you can contribute to this project:  

- Submit bugs and help us verify fixes  
- Submit pull requests for bug fixes and features and discuss existing proposals   

Please refer to [Contribution guidelines](.github/CONTRIBUTING.md) and the [Code of Conduct](.github/COC.md) for more details.

### Notices

Building this solution will download other software, subject to the third party license terms that are between you and the third party.

And npm dependencies list are :

- [Typescript](https://www.npmjs.com/package/typescript)
- [ts-npm-lint](https://www.npmjs.com/package/ts-npm-lint)
- [applicationinsights-js](https://www.npmjs.com/package/applicationinsights-js)
- [vss-web-extension-sdk](https://www.npmjs.com/package/vss-web-extension-sdk)
