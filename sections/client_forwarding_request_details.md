
# Client Forwarding Request Status Page ⇄ [List](client_forwarding_requests_list.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/clients/some_client/forwarding_requests/1337.json
```

**For [betterplace.org clients](../README.md#client-api) only:**

After submitting a forwarding request, you can request a status of the asynchronous
forwarding job. It returns a JSON response, containing information about its status,
including failure reasons in the case of a failure.


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
    <td><code>some_client</code></td>
    <td>yes</td>
    <td>The betterplace.org-internal client permalink.</td>
  </tr>
  <tr>
    <th align="left">id</th>
    <td><code>1337</code></td>
    <td>yes</td>
    <td>          The ID of the forwarding request, normally returned within the
          response of a successful forwarding request POST.
</td>
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
    <tr>
      <th align="left">confirmed_at</th>
      <td>undefined</td>
      <td>2016-11-11T09:50:06+01:00</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">failed_at</th>
      <td>undefined</td>
      <td>2016-11-11T09:50:06+01:00</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">state</th>
      <td>string</td>
      <td>"confirmed"</td>
      <td>One of "pending", "confirmed" or "failed".
<ul>
<li><code>pending</code>
The system is still processing this donation.
Please check again soon.
<li><code>confirmed</code>
The donation is confirmed. This state is final.
<li><code>failed</code>
The donation failed. Please check the <code>failure_code</code>.
This state is final.
</ul>
</td>
    </tr>
    <tr>
      <th align="left">failure_code</th>
      <td>string</td>
      <td>pool_missing</td>
      <td>A set of failure codes.<br>
You could use this to choose follow up actions in
your application. More details about each error are
part of the <code>failure_reason</code>.
<ul>
<li><code>pool_missing</code> No pool available
<li><code>pool_empty</code> Not enough money on the pool
<li><code>receiver_prohibited_from_receiving_donations</code> The forwarding request's receiver may not receive donations
<li><code>donation_invalid</code> Generic error, look at <code>failure_reason</code> for details
</ul>
This list might be extended at any time. Please
make sure you receive a notification if you encounter
a new code. Codes will note be removed but might be
depricated and not used anymore at some point in the
future.
</td>
    </tr>
    <tr>
      <th align="left">failure_reason</th>
      <td>string</td>
      <td></td>
      <td>A more detailed description of the failure.<br>
This message is meant to be interpreted by a
developer, not by a customer/user.
The message might change at any time, don't
use it to match actions based on the message
string.
</td>
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
      <th align="left">donation</th>
      <td>Link to the related donation
(<a href="client_donation_details.md">client donation details</a>)
</td>
    </tr>
</table>

## Response Example

```json
{
  "id": 1,
  "created_at": "2016-12-05T14:43:28+01:00",
  "updated_at": "2016-12-05T14:43:29+01:00",
  "confirmed_at": "2016-12-05T14:43:29+01:00",
  "failed_at": null,
  "state": "confirmed",
  "failure_code": null,
  "failure_reason": null,
  "links": [
    {
      "rel": "donation",
      "href": "https://api.betterplace.org/de/api_v4/clients/particulate-sww/client_donations/HUdyvyq2P96vJ7cxgqgVD37D.json"
    }
  ]
}
```

