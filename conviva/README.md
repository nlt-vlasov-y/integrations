# ![](./img/integration_conviva.png) Conviva

- [Description](#description)
- [Requirements and Dependencies](#requirements-and-dependencies)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Metrics](#metrics)
- [License](#license)

### DESCRIPTION

<a target="_blank" href="https://www.conviva.com/">Conviva</a> is a service for monitoring video playing experience on the Internet. The <a target="_blank" href="https://github.com/signalfx/integrations/tree/master/signalfx-agent">SignalFx Smart Agent</a> monitor called **conviva** was developed for Conviva integration. The conviva monitor can be configured to pull [Real-time/Live Conviva metrics](./docs/conviva_live_metrics.md) using the <a target="_blank" href="https://community.conviva.com/site/global/apis_data/experience_insights_api/index.gsp">Conviva Experience Insights REST APIs</a>. The Live Conviva metrics are converted to SignalFx metrics with dimensions for the name of the Conviva account and the name(s) of the applied filter(s). MetricLens metrics have an additional dimension called metric that identifies the metric of a MetricLens. Also, MetricLens dimensions are mapped one-to-one to SignalFx dimensions with their values derived from the values of the associated MetricLens dimension entities.

### REQUIREMENTS AND DEPENDENCIES

Only Live Conviva metrics are supported. Conviva MetricLens metrics require MetricLens enabled filters. MetricLens enable filters have a checkmark in the `ML` column of the table <a target="_blank" href="https://pulse.conviva.com/filters/">here</a>. Conviva Developer Community credentials are required to access this link.

This monitor requires:

| Software          | Version        |
|-------------------|----------------|
| Conviva Experience Insights API |     2.4+       |

### INSTALLATION

Install the latest version of the SignalFx Smart Agent as described [here](https://github.com/signalfx/integrations/tree/master/signalfx-agent).

### CONFIGURATION

Find and edit the SignalFx Smart Agent configuration file `agent.yaml` to configure the conviva monitor as described <a target="_blank" href="https://github.com/signalfx/signalfx-agent/blob/master/docs/monitors/conviva.md">here</a>.

### USAGE

>Below is a screen capture of an example SignalFx dashboard, illustrating the metrics emitted by this plugin. The dashboard is included in this repository, and can be imported into SignalFx or other monitoring product. [Click here to download](././Page_Example Python Plugin.json).
>
>![Example dashboard showing metrics from this plugin](././img/example_plugin_dashboard.png)

#### Important conditions to watch out for

The Conviva API response may return with filters listed in fields **filters_not_exist**, **filters_warmup** and **filters_incomplete_data**. This means data for these filters may be wholly or partially unavailable. When this happens it is logged in the SignalFx Smart Agent log file.

Configuration validation will fail when a non MetricLens enabled filter is listed in a MetricLens metric configuration.

The select all filters in combination with select all dimensions options should be used with care because of the potential to generate a large amount of datapoints.

### METRICS

For documentation of the metrics and dimensions emitted by this plugin, [click here](./docs).

### LICENSE

This integration is released under the Apache 2.0 license. See [LICENSE](./LICENSE) for more details.