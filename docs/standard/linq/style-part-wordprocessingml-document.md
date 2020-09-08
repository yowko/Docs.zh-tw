---
title: WordprocessingML 檔的樣式部分-LINQ to XML
description: 查看組成 Office Open XML WordprocessingML 檔樣式部分的 XML 範例。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 5458bccf-3898-4661-904b-7d280c9239a9
ms.openlocfilehash: 9283a62014b8d035f717f506dcf8a5850981abb5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552211"
---
# <a name="style-part-of-a-wordprocessingml-document-linq-to-xml"></a><span data-ttu-id="5403e-103">WordprocessingML 檔的樣式部分 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="5403e-103">Style part of a WordprocessingML document (LINQ to XML)</span></span>

<span data-ttu-id="5403e-104">本文顯示組成 Office Open XML WordprocessingML 檔樣式部分的 XML 範例。</span><span class="sxs-lookup"><span data-stu-id="5403e-104">This article shows an example of the XML that makes up the style part of an Office Open XML WordprocessingML document.</span></span>

## <a name="example-the-xml-that-makes-up-the-style-part-of-a-document"></a><span data-ttu-id="5403e-105">範例：組成檔樣式部分的 XML</span><span class="sxs-lookup"><span data-stu-id="5403e-105">Example: The XML that makes up the style part of a document</span></span>

<span data-ttu-id="5403e-106">下列範例為建立 Office Open XML WordprocessingML 文件樣式部分的 XML。</span><span class="sxs-lookup"><span data-stu-id="5403e-106">The following example is the XML that makes up the style part of an Office Open XML WordprocessingML document.</span></span>

<span data-ttu-id="5403e-107">預設段落樣式擁有包含下列開頭標記的項目：</span><span class="sxs-lookup"><span data-stu-id="5403e-107">The default paragraph style has an element with the following opening tag:</span></span>

```xml
<w:style w:type="paragraph" w:default="1" w:styleId="Normal">
```

<span data-ttu-id="5403e-108">當您撰寫查詢來尋找預設樣式識別項前，您必須知道這個資訊，該查詢才能識別包含預設樣式之段落的樣式。</span><span class="sxs-lookup"><span data-stu-id="5403e-108">You need to know this information when you write the query to find the default style identifier, so that the query can identify the style of paragraphs that have the default style.</span></span>

