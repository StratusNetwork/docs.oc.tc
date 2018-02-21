---
layout: page

category: "Modules"
title:  "Includes & Conditionals"
nav_content:
  - path: "#includes"
    name: "XML File Includes"
  - path: "#conditionals"
    name: "Conditionals"

---

### XML File Includes {#includes}
A XML file can be split into multiple files and then included into the main one by using the include element. This allows you to keep the main file more organized by including sections such as kits or classes.

    <include src="classes.xml"/>

The PGM plugin will look through it's plugin-wide include path for includes, and it will also look for them relative to from where they are imported. You can set up a chain of includes that respects those same semantics.

Included XML files should have the XML header and the main map container.

Example

    <?xml version="1.0"?>
    <map proto="{{site.current_proto}}">

    <!-- Add kits, classes etc., here -->

    </map>

The master map repository contains the following pre-made XML files for you to use

<div class='table-responsive'>
  <table class='table table-striped table-condensed'>
    <thead>
      <tr>
        <th>File</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>
          <a href='https://github.com/OvercastNetwork/maps.oc.tc/blob/master/Include/tutorial.xml'>tutorial.xml</a>
        </td>
        <td>Contains the starting and ending stages of a tutorial</td>
      </tr>
      <tr>
        <td>
          <a href='https://github.com/OvercastNetwork/maps.oc.tc/blob/master/continuity-tnt.xml'>continuity-tnt.xml</a>
        </td>
        <td>Contains a pre-designed TNT inventory, used on maps such as BoomBox</td>
      </tr>
      <tr>
        <td>
          <a href='https://github.com/OvercastNetwork/maps.oc.tc/blob/master/blasternauts.xml'>blasternauts.xml</a>
        </td>
        <td>Contains the base XML for an arcade gamemode called 'blasternauts'</td>
      </tr>
      <tr>
        <td>
          <a href='https://github.com/OvercastNetwork/maps.oc.tc/blob/master/Include/blitz-global.xml'>blitz-global.xml</a>
        </td>
        <td>Contains the autorespawn mechanism for blitz maps</td>
      </tr>
      <tr>
        <td>
          <a href='https://github.com/OvercastNetwork/maps.oc.tc/blob/master/Blitz/GS/gs.xml'>gs.xml</a>
        </td>
        <td>Contains pre-made classes for the Ghost Squadron gamemode</td>
      </tr>
      <tr>
        <td>
          <a href='https://github.com/OvercastNetwork/maps.oc.tc/blob/master/Blitz/GS/gs-ffa.xml'>gs-ffa.xml</a>
        </td>
        <td>Contains pre-made teams for the Ghost Squadron FFA gamemode</td>
      </tr>
      <tr>
        <td>
          <a href='https://github.com/OvercastNetwork/maps.oc.tc/blob/master/stamina.xml'>stamina.xml</a>
        </td>
        <td>Contains the default settings for the stamina module</td>
      </tr>
      <tr>
        <td>
          <a href='https://github.com/OvercastNetwork/maps.oc.tc/blob/master/Include/skywars.xml'>skywars.xml</a>
        </td>
        <td>Contains the base XML for Skywars</td>
      </tr>
      <tr>
        <td>
          <a href='https://github.com/OvercastNetwork/maps.oc.tc/blob/master/Include/block-runner.xml'>block-runner.xml</a>
        </td>
        <td>Contains the base XML for an arcade gamemode called 'block runner'</td>
      </tr>
      <tr>
        <td>
          <a href='https://github.com/OvercastNetwork/maps.oc.tc/blob/master/Include/disable-boat-crafting.xml'>disable-boat-crafting.xml</a>
        </td>
        <td>Contains XML that disables boat crafting of any kind</td>
      </tr>
    </tbody>
  </table>
</div>
<br/>

### Conditionals {#conditionals}

XML files can contain simple `<if>` and `<unless>` [conditional][1] statements, these conditionals can be used to reduce duplicated map files and simplify managing multiple variations of a map.
For example, instead of having multiple map variants in different folders they can condensed into one neat location.
This also allows map variants to be automatically loaded on a specific servers or during holiday events.

Conditionals can be used anywhere in the XML and can contain anything.
When PGM parses the XML, it will skip over any conditional blocks which are false.

