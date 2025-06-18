# ADAMS_xml_to_rdf
To convert an XML road profile to RDF format for use in ADAMS/Car
python
CopyEdit
import xml.etree.ElementTree as ET

tree = ET.parse('road_profile.xml')
root = tree.getroot()

with open('road_profile.rdf', 'w') as rdf:
    rdf.write("# Distance LF RF LR RR\n")
    for point in root.findall('point'):
        dist = point.find('distance').text
        lf = point.find('left_front').text
        rf = point.find('right_front').text
        lr = point.find('left_rear').text
        rr = point.find('right_rear').text
        rdf.write(f"{dist} {lf} {rf} {lr} {rr}\n")
