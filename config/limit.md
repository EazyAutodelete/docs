---
description: The limit with which the deletion algorithm should work.
---

# ⌛ Limit

This value specifies the time or number of messages after which messages are deleted

Depending on the mode, the input is either a duration or a simple number.

{% hint style="info" %}
For Mode 1 and 2: If a message gets edited and only meets the filters after the change, the time from sending the message is still used to calculate when to delete the message. This might lead to a message being deleted immediately after getting edited.
{% endhint %}

## Specifying the limit for different modes

{% tabs %}
{% tab title="Mode 1" %}
Specified as a duration.

{% hint style="warning" %}
The duration must be more than 10 seconds and less than 7 days
{% endhint %}
{% endtab %}

{% tab title="Mode 2" %}
Specified as a duration.

{% hint style="warning" %}
The duration must be more than 10 seconds and less than 7 days
{% endhint %}
{% endtab %}

{% tab title="Mode 3" %}
Specified as a simple number.

{% hint style="warning" %}
The number must be between 3 and 75.
{% endhint %}
{% endtab %}

{% tab title="Mode 4" %}
Specified as a simple number.

{% hint style="warning" %}
The number must be between 3 and 50.
{% endhint %}
{% endtab %}
{% endtabs %}

## How to specify durations

| Use of time units             | Correct use      | Incorrect use |
| ----------------------------- | ---------------- | ------------- |
| seconds: `s`, `sec`, `secs`   | `1mins 30sec`    | `1m30s`       |
| minutes: `m`, `min`, `mins`   | `5mins`          | `2,3h`        |
| hours: `h`, `hr`, `hrs`       | `2hrs 3m`        | `1d6h3m`      |
| days: `d`, `day`, `days`      | `1days 6hr 3min` | `1d 6hsr 3n`  |