There are two limitations to conditionals right now:
attributes can only equate to true/false and conditions are defined in the PGM server configuration.


[1]: https://en.wikipedia.org/wiki/Conditional_%28computer_programming%29

<div class='table-responsive'>
  <table class='table table-striped table-condensed'>
    <thead>
      <tr>
        <th>Element</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>
          <span class='highlight'>
            <code>{{'<if a="true"> </if>' | escape_once}}</code>
          </span>
        </td>
        <td>
          If a is true, use the contents of this element.
        </td>
      </tr>
      <tr>
        <td>
          <span class='highlight'>
            <code>{{'<if a="true" b="true"> </if>' | escape_once}}</code>
          </span>
        </td>
        <td>
          If a AND b are both true, use the contents of this element.
        </td>
      </tr>
      <tr>
        <td>
          <span class='highlight'>
            <code>{{'<unless a="true"> </unless>' | escape_once}}</code>
          </span>
        </td>
        <td>
          If a is NOT true, use the contents of this element.
        </td>
      </tr>
      <tr>
        <td>
          <span class='highlight'>
            <code>{{'<unless a="false" b="false"> </unless>' | escape_once}}</code>
          </span>
        </td>
        <td>
          If (a OR b) is NOT false, use the contents of this element.
        </td>
      </tr>
    </tbody>
  </table>
</div>
<h5>Conditionals</h5>
<div class='table-responsive'>
  <table class='table table-striped table-condensed'>
    <thead>
      <tr>
        <th>Name</th>
        <th>Description</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>
          <code>ranked=""</code>
        </td>
        <td>
          The map is running on a ranked server.
        </td>
      </tr>
      <tr>
        <td>
          <code>halloween=""</code>
        </td>
        <td>
          Halloween -- Oct 1st 00:00 to Nov 1st 00:00
        </td>
      </tr>
      <tr>
        <td>
          <code>christmas=""</code>
        </td>
        <td>
          Christmas -- Dec 1st 00:00 to Dec 26th 00:00
        </td>
      </tr>
      <tr>
        <td>
          <code>april-fools=""</code>
        </td>
        <td>
          April Fools Day -- Apr 1st 00:00 to Apr 2nd 00:00
        </td>
      </tr>
    </tbody>
  </table>
</div>

Examples

    <!-- this section is only parsed when on a ranked server. -->
    <if ranked="true">
        <time>30m</time>
        <broadcasts>
            <tip after="1m">You guys are pros, keep up the good teamwork!</tip>
        </broadcasts>
    </if>

    <!-- Conditional kit inventory -->
    <kits>
        <kit id="red-inventory">
            <if ranked="false">
                <item slot="0" material="iron sword"/>
            </if>
            <if ranked="true">
                <item slot="0" material="diamond sword"/>
            </if>
        </kit>
    </kits>

<br/>

#### Conditional Terrain
If the individual map variants have a different physical world file they can still be neatly organized in the same folder.
The [terrain](/modules/world#terrain) tag can be used to specify a sub-folder that contains the map's terrain data.
This will require any regions, etc. that are different between the worlds to be defined in separate conditionals.

    <if ranked="true">
        <terrain world="ranked"/>
        <time result="objectives">30m</time>
    </if>
    <unless ranked="true">
        <terrain world="normal"/>
        <time result="objectives">45m</time>
        <respawn delay="5s" auto="true"/>
    </unless>

<br/>

#### Things Not to Do

There are some pitfalls you should avoid when using conditionals.
Defining elements outside and inside a conditional is discouraged, instead those elements should be defined inside their own conditionals.
For example, elements with ID's will throw an error if they are defined in both places at the same time.
However, some elements will not, and instead the first or last defined instance of that element will be used.

    <!-- Don't do this! PGM will throw an error because the id 'zombies' is used twice. -->
    <teams>
        <team id="zombies" color="red" max="30"/>
        <if ranked="true">
            <team id="zombies" color="dark red" max="10"/>
        </if>
    </teams>

    <!-- This is the correct way to do the above. -->
    <teams>
        <if ranked="false">
            <team id="zombies" color="red" max="30"/>
        </if>
        <if ranked="true">
            <team id="zombies" color="dark red" max="10"/>
        </if>
    </teams>
