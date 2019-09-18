# NAIS

## What is NAIS?

NAIS is an open source application platform that aims to provide our developers with the best possible tools needed to develop and run their applications.

{% code-tabs %}
{% code-tabs-item title="hello\_world.py" %}
```python
print("hello world")
```
{% endcode-tabs-item %}

{% code-tabs-item title="index.html" %}
```markup
<h1>hello world</h1>
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% api-method method="delete" host="https://daemon.nais.preprod.local/app" path="/namespace/app" %}
{% api-method-summary %}
Delte Naisd app
{% endapi-method-summary %}

{% api-method-description %}
When using Naisd, the only way to remove your application is to use the delete-endpoint. This will remove all the Kubernetes resources made for your application.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="namespace" type="string" required=true %}
name of namespace
{% endapi-method-parameter %}

{% api-method-parameter name="app" type="string" required=true %}
name of app
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Done
{% endapi-method-response-example-description %}

```
result:
service: OK
deployment: OK
redis: N/A
secret: OK
ingress OK
autoscaler: OK
alert rules: OK
service account: OK
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}
Failed
{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="Yes" %}
Some text
{% endtab %}

{% tab title="No" %}
Other tab
{% endtab %}
{% endtabs %}

## Why NAIS exists

When you have a large development organisation, providing the developers with turnkey solutions for their most common needs can be a good investment.

This includes \(but not limited to\) [logging](observability/logs.md), [metrics](observability/metrics.md), [alerts](https://github.com/nais/doc/tree/8b3093ddc069e75f7b9cd3dd991e8d1e6c83c756/observability/alerts.md), [deployment](basics/deploy.md) and a [runtime environment](./#nais-clusters).

Within each of these aspects, we leverage open source projects best suited for our needs and provide them with usable abstractions, sane defaults and the required security hardening.

## NAIS clusters

NAIS is a platform spread over two different suppliers. One set of clusters on-premise, and another set running in the cloud \(namely Google Cloud Platform\).

### On-premise

The on-premise clusters are split into two zones, _selvbetjeningsonen_ \(SBS\), _fagsystemsonen_ \(FSS\).

| cluster | ingresses |
| :--- | :--- |
| dev-fss | nais.preprod.local |
| prod-fss | nais.adeo.no |
| dev-sbs | nais.oera-q.no |
| prod-sbs | nais.oera.no, tjenester.nav.no |

Example: If your app is named `myapp`, then the URL for `dev-fss` would be `https://my-app.nais.preprod.local/`.

{% hint style="info" %}
Remember `https://` when calling on-premise URLs!
{% endhint %}

{% hint style="warning" %}
We are working on moving away from the `preprod` prefix, so use `dev` where possible. Read more about the decision over at [pig-kubernetes-ops](https://github.com/navikt/pig/blob/master/PIG-Kubernetes-OPS/adr/000-preprod-rename.md).
{% endhint %}

### Cloud - Google Cloud Platform \(GCP\)

For the cloud there are no zones. Instead, we rely on a zero-trust model with a service-mesh.

| cluster | ingresses |
| :--- | :--- |
| dev-gcp | dev-adeo.no, dev-nais.no |
| prod-gcp | adeo.no |

## Contact the NAIS team

The team can be found either on [Slack](https://nav-it.slack.com/messages/C5KUST8N6/) or in Sannergata 2, 3rd floor, west wing.

Also, follow us on Twitter [@nais\_io](https://twitter.com/nais_io)!