<span data-ttu-id="5403e-109">請注意，與 Microsoft Word 所產生的一般文件相較，這些文件非常簡單。</span><span class="sxs-lookup"><span data-stu-id="5403e-109">Note that these documents are very simple when compared to typical documents that Microsoft Word generates.</span></span> <span data-ttu-id="5403e-110">在許多情況下，Word 會節省大量的額外資訊、額外的格式設定和中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5403e-110">In many cases, Word saves a great deal of additional information, additional formatting, and metadata.</span></span> <span data-ttu-id="5403e-111">此外，Word 不會將這些行格式化，如此範例所示：相反地，會在不縮排的情況下儲存 XML。</span><span class="sxs-lookup"><span data-stu-id="5403e-111">Furthermore, Word doesn't format the lines to be easily readable as in this example; instead, the XML is saved without indentation.</span></span> <span data-ttu-id="5403e-112">但是，所有 WordprocessingML 文件都會共用相同的 XML 基本組織結構。</span><span class="sxs-lookup"><span data-stu-id="5403e-112">However, all WordprocessingML documents share the same basic XML shape.</span></span> <span data-ttu-id="5403e-113">因此，本節提供的查詢將會使用更複雜的檔。</span><span class="sxs-lookup"><span data-stu-id="5403e-113">Because of this, the queries presented in this section will work with more complicated documents.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<w:styles
    xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"
    xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">
  <w:docDefaults>
    <w:rPrDefault>
      <w:rPr>
        <w:rFonts
            w:ascii="Times New Roman"
            w:eastAsia="Times New Roman"
            w:hAnsi="Times New Roman"
            w:cs="Times New Roman" />
        <w:sz w:val="22" />
        <w:szCs w:val="22" />
        <w:lang w:val="en-US" w:eastAsia="en-US" w:bidi="ar-SA" />
      </w:rPr>
    </w:rPrDefault>
    <w:pPrDefault />
  </w:docDefaults>
  <w:style w:type="paragraph" w:default="1" w:styleId="Normal">
    <w:name w:val="Normal" />
    <w:qFormat />
    <w:rPr>
      <w:sz w:val="24" />
      <w:szCs w:val="24" />
    </w:rPr>
  </w:style>
  <w:style w:type="paragraph" w:styleId="Heading1">
    <w:name w:val="heading 1" />
    <w:basedOn w:val="Normal" />
    <w:next w:val="Normal" />
    <w:link w:val="Heading1Char" />
    <w:uiPriority w:val="99" />
    <w:qFormat />
    <w:rsid w:val="006027C7" />
    <w:pPr>
      <w:keepNext />
      <w:spacing w:before="240" w:after="60" />
      <w:outlineLvl w:val="0" />
    </w:pPr>
    <w:rPr>
      <w:rFonts w:ascii="Arial" w:hAnsi="Arial" w:cs="Arial" />
      <w:b />
      <w:bCs />
      <w:kern w:val="32" />
      <w:sz w:val="32" />
      <w:szCs w:val="32" />
    </w:rPr>
  </w:style>
  <w:style w:type="character" w:default="1" w:styleId="DefaultParagraphFont">
    <w:name w:val="Default Paragraph Font" />
    <w:uiPriority w:val="99" />
    <w:semiHidden />
  </w:style>
  <w:style w:type="table" w:default="1" w:styleId="TableNormal">
    <w:name w:val="Normal Table" />
    <w:uiPriority w:val="99" />
    <w:semiHidden />
    <w:unhideWhenUsed />
    <w:qFormat />
    <w:tblPr>
      <w:tblInd w:w="0" w:type="dxa" />
      <w:tblCellMar>
        <w:top w:w="0" w:type="dxa" />
        <w:left w:w="108" w:type="dxa" />
        <w:bottom w:w="0" w:type="dxa" />
        <w:right w:w="108" w:type="dxa" />
      </w:tblCellMar>
    </w:tblPr>
  </w:style>
  <w:style w:type="numbering" w:default="1" w:styleId="NoList">
    <w:name w:val="No List" />
    <w:uiPriority w:val="99" />
    <w:semiHidden />
    <w:unhideWhenUsed />
  </w:style>
  <w:style w:type="character" w:customStyle="1" w:styleId="Heading1Char">
    <w:name w:val="Heading 1 Char" />
    <w:basedOn w:val="DefaultParagraphFont" />
    <w:link w:val="Heading1" />
    <w:uiPriority w:val="9" />
    <w:rsid w:val="009765E3" />
    <w:rPr>
      <w:rFonts
          w:asciiTheme="majorHAnsi"
          w:eastAsiaTheme="majorEastAsia"
          w:hAnsiTheme="majorHAnsi"
          w:cstheme="majorBidi" />
      <w:b />
      <w:bCs />
      <w:kern w:val="32" />
      <w:sz w:val="32" />
      <w:szCs w:val="32" />
    </w:rPr>
  </w:style>
  <w:style w:type="paragraph" w:customStyle="1" w:styleId="Code">
    <w:name w:val="Code" />
    <w:aliases w:val="c" />
    <w:uiPriority w:val="99" />
    <w:rsid w:val="006027C7" />
    <w:pPr>
      <w:spacing w:after="60" w:line="300" w:lineRule="exact" />
    </w:pPr>
    <w:rPr>
      <w:rFonts w:ascii="Courier New" w:hAnsi="Courier New" />
      <w:noProof />
      <w:color w:val="000080" />
      <w:sz w:val="20" />
      <w:szCs w:val="20" />
    </w:rPr>
  </w:style>
</w:styles>
```
