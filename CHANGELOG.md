## CHANGELOG

### head - 0.0.1-RC21-SNAPSHOT

### 0.0.1-RC20 (2019-April-26)
**IMPORTANT:** This release was brought forward due to a CVE in PDFBOX. While not directly affecting this project (it affects parsing of untrusted PDFs), it is better not to have a vulnerable library on your classpath.
+ [#349](https://github.com/danfickle/openhtmltopdf/issues/349) Upgrade PDF-BOX to 2.0.15 to avoid CVE in 2.0.14. Thanks @BryceMehring.
+ [#347](https://github.com/danfickle/openhtmltopdf/issues/347) Add document language and title preference for PDF/A documents to satisfy Acrobat Pro validator. Thanks @mattstjean.
+ [#339](https://github.com/danfickle/openhtmltopdf/issues/339) Mark Jsoup DOM converter module as deprecated (for removal). Please see integration guide for replacement. This module may also pull in an insecure version of Guava so please migrate now.

### 0.0.1-RC19 (2019-March-18)
+ [#336](https://github.com/danfickle/openhtmltopdf/issues/336) Fix for broken image links causing an NPE. Thanks @svenfrauen.
+ [#334](https://github.com/danfickle/openhtmltopdf/pull/334) Allow the user to supply `PDPage` objects via page supplier. Thanks @DSW-PS.

### 0.0.1-RC18 (2019-March-10)
+ Please start using the fast renderer (`builder.useFastMode()`) as the old renderer will be removed in a future version.
+ [#180](https://github.com/danfickle/openhtmltopdf/issues/180) Fast renderer is finally ready for production. The fast renderer comes with:
  + Nearly 150 automated end-to-end regression tests. This is about 150 more than the old renderer.
  + Improved performance. This renderer scales linearly with the number of pages, compared to the old renderer which scaled with the page count squared.
  + Far better support for transforms, including nested transforms, multiple transforms and transforms interacting with hidden overflow, etc.
  + Better support for hidden overflow, with boxes now not escaping except with accordance to the standard.
  + Support for inserted cut off overflow pages. See [Cut-off page support](https://github.com/danfickle/openhtmltopdf/wiki/Cut-off-page-support) on the wiki.
  + Link areas and their hash link targets now repect transforms.
  + Bookmark targets now respect transforms.
  + Improved page placement for boxes. Now respects overflow and tranform properties.
  + Greater understanding which should make fixes and feature improvements easier.
+ Visual testing API is now available to use in the PDFBOX module. Please see [testing your PDF](https://github.com/danfickle/openhtmltopdf/wiki/Testing-Your-PDF-Document-Output) on the wiki. Thanks @red6.
+ [#333](https://github.com/danfickle/openhtmltopdf/pull/333) Upgraded PDFBox to 2.0.14 and PDFBox-Graphics2D to 0.21.
+ [#315](https://github.com/danfickle/openhtmltopdf/pull/315), [#79](https://github.com/danfickle/openhtmltopdf/issues/79) Accessible and tagged PDF support. See [PDF Accessibility (PDF UA, WCAG, Section 508) Support](https://github.com/danfickle/openhtmltopdf/wiki/PDF-Accessibility-(PDF-UA,-WCAG,-Section-508)-Support) on the wiki.
+ [#326](https://github.com/danfickle/openhtmltopdf/issues/326) Proper support for PDF/A standards with automatic regression testing. See [PDF/A Standards Compliance](https://github.com/danfickle/openhtmltopdf/wiki/PDF-A-Standards-Compliance) on the wiki.
+ [#328](https://github.com/danfickle/openhtmltopdf/issues/328) SVG with `page` rule was crashing in certain circumstances.
+ [#324](https://github.com/danfickle/openhtmltopdf/issues/324) Better logging with invalid or missing fonts.
+ [#320](https://github.com/danfickle/openhtmltopdf/pull/320) NPE prevention in case of incorrect font configuration.
+ [a145329](https://github.com/danfickle/openhtmltopdf/commit/a145329aa03bab62725a883b3a5c05ffd49996c8) Were using incorrect font-metrics in certain situations.
+ [#303](https://github.com/danfickle/openhtmltopdf/issues/303) Fixed: Table borders are partly transparent.
+ [#297](https://github.com/danfickle/openhtmltopdf/issues/297) Fixed: Border not printed with "overflow: hidden".
+ [#304](https://github.com/danfickle/openhtmltopdf/pull/304) Fix warnings for icon font without space inside PDF/A, add tests.
+ [#301](https://github.com/danfickle/openhtmltopdf/pull/301) Make loading resources from classpath work when openhtmltopdf is a named module.
+ [#232](https://github.com/danfickle/openhtmltopdf/issues/232) Were using JRE internal APIs.
+ [#289](https://github.com/danfickle/openhtmltopdf/issues/289) System.out.println("Getting image") in NaiveUserAgent.

Thanks to these people for pull-requests:
+ @rototor
+ @brundipub
+ @zimmi
+ @dnguyenminh

Finally, a big thanks to all issue reporters and extra thanks to those who help out in issues.


### 0.0.1-RC17
+ [#284](https://github.com/danfickle/openhtmltopdf/pull/284) [#288](https://github.com/danfickle/openhtmltopdf/issues/288) IMPORTANT: This release was brought forward due to a CVE in Apache Batik used by the optional SVG module.
  While this project strongly advises not to use untrusted XML either in SVG or XHTML, you may be using Batik in another part of your project and therefore it is a good idea to update. Thanks a lot @ghenadiibatalski, @chubbard
+ [#286](https://github.com/danfickle/openhtmltopdf/issues/286) [#281](https://github.com/danfickle/openhtmltopdf/issues/281) Fix for text decorations/background incorrect coverage in justified text. Thanks @koritakoa, @allartammik
+ [#280](https://github.com/danfickle/openhtmltopdf/issues/280) This will be the last release compatible with Java 7, from now on Java 8 or above will be required. Thanks for everyone's thoughts on this.

### 0.0.1-RC16
+ [#279](https://github.com/danfickle/openhtmltopdf/pull/279) [#264](https://github.com/danfickle/openhtmltopdf/pull/264)
IMPORTANT: This release was brought forward so that we link against PDFBOX-2.0.12 as previous versions had another DOS security vulnerability when parsing arbitary PDF files. Also there was a security issue in the old version of JSoup used by the optional jsoup-dom-converter module.
  While I believe these vulnerabilities should not impact this project directly, having an insecure library on your classpath may be dangerous if you use it for other tasks.
  Thanks @rototor, @dheid
+ [#279](https://github.com/danfickle/openhtmltopdf/pull/279) Support for testing and running on JDK-11. Extensive work by @rototor. Thanks.
+ [#278](https://github.com/danfickle/openhtmltopdf/pull/278) Support for additional PDF/A conformance levels.  Thanks @TheUnnamedDude
+ [87dc1a9](https://github.com/danfickle/openhtmltopdf/commit/87dc1a98f5821b4b80b6f85db93def53f770ecc5) Fixed nasty bug where positioned elements (absolute, fixed) were being printed twice. By @danfickle
+ [#271](https://github.com/danfickle/openhtmltopdf/pull/271) Support right-to-left list items. Thanks @ieugen for work, @sandre1 for reporting.
+ Much more work on the fast renderer. But not ready for prime time yet!


### 0.0.1-RC15
+ NOTE: Started moving [project documentation to wiki](https://github.com/danfickle/openhtmltopdf/wiki).
+ [#228](https://github.com/danfickle/openhtmltopdf/issues/228) Support for letter-spacing CSS property. By @danfickle
+ [#143](https://github.com/danfickle/openhtmltopdf/pull/143) Merging of remaining items thanks to @backslash47
  + Support for ```box-sizing:border-box```. With additional work (for min/max width/height) by @danfickle
  + Text justification for embedded unicode fonts
  + [#250](https://github.com/danfickle/openhtmltopdf/pull/250) Optional PDF/A conformance. Thanks @syjer
+ [#252](https://github.com/danfickle/openhtmltopdf/issues/252) Incorrect placement of form controls. Thanks @tiredelk
+ [#249](https://github.com/danfickle/openhtmltopdf/pull/249) Cache font metrics across runs to avoid having to load fallback fonts on each run. By @danfickle
+ [#254](https://github.com/danfickle/openhtmltopdf/pull/254) Allow use of SVG image in image tag. Thanks @syjer


### 0.0.1-RC14
+ IMPORTANT: This release was brought forward so that we link against PDFBOX-2.0.11 as previous versions had a security vulnerability when parsing arbitary PDF files.
  While I believe this should not impact this project directly, having an insecure library on your classpath may be dangerous if you use it for other tasks.
  [#241](https://github.com/danfickle/openhtmltopdf/issues/241) [#239](https://github.com/danfickle/openhtmltopdf/pull/239) Thanks @rototor, @cseblog
+ NOTE: This release incorportate a new faster renderer (especially for large documents) that is in alpha state. Specifically, it can be used with everything except inline-blocks.
  You can start testing it now with ````builder.useFastMode()```` [#180](https://github.com/danfickle/openhtmltopdf/issues/180) Thanks @rajaningle @javimartinez @dilworks @rototor
+ Image with CSS max-width and max-height incorrectly scaled [#242](https://github.com/danfickle/openhtmltopdf/issues/242) Thanks @koan00
+ Bold and italic emulation [#240](https://github.com/danfickle/openhtmltopdf/pull/240) Thanks @syjer @backslash47
+ Work on correctly outputting multiple HTML files to one PDF [#222](https://github.com/danfickle/openhtmltopdf/pull/222) Thanks @rototor
+ ONGOING: Attempt at fixing font file handle leak [#215](https://github.com/danfickle/openhtmltopdf/pull/215) Thanks @rototor
+ Don't throw NPE when no base URI is provided [#206](https://github.com/danfickle/openhtmltopdf/issues/206)
+ [Fix link annotation placement in margin or generated boxes](https://github.com/danfickle/openhtmltopdf/issues/213) Thanks @jesselong, @Kuhlware, @markhowardnz 


### 0.0.1-RC13
+ [Use common base class for PDF and Java2D builder - SOME IMPORTS MAY CHANGE](https://github.com/danfickle/openhtmltopdf/pull/177) Thanks @rototor
+ Major work on transforms, we're getting there, but still test well before use. Thanks @rototor
+ [Make it possible to set a PDF producer](https://github.com/danfickle/openhtmltopdf/pull/158) Thanks @schmitch
+ [Support for JFreeCharts diagrams with simple markup](https://github.com/danfickle/openhtmltopdf/pull/165) Thanks @rototor
+ [Ability to stamp another PDF on page](https://github.com/danfickle/openhtmltopdf/pull/165) Thanks @rototor
+ [Support for Latex](https://github.com/danfickle/openhtmltopdf/pull/177) Thanks @rototor
+ [Support for MathML](https://github.com/danfickle/openhtmltopdf/issues/161#issuecomment-365844595) Thanks @m-a-t
+ [Support for HTML and MathML character entities such as nbsp, etc](https://github.com/danfickle/openhtmltopdf/blob/19828ff579863fdbd0ffe28108d3b14626ec64da/openhtmltopdf-examples/src/main/resources/documentation/documentation.md#character-entities)
+ [Allow user to construct their own PDDocument so memory options can be specified](https://github.com/danfickle/openhtmltopdf/issues/180) Thanks @rajaningle, @javimartinez
+ [Fixed silly bug and got dramatic performance improvement for large documents](https://github.com/danfickle/openhtmltopdf/issues/170#issuecomment-376441271)
+ [Fix for XML loading problems where older version of xerces was being picked up](https://github.com/danfickle/openhtmltopdf/issues/187) Thanks @sosnut
+ [Fix for XML loading problems with JBoss,Wildfly](https://github.com/danfickle/openhtmltopdf/issues/54) Thanks @estevandiedrich, @alanhay
+ [Support image maps on img, object and svg](https://github.com/danfickle/openhtmltopdf/pull/163) Uses a kong polygon tesselation implementation by [sunshine2k](https://www.sunshine2k.de/coding/java/Polygon/Kong/Kong.html)
+ API BREAKING CHANGE: [Support custom shape <=> link maps in object drawers](https://github.com/danfickle/openhtmltopdf/pull/163)

Note: Shaped links only work in Acrobat Reader. All other PDF reader seem to ignore them.

### 0.0.1-RC12
+ [Upgrade the PDFBox to 2.0.8 and PDFBox-Graphics2D to 0.10 versions again](https://github.com/danfickle/openhtmltopdf/pull/150) Thanks @rototor
+ [Fix incorrect strikethrough offset](https://github.com/danfickle/openhtmltopdf/issues/136) Thanks @alebar, @backslash47, @izhenka
+ Allow percentages for max-width and max-height of images Thanks @backslash47
+ [Better sizing system for inline SVG images](https://github.com/danfickle/openhtmltopdf/issues/128) Thanks @harbulot
+ [Allow uri resolver to resolve uri before checking if a data uri](https://github.com/danfickle/openhtmltopdf/pull/132) Thanks @AlbanSeurat
+ [Ability to run examples from maven](https://github.com/danfickle/openhtmltopdf/pull/108) Thanks @jartysiewicz
+ [Fix to allow jar scheme urls](https://github.com/danfickle/openhtmltopdf/issues/125) Thanks @geesen
+ [Font mapping in custom object drawer rather than using vector shapes](https://github.com/danfickle/openhtmltopdf/pull/121) Thanks @rototor
+ [Upgraded PDFBOX to 2.0.7, ICU4J to 59.1 and PDFBOX-GRAPHICS2D to 0.7](https://github.com/danfickle/openhtmltopdf/pull/121) Thanks @rototor
+ [Implemented CSS3 flowing text columns](https://github.com/danfickle/openhtmltopdf/issues/60#issuecomment-310959602) Thanks @miminno
+ [FIX: Don't write miter values of zero into the PDF, fixes dotted/dashed lines in Acrobat Reader](https://github.com/danfickle/openhtmltopdf/issues/135)

### 0.0.1-RC11
+ [Allow collapsed borders with table pagination](https://github.com/danfickle/openhtmltopdf/issues/97) Thanks @Epimetheus89 
+ [FIX: Dispose of thread local when renderer is cleaned up](https://github.com/danfickle/openhtmltopdf/issues/94) Thanks @rototor
+ [FIX: Link handling when identical link positions on multiple pages](https://github.com/danfickle/openhtmltopdf/pull/95) Thanks @rototor
+ [FIX: Allow user to disable logging](https://github.com/danfickle/openhtmltopdf/pull/90) Thanks @GrammyTraore
+ [Handle TrueType font collections added in builder](https://github.com/danfickle/openhtmltopdf/pull/89) Thanks @rototor
+ [Implement custom object drawer for Java2D output](https://github.com/danfickle/openhtmltopdf/pull/87) Thanks @rototor
+ [Upgrade PDFBox library to 2.05](https://github.com/danfickle/openhtmltopdf/pull/86) Thanks @rototor, PDFBox team


### 0.0.1-RC10
+ [Support for inline SVG images](https://github.com/danfickle/openhtmltopdf/issues/23) Thanks @rototor
+ [Support for outputting paged or continuous images](https://github.com/danfickle/openhtmltopdf/issues/73#issuecomment-291070264) Thanks @rototor


### 0.0.1-RC9
+ [Don't output acroform for formless document](https://github.com/danfickle/openhtmltopdf/issues/52) Thanks @aleksandr-m
+ [Upgraded to PDFBox 2.0.4](https://github.com/danfickle/openhtmltopdf/issues/59) Thanks PDFBox team
+ [Fixed memory leak - properly - in image processing on some JREs](https://github.com/danfickle/openhtmltopdf/issues/51) Thanks @skjardenCode and @MartyMcMartface

### 0.0.1-RC8
+ [Initial support for CSS transform property](https://github.com/danfickle/openhtmltopdf/issues/38) Thanks @rototor
+ [Add support for max-width and max-height on img elements](https://github.com/danfickle/openhtmltopdf/pull/48) Thanks @achuinard

### 0.0.1-RC7
+ SECURITY ISSUE: [Prevent XXE Attacks](https://github.com/danfickle/openhtmltopdf/issues/44) Thanks @lillesand
+ BREAKING CHANGE: [Support for dir attribute and bdi element](https://github.com/danfickle/openhtmltopdf/issues/9#issuecomment-257072765)
+ [Do not download fonts that are not actually used](https://github.com/danfickle/openhtmltopdf/issues/43)
+ [Fixed resolution of relative URLs in inline style declarations](https://github.com/danfickle/openhtmltopdf/issues/27)
+ [Added support for hidden controls and submit controls with values](https://github.com/danfickle/openhtmltopdf/issues/24)
+ [Corrected naming scheme for form controls](https://github.com/danfickle/openhtmltopdf/issues/42) Thanks @scoldwell

### 0.0.1-RC5
+ [Reimplemented text justification](https://github.com/danfickle/openhtmltopdf/pull/33) Thanks @hiddendog 
+ [Fixed bug in table borders](https://github.com/danfickle/openhtmltopdf/pull/34) Thanks @rototor
+ [Added support for -fs-page-break-min-height CSS property](https://github.com/danfickle/openhtmltopdf/pull/31) Thanks @rototor
+ [Added support for -fs-table-paginate-repeated-visible CSS property](https://github.com/danfickle/openhtmltopdf/pull/32) Thanks @rototor
+ BREAKING CHANGE: Removed font subset method in builder, replaced with property in font face rule. Example: ````-fs-font-subset: complete-font;````
+ [Added support for text, password, textarea, submit, reset, checkbox, radio and select - multiple and single - controls](https://github.com/danfickle/openhtmltopdf/issues/24)
+ BREAKING CHANGE: Changed bi-directional method names in builder to be more consistent.
+ [Add method to builder to specify custom text transformers](https://github.com/danfickle/openhtmltopdf/issues/28)
+ [Add method to builder to specify a custom line breaker](https://github.com/danfickle/openhtmltopdf/issues/25) Thanks @Magotchi

### 0.0.1-RC4
+ Add method to builder to specify replacement text if no specified font can render a character.
+ [BREAKING CHANGE: Reworked URI resolver, changed FSUriResolver interface and made sure it is used everywhere](https://github.com/danfickle/openhtmltopdf/issues/27) - See example in integration guide.
+ Fixed issue where different size pages in the same document were not being recognized.
+ Add method to builder to specify default page size. Example: ````builder.useDefaultPageSize(PdfRendererBuilder.PAGE_SIZE_LETTER_WIDTH, PdfRendererBuilder.PAGE_SIZE_LETTER_HEIGHT, PdfRendererBuilder.PAGE_SIZE_LETTER_UNITS);````
+ BREAKING CHANGE: If no page size is specified in builder or CSS use A4, rather than locale dependent. See above.
+ [Silently discard control characters, etc at the rendering stage](https://github.com/danfickle/openhtmltopdf/issues/21#issuecomment-227850449) Thanks @scoldwell
+ [Fixed incorrect spacing when characters are replaced](https://github.com/danfickle/openhtmltopdf/issues/26) Thanks @scoldwell
 
### 0.0.1-RC3
+ [Experimental and unstable SVG support - early prototype](https://github.com/danfickle/openhtmltopdf/issues/23)
+ [Replaced non-breaking spaces - and other unusual spaces - with normal space if font does not support them](https://github.com/danfickle/openhtmltopdf/issues/21) Thanks @rototor
+ [Added a method for adding a PDF font using an input stream](https://github.com/danfickle/openhtmltopdf/issues/20) Thanks @aleksandr-m
+ [Added support for plugging in an external URI resolver](https://github.com/danfickle/openhtmltopdf/issues/18)
+ [Added support for plugging in an external cache](https://github.com/danfickle/openhtmltopdf/issues/18)
+ [Added support for font fallback for Java2D](https://github.com/danfickle/openhtmltopdf/issues/10) Thanks @willamette
+ [Fixed crash issue when document contained CDATA sections](https://github.com/danfickle/openhtmltopdf/issues/16) Thanks @hiddendog

### 0.0.1-RC2
+ [Added support for font fallback for PDFs](https://github.com/danfickle/openhtmltopdf/issues/10)
+ [Added fluent builder style API for PDF conversion](https://github.com/danfickle/openhtmltopdf/issues/14)
+ [Added ability to plugin external HTTP/HTTPS implementation](https://github.com/danfickle/openhtmltopdf/issues/13)
+ [Added Jsoup HTML5 to DOM converter module](https://github.com/danfickle/openhtmltopdf/issues/12)
+ Fixed divide-by-zero error in BorderPainter class. Thanks @fenrhil
+ [Added slf4j logging facade adapter](https://github.com/danfickle/openhtmltopdf/issues/11)
+ [Added right-to-left(RTL) and bi-directional text support](https://github.com/danfickle/openhtmltopdf/issues/9)
+ [Added output device using PDF-BOX 2.0.0](https://github.com/danfickle/openhtmltopdf/issues/1)
+ [Make sure XML Document Builder doesn't resolve external DTDs](https://github.com/danfickle/openhtmltopdf/issues/2)
+ [Removed obsolete ITEXT based output devices](https://github.com/danfickle/openhtmltopdf/issues/4)
+ [Removed SWT support](https://github.com/danfickle/openhtmltopdf/issues/6)
+ Regressions (please open issue if required):
    + <s>PDF form controls.</s> [Reimplemented in RC5](https://github.com/danfickle/openhtmltopdf/issues/24)
    + PDF font types other than built-in and truetype.
    + XMP PDF metadata in PDFs.
    + <s>PDF encryption.</s> [Reimplemented in RC5](https://github.com/danfickle/openhtmltopdf/issues/30)
    + <s>[PDF text justification](https://github.com/danfickle/openhtmltopdf/issues/3)</s> [Reimplemented in RC5](https://github.com/danfickle/openhtmltopdf/pull/33) 
