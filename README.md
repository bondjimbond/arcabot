# ArcaBot

A silly little bot that tweets random [Arca](http://arcabc.ca) content. You can find it at [@arca_bc](http://twitter.com/arca_bc).
This is a clone of [YUDLbot](https://github.com/yorkulibraries/YUDLbot) by Nick Ruest.

If you want use it, you will need to setup the variables outlined in `config.py.example` and rename it to `config.py`. For `SOLR_DATA` you will need to construct a query, and append `&fl=PID%2C+mods_titleInfo_title_ms&wt=json&indent=true` along with the number of rows you want. For example `&rows=100`.

If you run a Solr search with Debug Mode turned on (Solr settings, "Other" tab), you can see the Solr query being used. This can provide some guidance for formulating your query in SOLR_DATA.

Example internal SOLR_DATA query, grabbing all items from five CModels:
SOLR_DATA = 'http://localhost:8080/solr/select?q=RELS_EXT_hasModel_uri_ms%3A%28%22info%3Afedora%2Fir%3AthesisCModel%22%29+OR+RELS_EXT_hasModel_uri_ms%3A%28%22info%3Afedora%2Fir%3AcitationCModel%22%29+OR+RELS_EXT_hasModel_uri_ms%3A%28%22info%3Afedora%2Fislandora%3Asp_basic_image%22%29+OR+RELS_EXT_hasModel_uri_ms%3A%28%22info%3Afedora%2Fislandora%3Asp_large_image_cmodel%22%29+OR+RELS_EXT_hasModel_uri_ms%3A%28%22info%3Afedora%2Fislandora%3Asp_videoCModel%22%29&fl=PID%2C+mods_titleInfo_title_ms&wt=json&indent=true&rows=20000'

Sample externals query from York:
SOLR_DATA = 'https://digital.library.yorku.ca/solr/yudl/select?q=mods_relatedItem_titleInfo_title_s%3A%22Toronto+Telegram+fonds%2C+F0433%22+AND+dc.title%3Acats+AND+RELS_EXT_hasModel_uri_ms%3A"info%3Afedora%2Fislandora%3Asp_large_image_cmodel"&fl=PID%2C+mods_abstract_s&rows=20000&wt=json&indent=true'

Ideally, the script can be hosted on your Islandora server, using the http://localhost:8080 domain, as it must access Solr directly. 
But as long as you can reach Solr externally and get JSON back, you can host the file externally.

Note that you'll need to tweak the primary script to use the appropriate title field depending on what is available.

Todo: 
- Set a character limit on the Abstract and fields (this may just be part of the Solr query)
