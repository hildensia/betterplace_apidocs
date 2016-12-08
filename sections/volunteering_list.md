
# Volunteering List ⇄ [Details](volunteering_details.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/volunteering.json?around=10997+Berlin%2C+Germany&around_distance=25km&nelat=51.123&nelng=12.123&order=content_updated_at%3AASC&q=Homework+help&scope=location&swlat=51.001&swlng=12.001
```

A list of betterplace.org volunteering offers (donate time).
Results are contained in a *data* attribute.

**For [betterplace.org clients](../README.md#client-api):**
This resource is not available at the moment.


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">scope</th>
    <td><code>location</code></td>
    <td>no</td>
    <td>Use the scope to specify how the search query <code>q</code> should behave:
<ul>
<li>"no scope" (default) performs a full text search
<li><code>human_name</code> searches only on the manager-fullname and carrier-fullname.
  Use this to get all entities by "Unicef" or by "Till Behnke".
<li><code>location</code> does a reverse geocoding lookup.
  This lookup returns a bounding box. We transform this bounding box to a
  rectangle that is large enough to encapsulate the whole bounding box.
  We then return all entities that are within this rectangle.
</ul>
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
</td>
  </tr>
  <tr>
    <th align="left">around</th>
    <td><code>10997 Berlin, Germany</code></td>
    <td>no</td>
    <td>Order the results by the distance to the given location from near to far.
<br>
Location can be provided as …
<br>
<em>… Lat/Lng:</em> <code>52.50,13.45</code>
<br>
<em>… ZIP:</em> <code>10997 Berlin, Germany</code>.
We use the centre of the ZIP code area as center for the search.
Please add enough context information (like the Country name)
so google knows what place you are looking for.
<br>
<em>… any location search:</em> All queries other than a float tuple
are sent to the google location service. For the provided response we
take a fitting lat/lng value as center of the search. So in theory,
you can use any search that works for google maps.
<br>
Check the <code>around_location</code> to see what latitude/longitude
values have been used for the query.
</td>
  </tr>
  <tr>
    <th align="left">around_distance</th>
    <td><code>25km</code></td>
    <td>no</td>
    <td>In combination with the <code>around</code> parameter the search will be
limited to results whose location is closer than the given value to the
location provided through the <code>around</code> parameter. Possible
values are all integer values followed by <code>m</code> for meters or
<code>km</code> for kilometers, e.g. <code>1000m</code>, <code>1km</code>.
<br>
When <code>around_distance</code> is given without <code>around</code> it
will be ignored.
</td>
  </tr>
  <tr>
    <th align="left">nelat</th>
    <td><code>51.123</code></td>
    <td>no</td>
    <td>For geographic bound filterning: The northeast corner's latitude.</td>
  </tr>
  <tr>
    <th align="left">nelng</th>
    <td><code>12.123</code></td>
    <td>no</td>
    <td>For geographic bound filterning: The northeast corner's longitude.</td>
  </tr>
  <tr>
    <th align="left">swlat</th>
    <td><code>51.001</code></td>
    <td>no</td>
    <td>For geographic bound filterning: The southwest corner's latitude.</td>
  </tr>
  <tr>
    <th align="left">swlng</th>
    <td><code>12.001</code></td>
    <td>no</td>
    <td>For geographic bound filterning: The southwest corner's longitude.</td>
  </tr>
  <tr>
    <th align="left">q</th>
    <td><code>Homework help</code></td>
    <td>no</td>
    <td>Search query. The searches behaviour is based on the scope.</td>
  </tr>
  <tr>
    <th align="left">order</th>
    <td><code>content_updated_at:ASC</code></td>
    <td>no</td>
    <td>Order the result by <code>has_image</code> (default),
<code>content_updated_at</code> (second default). Use the optional
<code>ASC</code> (default) or <code>DESC</code>.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
<br>
The default order is the same as for the
<a href="http://www.betterplace.org/en/volunteering/list">betterplace.org volunteering list</a>:
<code>has_image:desc| carrier_has_image:desc| content_updated_at:desc</code>
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
      <th align="left">latitude</th>
      <td>number</td>
      <td>52.499007</td>
      <td>Decimal degrees based on user input</td>
    </tr>
    <tr>
      <th align="left">longitude</th>
      <td>number</td>
      <td>13.44947</td>
      <td>Decimal degrees based on user input</td>
    </tr>
    <tr>
      <th align="left">street</th>
      <td>null &#124; string</td>
      <td>"Schlesische Straße 26"</td>
      <td>Street address</td>
    </tr>
    <tr>
      <th align="left">zip</th>
      <td>null &#124; string</td>
      <td>"10997"</td>
      <td>ZIP code</td>
    </tr>
    <tr>
      <th align="left">city</th>
      <td>null &#124; string</td>
      <td>"Berlin"</td>
      <td>Name of the city</td>
    </tr>
    <tr>
      <th align="left">country</th>
      <td>null &#124; string</td>
      <td>"Deutschland"</td>
      <td>Name of the country</td>
    </tr>
    <tr>
      <th align="left">content_updated_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td>string</td>
      <td>TODO</td>
      <td>Max 100 character unless the volunteering is imported</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td>string</td>
      <td></td>
      <td>A description of the offer. This may contain any of the following
HTML tags: <code>a, br, strong, b, em, i, ul, ol, li, p, div, img, iframe</code>.
</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="carrier-ref" href="#carrier">
            ↓carrier
          </a>
        </th>
      <td>object</td>
      <td>TODO</td>
      <td>The organisation that carrier this volunteering</td>
    </tr>
    <tr>
      <th align="left">vacancies</th>
      <td>number</td>
      <td>1</td>
      <td>The number of volunteers that are needed, provided by the manager</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="image-ref" href="#image">
            ↓image
          </a>
        </th>
      <td>null &#124; object</td>
      <td>TODO</td>
      <td>Each volunteering has one optional image / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact-ref" href="#contact">
            ↓contact
          </a>
        </th>
      <td>object</td>
      <td>TODO</td>
      <td>Contact person, contact data and contact address</td>
    </tr>
    <tr>
      <th align="left">location_fixed</th>
      <td>boolean</td>
      <td>true</td>
      <td>Specifies whether the volunteering offer is limited to a certain location or if it may be
executed remotely.
</td>
    </tr>
    <tr>
      <th align="left">working_time_selection</th>
      <td>string</td>
      <td>regular commitment</td>
      <td>Working time selection, specifies if this is a one-time event or if
this volunteering can takes place regulary.
</td>
    </tr>
    <tr>
      <th align="left">working_time_weekends</th>
      <td>array</td>
      <td>["in the mornings"]</td>
      <td>Up to three working time preferences. They specify when this volunteering
should take place on weekends.
</td>
    </tr>
    <tr>
      <th align="left">working_time_weekdays</th>
      <td>array</td>
      <td>["in the mornings"]</td>
      <td>Up to three working time preferences. They specify when this volunteering
should take place on weekdays.
</td>
    </tr>
    <tr>
      <th align="left">begins_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">ends_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">topics</th>
      <td>array</td>
      <td>["Development cooperation", "Children & youth"]</td>
      <td>Up to 4 categories that describe, what for which causes you need volunteers.
Results are translated to the requested language.
Possible results: "Animal & environment protection", "Culture & sports",
"Children & youth", "Development cooperation ", "DisabledEducation", "Elderly people",
"Human rights", "Refugees & immigrants", "Invalid", "Local help", "Socially deprived"
</td>
    </tr>
    <tr>
      <th align="left">activities</th>
      <td>array &#124; null</td>
      <td>["consulting/coaching", "office work"]</td>
      <td>Up to 4 categories that describe, what for which causes you need volunteers.
Results are translated to the requested language.
Possible results: "consulting/coaching", "crafting/gardening", "doing sports",
"doing the chores", "group care", "nursing/parenting", "office work",
"organising/managing", "painting/designing", "tutoring/reading",
"visiting/accompanying", "writing/translating"
</td>
    </tr>
    <tr>
      <th align="left">imported_from</th>
      <td>null &#124; string</td>
      <td>aktion_mensch</td>
      <td>Betterplace imports volunteering offers from Aktions Mensch.</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="import_information-ref" href="#import_information">
            ↓import_information
          </a>
        </th>
      <td>null &#124; object</td>
      <td>TODO</td>
      <td>Meta data concerning the import of this volunteering offer, if it
was indeed imported.
</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="profile_picture-ref" href="#profile_picture">
            ↓profile_picture
          </a>
        </th>
      <td>null &#124; object</td>
      <td></td>
      <td>TODO</td>
    </tr>
  </table>
### <a id="carrier" href="#carrier-ref">↑Nested Attributes: carrier</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">carrier.latitude</th>
      <td>number</td>
      <td>52.499007</td>
      <td>Decimal degrees based on user input</td>
    </tr>
    <tr>
      <th align="left">carrier.longitude</th>
      <td>number</td>
      <td>13.44947</td>
      <td>Decimal degrees based on user input</td>
    </tr>
    <tr>
      <th align="left">carrier.name</th>
      <td>string</td>
      <td>"Viva con Agua de Sankt Pauli e.V."</td>
      <td>An organisation name, Users will be added later</td>
    </tr>
    <tr>
      <th align="left">carrier.street</th>
      <td>string</td>
      <td>"Rosenstr. 3"</td>
      <td>Contact data for the organisation</td>
    </tr>
    <tr>
      <th align="left">carrier.city</th>
      <td>string</td>
      <td>"Berlin"</td>
      <td>Contact data for the organisation</td>
    </tr>
    <tr>
      <th align="left">carrier.zip</th>
      <td>string</td>
      <td>"10123"</td>
      <td>Contact data for the organisation</td>
    </tr>
    <tr>
      <th align="left">carrier.country</th>
      <td>string</td>
      <td>"Germany"</td>
      <td>Contact data for the organisation</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="carrier.picture-ref" href="#carrier.picture">
            ↓carrier.picture
          </a>
        </th>
      <td>null &#124; object</td>
      <td></td>
      <td>TODO</td>
    </tr>
  </table>
### <a id="carrier.picture" href="#carrier.picture-ref">↑Nested Attributes: carrier.picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">carrier.picture.fallback</th>
      <td>boolean</td>
      <td>true</td>
      <td>Specifies whether a fallback image is given or not</td>
    </tr>
  </table>
### <a id="image" href="#image-ref">↑Nested Attributes: image</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">image.description</th>
      <td>string</td>
      <td></td>
      <td>Image description</td>
    </tr>
  </table>
### <a id="contact" href="#contact-ref">↑Nested Attributes: contact</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">contact.name</th>
      <td>string</td>
      <td>Till Behnke</td>
      <td>Fullname of the contact person.
For imported volunteering offers, this is the
contact-name that is provided on import.
</td>
    </tr>
    <tr>
      <th align="left">contact.phone</th>
      <td>string</td>
      <td>030 - 7676 4488 44</td>
      <td>Phone number for direct contact.
No validations on input apply.
</td>
    </tr>
    <tr>
      <th align="left">contact.email</th>
      <td>string</td>
      <td>support@betterplace.org</td>
      <td>Plain text email-address for direct contact
</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact.picture-ref" href="#contact.picture">
            ↓contact.picture
          </a>
        </th>
      <td>object</td>
      <td>//assets.betterplace.org/…</td>
      <td>User profile picture or a fallback image</td>
    </tr>
  </table>
### <a id="contact.picture" href="#contact.picture-ref">↑Nested Attributes: contact.picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">contact.picture.fallback</th>
      <td>boolean</td>
      <td>true</td>
      <td>Specifies whether a fallback image is given or not</td>
    </tr>
  </table>
### <a id="import_information" href="#import_information-ref">↑Nested Attributes: import_information</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">import_information.created_at</th>
      <td>null &#124; string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the imported record was actually created.
</td>
    </tr>
    <tr>
      <th align="left">import_information.updated_at</th>
      <td>null &#124; string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the imported record was
actually updated last.
</td>
    </tr>
    <tr>
      <th align="left">import_information.import_type</th>
      <td>string</td>
      <td>"Import::ImportFormat"</td>
      <td>Type of import this record originated from.</td>
    </tr>
    <tr>
      <th align="left">import_information.import_id</th>
      <td>string</td>
      <td>"foo:23"</td>
      <td>Unique identifier for this imported record.
</td>
    </tr>
    <tr>
      <th align="left">import_information.imported_at</th>
      <td>string</td>
      <td>"1994-11-15T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the record was imported at
betterplace.
</td>
    </tr>
  </table>
### <a id="profile_picture" href="#profile_picture-ref">↑Nested Attributes: profile_picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">profile_picture.fallback</th>
      <td>boolean</td>
      <td>true</td>
      <td>Specifies whether a fallback image is given or not</td>
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
(<a href="volunteering_details.md">volunteering details</a>)
</td>
    </tr>
    <tr>
      <th align="left">platform</th>
      <td>Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">inquiries</th>
      <td>The URL to which inquiries about this offer can be POSTed
(<a href="volunteering_inquiries.md">inquiry details</a>).
Templated, needs insertion of the client_id.
</td>
    </tr>
    <tr>
      <th align="left">carrier.self</th>
      <td>Link to this resource itself
(<a href="organisation_details.md">organisation details</a>)
</td>
    </tr>
    <tr>
      <th align="left">carrier.picture.fill_100x100</th>
      <td>100×100 Pixel</td>
    </tr>
    <tr>
      <th align="left">carrier.picture.fill_200x200</th>
      <td>200×200 Pixel</td>
    </tr>
    <tr>
      <th align="left">carrier.picture.fill_400x400</th>
      <td>400×400 Pixel</td>
    </tr>
    <tr>
      <th align="left">carrier.picture.original</th>
      <td>Maximum sized image. This is the original image with default-cropping or user-cropping applied.</td>
    </tr>
    <tr>
      <th align="left">image.fill_618x322</th>
      <td>618×322 Pixel / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">image.fill_270x141</th>
      <td>270×141 Pixel / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">image.original</th>
      <td>Original size / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">image.thumb</th>
      <td>Thumbnail size / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">image.medium</th>
      <td>Medium size / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">image.regular</th>
      <td>Regular size / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">contact.picture.fill_100x100</th>
      <td>100×100 Pixel</td>
    </tr>
    <tr>
      <th align="left">contact.picture.original</th>
      <td>Maximum sized image. This is the original image with default-cropping or user-cropping applied.</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_960x500</th>
      <td>950×500 Pixel</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_730x380</th>
      <td>730×380 Pixel</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_618x322</th>
      <td>618×322 Pixel / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_410x214</th>
      <td>410×214 Pixel</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_270x141</th>
      <td>270×141 Pixel / DEPRECATED, will be removed after 5/2015</td>
    </tr>
    <tr>
      <th align="left">profile_picture.original</th>
      <td>Maximum sized image. This is the original image with default-cropping or user-cropping applied.</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 4196,
  "offset": 3,
  "total_pages": 1399,
  "current_page": 2,
  "per_page": 3,
  "data": [
    {
      "id": 7074,
      "created_at": "2013-03-03T19:43:47+01:00",
      "updated_at": "2016-11-11T14:12:30+01:00",
      "latitude": 10.6346,
      "longitude": -85.4407,
      "street": " Rincon de La Vieja",
      "zip": "1000",
      "city": "Liberia",
      "country": "Costa Rica",
      "content_updated_at": "2016-01-17T08:38:25+01:00",
      "title": "Projekt des nachhaltigen Tourismus in Costa Rica",
      "description": "Projekt des nachhaltigen Tourismus in der Buena Vista Lodge<br>An den Hängen des Rincon de la Vieja Vulkan und in der Mitte von fünf Nationalparks (Rincón de la Vieja, Santa Rosa, Guanacaste, Santa Elena und El Acha) finden Sie unsere Lodge, die versucht eine autarke organische touristische Unterkunft zu werden , die nachhaltigen Tourismus betreibt und sich zum Ziel gemacht hat die natürlichen Ressourcen so gut wie möglich zu schützen.<br>Ziel unseres Volontär Programm<br>Ziel unseres Freiwilligen Programms ist Bildungsarbeit im Umweltschutz. Der Schwerpunkt dieser Bildungsarbeit konzentriert sich auf die Erlernung einer verantwortungsvollen und nachhaltigen Nutzung der natürlichen Ressourcen durch praktische Tätigkeiten mit dem Ziel dieses Wissen als Multiplikator an andere Menschen weiterzugeben. Unsere Philosophie ist es, die meisten der grundlegenden Produkte, die wir verbrauchen, in einer kostengünstigen und umweltfreundlichen Weise zu erzeugen, unter Berücksichtigung der sozialen, ökologischen, wirtschaftlichen und politischen Vorgaben.<br><br>Ein Agrarwirt der bekannten agrarwirtschaftlichen Universität EARTH, der sich auf die Verwaltung und Nutzung natürlicher Ressourcen spezialisiert hat, wird die Volontäre durch ihr Volontariat begleiten.<br>Nachhaltige Projekte, bei denen Freiwillige Wissen vermittelt wird:<br>Woche eins und zwei: Abfall ist kein Problem sondern bei richtiger Handhabung die Möglichkeit eine neue nutzbare Ressource herzustellen.<br>• Die Biogasanlage als Ressourcenhersteller<br>Auf der Lodge haben wir eine Kläranlage, die wir als produktives System nutzen. Durch die Zuführung aller organischen Abfälle wie Seife, Lebensmittel und Fette (tierische und pflanzliche Fette) wird die Verschmutzung durch physikalische Verfahren verringert (Filter, Sedimentation und Fest-Trennung) und durch biologische Verfahren (Mikroorganismus Aktivitäten) produzieren wir Methan, das für das Kochen, die Wassererwärmung und demnächst zur Stromherstellung genutzt wird. Weiterhin wird natürliches Düngemittel hergestellt und zur gleichen Zeit, reduzieren wir 98% der Wasserverschmutzung.<br>Durch dieses vorbildliche System können in ländlichen Gemeinden wo manchmal Strom nicht zur Verfügung steht, und man teures Propangas oder teure chemische Düngung für die Acker kaufen muss eine kostengünstige, effiziente und nachhaltige Lösung zur Verfügung gestellt.<br>Woche drei: Arbeiten auf der Bio-Farm<br>• Arbeiten in der hoteleigenen Biofarm",
      "carrier": {
        "latitude": 51.75091934204102,
        "longitude": 14.64650440216064,
        "name": "(F.A.W.N.) Deutschland e.V.",
        "street": "Gubenerstr.36",
        "city": "Forst/Lausitz",
        "zip": "03149",
        "country": "Deutschland",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/002/089/fill_100x100_original_FAWNLogo2010neu.jpg"
            },
            {
              "rel": "fill_200x200",
              "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/002/089/fill_200x200_original_FAWNLogo2010neu.jpg"
            },
            {
              "rel": "fill_400x400",
              "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/002/089/fill_400x400_original_FAWNLogo2010neu.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/002/089/crop_original_original_FAWNLogo2010neu.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/de/api_v4/organisations/2089.json"
          }
        ]
      },
      "vacancies": 6,
      "image": {
        "description": "Blick vom Projekt auf Guanacaste bis zum Pazifik",
        "links": [
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/074/fill_618x322_P1220394.JPG"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/074/fill_270x141_P1220394.JPG"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/074/P1220394.JPG"
          },
          {
            "rel": "thumb",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/074/thumb_P1220394.JPG"
          },
          {
            "rel": "medium",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/074/medium_P1220394.JPG"
          },
          {
            "rel": "regular",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/074/regular_P1220394.JPG"
          }
        ]
      },
      "contact": {
        "name": "Ralph Scheel",
        "phone": "+49 (0) 1577-2623892",
        "email": "info@fawn.de",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/019/008/fill_100x100_original_Carara-Nationalpark.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/019/008/crop_original_original_Carara-Nationalpark.jpg"
            }
          ]
        },
        "links": [

        ]
      },
      "location_fixed": true,
      "working_time_selection": "egal wann / nach Vereinbarung",
      "working_time_weekends": [

      ],
      "working_time_weekdays": [

      ],
      "begins_at": null,
      "ends_at": null,
      "topics": [
        "Bildung",
        "Entwicklungszusammenarbeit",
        "Kultur, Freizeit & Sport",
        "Tierschutz & Umwelt"
      ],
      "activities": [
        "Gruppen betreuen",
        "Büroarbeit",
        "werken/gärtnern",
        "organisieren/planen"
      ],
      "imported_from": null,
      "import_information": null,
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/074/fill_960x500_P1220394.JPG"
          },
          {
            "rel": "fill_730x380",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/074/fill_730x380_P1220394.JPG"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/074/fill_618x322_P1220394.JPG"
          },
          {
            "rel": "fill_410x214",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/074/fill_410x214_P1220394.JPG"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/074/fill_270x141_P1220394.JPG"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/074/crop_original_P1220394.JPG"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/volunteering/7074.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/volunteering/7074-projekt-des-nachhaltigen-tourismus-in-costa-rica"
        },
        {
          "rel": "inquiries",
          "href": "https://api.betterplace.org/de/api_v4/clients/%7Bclient_id%7D/volunteering/7074-projekt-des-nachhaltigen-tourismus-in-costa-rica/inquiries.json",
          "templated": true
        }
      ]
    },
    {
      "id": 7259,
      "created_at": "2013-03-08T11:45:28+01:00",
      "updated_at": "2016-07-07T12:37:24+02:00",
      "latitude": 44.62649917602539,
      "longitude": -85.78849792480469,
      "street": null,
      "zip": null,
      "city": null,
      "country": null,
      "content_updated_at": "2016-02-03T07:23:47+01:00",
      "title": "Improve our website and online info: Social media expert",
      "description": "The volunteer will: <br>Help to translate our project blog in Germany<br>Volunteer will help in office work. <br>The volunteer will mobilise his or her network to help spread the word about our crowdfunding campaigns.<br>The volunteer will write online reports and blogs about the implemented work in the organisation. <br>Volunteer will engage in unskillled work like construction of domesticated animal houses. <br>Help in updating our betterplace project page.<br>The volunteer will post pictures of our activities and write comments about them in German.",
      "carrier": {
        "latitude": 44.62649917602539,
        "longitude": -85.78849792480469,
        "name": "Ndibwami Integrated Rescue Project",
        "street": "Grant",
        "city": "Kamapala",
        "zip": "256",
        "country": "Uganda",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/004/177/fill_100x100_original_NIRP_LOGO.jpg"
            },
            {
              "rel": "fill_200x200",
              "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/004/177/fill_200x200_original_NIRP_LOGO.jpg"
            },
            {
              "rel": "fill_400x400",
              "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/004/177/fill_400x400_original_NIRP_LOGO.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/004/177/crop_original_original_NIRP_LOGO.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/de/api_v4/organisations/4177.json"
          }
        ]
      },
      "vacancies": 3,
      "image": {
        "description": "Volunteers share business skills with women groups",
        "links": [
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/259/fill_618x322_home-office.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/259/fill_270x141_home-office.jpg"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/259/home-office.jpg"
          },
          {
            "rel": "thumb",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/259/thumb_home-office.jpg"
          },
          {
            "rel": "medium",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/259/medium_home-office.jpg"
          },
          {
            "rel": "regular",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/259/regular_home-office.jpg"
          }
        ]
      },
      "contact": {
        "name": "Hellen Nalugo Sabastian",
        "phone": "+256773779423",
        "email": "nirpproject@yahoo.com",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/106/107/fill_100x100_original_nalugo.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/106/107/crop_original_original_nalugo.jpg"
            }
          ]
        },
        "links": [

        ]
      },
      "location_fixed": false,
      "working_time_selection": "egal wann / nach Vereinbarung",
      "working_time_weekends": [

      ],
      "working_time_weekdays": [

      ],
      "begins_at": null,
      "ends_at": null,
      "topics": [
        "Bildung",
        "Kinder & Jugendliche",
        "Kranke",
        "Sozial Benachteiligte"
      ],
      "activities": [
        "Büroarbeit",
        "programmieren",
        "PR / Social Media"
      ],
      "imported_from": null,
      "import_information": null,
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/259/fill_960x500_home-office.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/259/fill_730x380_home-office.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/259/fill_618x322_home-office.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/259/fill_410x214_home-office.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/259/fill_270x141_home-office.jpg"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/259/crop_original_home-office.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/volunteering/7259.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/volunteering/7259-improve-our-website-and-online-info-social-media-expert"
        },
        {
          "rel": "inquiries",
          "href": "https://api.betterplace.org/de/api_v4/clients/%7Bclient_id%7D/volunteering/7259-improve-our-website-and-online-info-social-media-expert/inquiries.json",
          "templated": true
        }
      ]
    },
    {
      "id": 7268,
      "created_at": "2013-03-11T18:00:54+01:00",
      "updated_at": "2016-11-03T11:25:45+01:00",
      "latitude": 52.52,
      "longitude": 13.405,
      "street": "",
      "zip": "",
      "city": "Berlin",
      "country": "Deutschland",
      "content_updated_at": "2016-01-07T17:20:56+01:00",
      "title": "\"Pate oder Patin werden und mit einem Neuköllner Kind die Welt neu entdecken\"",
      "description": "Bevor wir uns hier in Details verlieren, lassen wir erst einmal unsere Patin Linda zu Wort kommen, denn wer könnte besser Beschreiben, was ein Engagement in unserem Projekt ausmacht, als die Engagierten selbst?<br>http://neukoellner-talente.de/paten/paten-stellen-sich-vor/<br><br>Wer neugierig ist und noch mehr wissen will, kann gerne weiter lesen oder sich gleich bei uns im Büro melden: 030 - 62 73 80 14<br><br>---<br><br>http://neukoellner-talente.de/<br><br>Kinder brauchen Zeit, viel Aufmerksamkeit und eine individuelle Förderung, um ihre Stärken und Begabungen zu entdecken und zu entfalten. Mit ihrem Patenschaftsprojekt »Neuköllner Talente« wendet sich die Bürgerstiftung Neukölln an Kinder im Grundschulalter, die entdecken und zeigen wollen, was in ihnen steckt. Vorrangiges Ziel ist es, durch eine intensive 1:1 Betreuung im Rahmen einer Patenschaft, benachteiligten Kindern in dem multiethnischen Berliner Bezirk die Chance zum Entdecken ihrer Interessen und Begabungen, und die Möglichkeit zur Teilhabe zu eröffnen.",
      "carrier": {
        "latitude": 52.46874,
        "longitude": 13.4341,
        "name": "Bürgerstiftung Neukölln",
        "street": "Emser Str. 117",
        "city": "Berlin",
        "zip": "12051",
        "country": "Deutschland",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/012/964/fill_100x100_profile_thumb_B_rgerstiftung.png"
            },
            {
              "rel": "fill_200x200",
              "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/012/964/fill_200x200_profile_thumb_B_rgerstiftung.png"
            },
            {
              "rel": "fill_400x400",
              "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/012/964/fill_400x400_profile_thumb_B_rgerstiftung.png"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/012/964/crop_original_profile_thumb_B_rgerstiftung.png"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/de/api_v4/organisations/12964.json"
          }
        ]
      },
      "vacancies": 20,
      "image": {
        "description": "",
        "links": [
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/fill_618x322_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/fill_270x141_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "thumb",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/thumb_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "medium",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/medium_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "regular",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/regular_TalentePatInnenaufruf_2.jpg"
          }
        ]
      },
      "contact": {
        "name": "Deniz Eroglu",
        "phone": "030 627 380 14",
        "email": "info@neukoellner-talente.de",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/293/450/fill_100x100_original_00b1f1a4aa.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/293/450/crop_original_original_00b1f1a4aa.jpg"
            }
          ]
        },
        "links": [

        ]
      },
      "location_fixed": true,
      "working_time_selection": "egal wann / nach Vereinbarung",
      "working_time_weekends": [

      ],
      "working_time_weekdays": [

      ],
      "begins_at": null,
      "ends_at": null,
      "topics": [
        "Bildung",
        "Kinder & Jugendliche",
        "Kultur, Freizeit & Sport",
        "Flüchtlinge & Migranten"
      ],
      "activities": [
        "besuchen/begleiten"
      ],
      "imported_from": null,
      "import_information": null,
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/fill_960x500_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/fill_730x380_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/fill_618x322_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/fill_410x214_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/fill_270x141_TalentePatInnenaufruf_2.jpg"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/bettertime/job_description/profile_picture/000/007/268/crop_original_TalentePatInnenaufruf_2.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/volunteering/7268.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/volunteering/7268-pate-oder-patin-werden-und-mit-einem-neukollner-kind-die-welt-neu-entdecken"
        },
        {
          "rel": "inquiries",
          "href": "https://api.betterplace.org/de/api_v4/clients/%7Bclient_id%7D/volunteering/7268-pate-oder-patin-werden-und-mit-einem-neukollner-kind-die-welt-neu-entdecken/inquiries.json",
          "templated": true
        }
      ]
    }
  ]
}
```

