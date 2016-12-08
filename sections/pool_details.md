
# Pool Details

```Rebol
GET https://api.betterplace.org/de/api_v4/clients/payback/pool.json
```

The details of a betterplace.org client pool.

**For [betterplace.org clients](../README.md#client-api):**
Use this resource as follows: `/clients/PERMALINK/pool.json`


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">client_id</th>
    <td><code>payback</code></td>
    <td>yes</td>
    <td>The betterplace.org-internal client permalink.</td>
  </tr>
</table>


## Response Attributes

### Root Attributes

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">id</th>
      <td>number</td>
      <td>1</td>
      <td>An integer number ≥ 1</td>
    </tr>
    <tr>
      <th align="left">created_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">updated_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
  </table>
</table>

## Response Links

<table>
  <tr>
    <th>Linkname</th>
    <th>Description</th>
  </tr>

    <tr>
      <th align="left">self</th>
      <td>Link to this resource itself
(<a href="pool_details.md">pool details</a>)
</td>
    </tr>
</table>

## Response Example

```json
{
  "id": 4,
  "created_at": "2016-01-14T15:12:34+01:00",
  "updated_at": "2016-11-20T16:39:05+01:00",
  "links": [
    {
      "rel": "self",
      "href": "https://api.betterplace.org/de/api_v4/clients/payback/pool.json"
    }
  ]
}
```

