# Endpoints

## 👉 Get token details by chain ID and token address

<mark style="color:green;">`GET`</mark> `/{chainId}/{address}`

We recommend using this endpoint over the next one if you are working on a specific chain as requesting by address only can return more than one result if there are other token with the same address on other chains.

{% hint style="info" %}
You can pass checksum and non-checksum addresses
{% endhint %}

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |

**Body**

| Name      | Type    | Description     |
| --------- | ------- | --------------- |
| `chainId` | integer | Chain number ID |
| `address` | string  | Token address   |

**Response**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "name": "Uniswap",
        "logoURI": "https://xkqpczltzicnmbqvihbc.supabase.co/storage/v1/object/public/logos/uni_7687.png",
        "symbol": "uni",
        "chainId": 1,
        "decimals": 18,
        "address": "0x1f9840a85d5af5bf1d1762f925bdaddc4201f984",
        "chain": "ethereum"
    }
]
```
{% endtab %}

{% tab title="400" %}
```json
{
"error":"No data found {address} on chain {chainId}"
}
```
{% endtab %}
{% endtabs %}

## 👉 Get token details by address

<mark style="color:green;">`GET`</mark> `/{address}`

\<Description of the endpoint>

**Headers**

| Name          | Value              |
| ------------- | ------------------ |
| Content-Type  | `application/json` |
| Authorization | `Bearer <token>`   |

**Body**

| Name      | Type   | Description   |
| --------- | ------ | ------------- |
| `address` | string | Token address |

**Response**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "name": "Uniswap",
        "logoURI": "https://xkqpczltzicnmbqvihbc.supabase.co/storage/v1/object/public/logos/uni_7687.png",
        "symbol": "uni",
        "chainId": 1,
        "decimals": 18,
        "address": "0x1f9840a85d5af5bf1d1762f925bdaddc4201f984",
        "chain": "ethereum"
    }
]
```
{% endtab %}

{% tab title="400" %}
```json
{
"error":"No data found for {address}"
}
```
{% endtab %}
{% endtabs %}
