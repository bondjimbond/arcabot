# YUDLbot

A silly little bot that tweets random [York University Digital Library](http://digital.library.yorku.ca) content. You can find me at [@YUDLbot](http://twitter.com/YUDLbot).

If you want use it, you will need to setup the variables outlined in `config.py.example` and rename it to `config.py`. For `SOLR_DATA` you will need to construct a query, and append `&fl=PID%2C+mods_titleInfo_title_ms&wt=json&indent=true` along with the number of rows you want. For example `&rows=100`.

Example SOLR_DATA query (from YUDL): solr_data = 'http://localhost:8080/solr/yudl/select?q=mods_relatedItem_titleInfo_title_s%3A"Toronto+Telegram+fonds%2C+F0433"+AND+dc.title%3Acats+AND+RELS_EXT_hasModel_uri_ms%3A"info%3Afedora%2Fislandora%3Asp_large_image_cmodel"&fl=PID%2C+mods_abstract_s&rows=20000&wt=json&indent=true'

The script must be hosted on your Islandora server, as it must access Solr directly.
