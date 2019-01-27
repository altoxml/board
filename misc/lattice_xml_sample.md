An existing example of lattice representation in XML is the 
[ALPS project (Algorithms and Libraries for Physics Simulations)](http://alps.comp-phys.org/mediawiki/index.php/Main_Page). The
link for the schema is broken but it can be viewed 
[via the Wayback Machine](https://web.archive.org/web/20110118082924/http://xml.comp-phys.org:80/lattice.xsd). 

![ruby](https://raw.githubusercontent.com/altoxml/board/gh-pages/misc/graph1.png)

```xml
<LATTICES>
  <GRAPH vertices="5" edges="5">
    <VERTEX id="1" type="0"/>
    <VERTEX id="2" type="1"/>
    <VERTEX id="3" type="0"/>
    <VERTEX id="4" type="2"/>
    <VERTEX id="5" type="2"/>
    <EDGE source="1" target="2" type="0"/>
    <EDGE source="2" target="3" type="0"/>
    <EDGE source="1" target="4" type="1"/>
    <EDGE source="2" target="5" type="1"/>
    <EDGE source="4" target="5" type="0"/>
  </GRAPH>
</LATTICES>
```
The [ALPS mailing lists](https://lists.phys.ethz.ch/pipermail/comp-phys-alps-users/) still seem to be active.