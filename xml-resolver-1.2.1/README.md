# xml-resolver-1.2.1-patched

This is a patched version of xml-commons-resolver-1.2 from xml-commons trunk code. 

The patch fixes URL handling from oasis catalogs on Windows machines. The files affected are:

org/apache/xml/resolver/helpers/FileURL.java
org/apache/xml/resolver/Catalog.java
org/apache/xml/resolver/apps/resolver.java
org/apache/xml/resolver/readers/TextCatalogReader.java
org/apache/xml/resolver/readers/SAXCatalogReader.java
org/apache/xml/resolver/tools/CatalogResolver.java

The fix uses java.io.File.toURI().toURL() to correctly generate file: URLs on Windows (and all
other operating systems though it obviously worked ok on Linux before this). 

If this jar is not present GN will fail when it tries to resolve any URL against the oasis catalog. The first
time this usually takes place is when a schema-ident.xml file from a schemaPlugin is validated against its XML 
schema definition during startup.

Simon Pigot
