# FIESTA-Priv Ontology:A GDPR-inspired IoT Ontology enabling Semantic Interoperability, Federation of Deployments and Privacy-Preserving Applications.

Citation
========
R. Agarwal, T. Elsaleh and E. Tragos, "GDPR-inspired IoT Ontology enabling Semantic Interoperability, Federation of Deployments and Privacy-Preserving Applications," 2022 IEEE 8th World Forum on Internet of Things (WF-IoT), Yokohama, Japan, 2022, pp. 1-8, doi: 10.1109/WF-IoT54382.2022.10152206. 

Abstract
========

Testing and experimentation are crucial for promoting innovation and building systems that can evolve to meet high levels of service quality. IoT data that belong to users and from which their personal information can be inferred are frequently shared in the background of IoT systems with third parties for experimentation and building quality services. This data sharing raises privacy concerns especially since in most cases the data are gathered and shared without the user's knowledge or explicit consent or for different purposes than the one for which the data were initially gathered. With the introduction of GDPR, IoT systems and experimentation platforms that federate data from different deployments, testbeds and data providers must be privacy-preserving. The wide adoption of IoT applications in scenarios ranging from smart cities to Industry 4.0 has raised concerns with respect to the privacy of users' data collected using IoT devices. Many experimental smart city applications are also using crowdsourcing data. Inspired by the GDPR requirements, we propose an IoT ontology built using available standards that enhances privacy, enables semantic interoperability between IoT deployments and supports the development of privacy-preserving experimental IoT applications.  On top, we propose recommendations on how to efficiently use the ontology within IoT testbed and federating platforms. Our ontology is validated for different quality assessment criteria using standard validation tools. We focus on "experimentation" without any loss of generality, because it covers scenarios from both research and industry, that are directly linked with innovation and in most cases neglect privacy.


Modifications performed
========
![Ontology](https://github.com/ragarwa2/fiesta-priv/blob/master/ontology.png)

Privacy graph
=======
![privacy](https://github.com/ragarwa2/fiesta-priv/blob/master/privacygraph.png)

Ontology Connections 
======
![Ontology Connections](https://github.com/ragarwa2/fiesta-priv/blob/master/connections.png)


Sample SPARQL Query
===================
```sparql
	# relevant PREFIX
	select ?sensor
	where {
	 # Below is the Augmented part
	 <USER_URI> a con:AllowedParty .
	 <USER_URI> priv:hasPermission  ?permission .
	 ?permission con:permission_given_for_activity ?action .
	 ?action a iot-taxonomy:Discovery .
	 ?action con:activity_has_purpose ?purpose .
	 ?purpose a iot-taxonomy:KnowSensorsInTheArea . 
	 ?permission Con:permission_given_for_data ?sensor .
	 # Below is the original user defined 'where' clause
	 ?sensor sosa:isHostedBy ?platform .
	 ?platform geo:location ?point.
	 ?point geo:lat ?lat . 
	 ?point geo:long ?lng . 
	 FILTER (?lng > -50 && ?lng < 50 && ?lat < 100 && ?lat > 0 ) 
	}
```

Authors
=======
- [Rachit Agarwal](https://rachit.gitlab.io), Inria Paris
- [Tarek Elsaleh](https://github.com/telsaleh), University of Surrey, UK
- Elias Tragos, Insight Center for Data Analytics, UCD

Tools used
==========
- Ontology Documentation: 
	- [Widoco](https://github.com/dgarijo/Widoco)
- Ontology Validation: 
	- [OOPS](http://smart-ics.ee.surrey.ac.uk/fiesta/ontology/fiesta-priv/OOPSevaluation/oopsEval.html#)
	- [Vapour](http://linkeddata.uriburner.com:8000/vapour?uri=http%3A%2F%2Fpurl.org%2Fiot%2Fontology%2Ffiesta-priv%23&acceptRdfXml=1&defaultResponse=dontmind&userAgent=#)


General Information
===================
The ontology file is fiesta-priv.owl and the taxonomy file is iot-taxonomy-lite.owl. Nonetheless, other format files are also made available. The available code, source of the ontology documentation, deploys it along with necessary files


Do you have a problem? Open an issue at [https://github.com/ragarwa2/fiesta-priv](https://github.com/ragarwa2/fiesta-priv)

