---
description: How the deletion algorithm works
---

# ⚙ Mode

Currently 5 different modes are supported.

{% hint style="warning" %}
You have to set a new [limit](limit.md) when you change the mode.
{% endhint %}

{% tabs %}
{% tab title="Mode 0" %}
Disables the deletion algorithm in the specified channel.
{% endtab %}

{% tab title="Mode 1" %}
Deletes the sent message after the given time.

<figure><img src="https://cdn.eazyautodelete.xyz/assets/2d3cfd88-4ed5-4ca0-b554-21670e81742a" alt=""><figcaption><p>Deletes a sent message after 10 seconds</p></figcaption></figure>
{% endtab %}

{% tab title="Mode 2" %}
Deletes all messages in the specified channel after the given time.
{% endtab %}

{% tab title="Mode 3" %}
Deletes all messages after a given amount of messages was sent.
{% endtab %}

{% tab title="Mode 4" %}
Keeps a defined number of new messages and deletes the messages before.
{% endtab %}
{% endtabs %}
