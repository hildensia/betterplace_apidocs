
# Client Donations List ⇄ [Details](client_donation_details.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations.json?facets=client_reference%3A922ec9b-etc
```

**For [betterplace.org clients](../README.md#client-api) only:**

This API returns all donations to all client projects that where made using
the client donation form (but none of the other donation-sources).

Results are contained in a *data* attribute.


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
    <td><code>volksfreund</code></td>
    <td>yes</td>
    <td>The betterplace.org-internal client permalink.</td>
  </tr>
  <tr>
    <th align="left">facets</th>
    <td><code>client_reference:922ec9b-etc</code></td>
    <td>no</td>
    <td>You can search for a specific client_reference: <code>?facets=client_reference:54</code>

<br>
Example:
<a href="https://api.betterplace.org/en/api_v4/clients/karmic_minion/client_donations?facets=client_reference:54">
  <code>https://api.betterplace.org/en/api_v4/ clients/karmic_minion/ client_donations?facets=client_reference:54</code>
</a>

<br>
This feature is only used in some cases that relate to the
<a href="../donation_form/third_party_app_donation_form.md">ThirdPartyApp custom donation form for organisations</a>
and the <a href="client_donation_pledges.md">Client donation pledge endpoint</a>.
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
      <th align="left">amount_in_cents</th>
      <td>number</td>
      <td>10100</td>
      <td>Donated amount in cents</td>
    </tr>
    <tr>
      <th align="left">state</th>
      <td>string</td>
      <td>"confirmed"</td>
      <td>At the moment, all donations that are returned by the API are "confirmed".
Unconfirmed donations do not show up at all or disappear after they were revoked.
Revocations usually take place during the first 14 days – but there are no guarantees.

Please make sure to check for the "confirmed" state in your application explicitly since
we might add a "revoked" state in the future.
</td>
    </tr>
    <tr>
      <th align="left">token</th>
      <td>string</td>
      <td>ofMmTgfiPL-n1dDlNmFWqTQN</td>
      <td>A token uniquely identifies a donation on the platform.
</td>
    </tr>
    <tr>
      <th align="left">client_reference</th>
      <td>string</td>
      <td>922ec9b-etc</td>
      <td>Client Donations can be identified via a custom client reference token.

This <code>donation_client_reference</code> can be provided by users of our
<a href="../donation_form/third_party_app_donation_form.md">
ThirdPartyApp custom donation form for organisations</a>, for example.
</td>
    </tr>
    <tr>
      <th align="left">created_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">receiver_type</th>
      <td>string</td>
      <td>"Project"</td>
      <td>Client donations may go to a <code>Project</code>,
a Project's <code>Element</code>, a <code>FundraisingEvent</code>,
a <code>Pool</code>.
</td>
    </tr>
    <tr>
      <th align="left">receiver_id</th>
      <td>number</td>
      <td>1114</td>
      <td>The id of the project, project element or fundraising event.</td>
    </tr>
    <tr>
      <th align="left">receiver_title</th>
      <td>string</td>
      <td>"Skateistan Afghanistan"</td>
      <td>The title of the project, project element or fundraising event.</td>
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
      <th align="left">receiver</th>
      <td>Link to the <a href="project_details.md">project details</a>,
<a href="need_details.md">project need details</a>,
<a href="fundraising_event_details.md">fundraising event details</a>,
that is associated with this donation.<br>
Right now, there is no api end point for donations that are
redirect or donated to the client pool.
</td>
    </tr>
    <tr>
      <th align="left">self</th>
      <td>Link to this resource itself
(<a href="client_donation_details.md">client donation details</a>)
</td>
    </tr>
    <tr>
      <th align="left">donor_contact_data</th>
      <td>Link to the donor contact data
(<a href="donor_contact_data_details.md">donor contact data details</a>)
</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 15625,
  "offset": 0,
  "total_pages": 5209,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "amount_in_cents": 1000,
      "state": "confirmed",
      "token": "328db52eb745be52f3b5aaf0",
      "client_reference": null,
      "created_at": "2010-10-28T14:44:49+02:00",
      "receiver_type": "Project",
      "receiver_id": 4807,
      "receiver_title": "Kleinbus für den Palais e.V. Trier",
      "links": [
        {
          "rel": "receiver",
          "href": "https://api.betterplace.org/de/api_v4/projects/4807.json"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/328db52eb745be52f3b5aaf0.json"
        },
        {
          "rel": "donor_contact_data",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/328db52eb745be52f3b5aaf0/donor_contact_data.json"
        }
      ]
    },
    {
      "amount_in_cents": 100,
      "state": "confirmed",
      "token": "7d775febc93584375ab07136",
      "client_reference": null,
      "created_at": "2010-10-28T17:48:16+02:00",
      "receiver_type": "Project",
      "receiver_id": 4798,
      "receiver_title": "Hilfe für Jugendliche mit krebskranken Eltern",
      "links": [
        {
          "rel": "receiver",
          "href": "https://api.betterplace.org/de/api_v4/projects/4798.json"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/7d775febc93584375ab07136.json"
        },
        {
          "rel": "donor_contact_data",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/7d775febc93584375ab07136/donor_contact_data.json"
        }
      ]
    },
    {
      "amount_in_cents": 400,
      "state": "confirmed",
      "token": "86be4452d4afb0f2d56f0add",
      "client_reference": null,
      "created_at": "2010-10-29T09:46:25+02:00",
      "receiver_type": "Project",
      "receiver_id": 4798,
      "receiver_title": "Hilfe für Jugendliche mit krebskranken Eltern",
      "links": [
        {
          "rel": "receiver",
          "href": "https://api.betterplace.org/de/api_v4/projects/4798.json"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/86be4452d4afb0f2d56f0add.json"
        },
        {
          "rel": "donor_contact_data",
          "href": "https://api.betterplace.org/de/api_v4/clients/volksfreund/client_donations/86be4452d4afb0f2d56f0add/donor_contact_data.json"
        }
      ]
    }
  ]
}
```

