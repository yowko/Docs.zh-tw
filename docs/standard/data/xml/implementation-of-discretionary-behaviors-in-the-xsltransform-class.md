---
title: XslTransform 類別中的 Discretionary 行為實作
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d2758ea1-03f6-47bd-88d2-0fb7ccdb2fab
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fcc294f09172eb2029f92d2c05821837aa10c35f
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591496"
---
# <a name="implementation-of-discretionary-behaviors-in-the-xsltransform-class"></a>XslTransform 類別中的 Discretionary 行為實作

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> 類別在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中已過時。 您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。 如需詳細資訊，請參閱[使用 XslCompiledTransform 類別](using-the-xslcompiledtransform-class.md)和[從 XslTransform 類別移轉](migrating-from-the-xsltransform-class.md)。

判別行為會以[全球資訊網協會 (W3C) XSL 轉換 (XSLT) 1.0 版建議事項](https://www.w3.org/TR/1999/REC-xslt-19991116)中所列行為說明，其中實作提供者可選擇數個可能選項之一，作為處理狀況的方法。 例如，在 7.3 節＜建立處理指示＞(英文) 中，W3C 建議事項指出如果具現化 `xsl:processing-instruction` 的內容會建立非文字節點的節點，就會產生錯誤。 針對某些問題，W3C 會在處理器決定從錯誤復原時通知要採取的決策。 針對 7.3 節中的問題，W3C 指出只要忽略節點及其內容，實作即可從這項錯誤中復原。

因此，針對 W3C 所允許的每個判別行為，下表列出為 <xref:System.Xml.Xsl.XslTransform> 類別 .NET Framework 實作所實作的判別行為，以及在 W3C XSLT 1.0 建議事項中的哪一節討論了此問題。

|問題|行為|區段|
|-------------|--------------|-------------|
|文字節點同時符合 `xsl:strip-space` 及 `xsl:preserve-space`。|復原|3.4|
|來源節點符合一個以上的範本 (Template) 規則。|復原|5.5|
|命名空間統一資源識別元 (URI) 會被宣告成多個命名空間 URI 的別名，且全都具有相同的匯入優先順序。|復原|7.1.1|
|從屬性值範本產生的 `xsl:attribute` 與 `xsl:element` 中的名稱屬性，不是有效的限定名稱 (QName)。|擲回例外狀況|7.1.12 和 7.1.3|
|在子節點已經加入項目節點之後，將屬性加入至項目。|復原|7.1.3|
|將屬性加入至不是項目節點的其他節點。|復原|7.1.3|
|`xsl:attribute` 項目內容的執行個體化不是文字節點。|復原|7.1.3|
|兩個屬性集具有相同的匯入優先順序與展開名稱。 兩個屬性集會具有相同的屬性，且沒有其他屬性集會含有名稱相同而重要性較高的共同屬性。|復原|7.1.4|
|`xsl:processing-instruction` 名稱屬性不會同時產生無冒號名稱 (NCName) 和處理指示目標。|復原|7.3|
|具現化 `xsl:processing-instruction` 的內容會建立非文字節點的節點。|復原|7.3|
|具現化 `xsl:processing-instruction` 內容的結果包含字串 "`?>`"。|復原|7.3|
|具現化 `xsl:comment` 內容的結果包含字串 --，或以 - 為結尾。|復原|7.4|
|具現化 `xsl:comment` 內容的結果會建立非文字節點的節點。|復原|7.4|
|變數繫結項目內的範本會傳回屬性節點或命名空間節點。|復原|11.2|
|從傳遞至文件函式的 URI 上擷取資源時發生錯誤。|擲回例外狀況|12.1|
|文件函式中的 URI 參考包含片段識別項，且處理片段識別項時發生錯誤。|擲回例外狀況|12.1|
|在 `cdata-section-elements` 中有多個屬性具有名稱不是 `xls:output` 的相同名稱，這些屬性具有相同的匯入優先順序。|復原|16|
|處理器不支援 `encoding` 項目的 `xsl:output` 屬性中所指定的字元編碼值。|復原|16.1|
|`disable-output-escaping` 用於文字節點，而且該文字節點會用來建立結果樹狀結構的文字節點以外的項目。|會忽略 `disable-output-escaping` 屬性|16.4|
|如果結果樹狀結構片段包含啟用輸出逸出的文字節點，則結果樹狀結構片段會轉換成數字或字串。|略過|16.4|
|對不能以 XSLT 處理器用來輸出的編碼方式，停用表示的字元輸出逸出。|略過|16.4|
|在項目加入子系或屬性後，加入命名空間節點|復原|Errata e25|
|`xsl:number` 是 NaN、無限或小於 0.5。|復原|Errata e24|
|文件函式的第二個引數節點集是空的，且 URI 參考是相對的。|復原|Errata e14|

W3C [XSL 轉換 (XSLT) 1.0 版規格錯誤](https://www.w3.org/1999/11/REC-xslt-19991116-errata/)中提供錯誤的章節。

## <a name="custom-defined-implementation-behaviors"></a>自訂定義的實作行為

有一些行為對於 <xref:System.Xml.Xsl.XslTransform> 類別實作而言是唯一的。 本節將討論 `xsl:sort` 的提供者特定實作，以及 <xref:System.Xml.Xsl.XslTransform> 類別所支援的選擇性功能。

## <a name="xslsort"></a>xsl:sort

使用轉換進行排序時，W3C XSLT 1.0 版建議事項會進行某些觀察。 包括：

- 兩個 XSLT 處理器可以是一致的處理器，但仍可以不同地排序。

- 並非所有 XSLT 處理器支援相同的語言。

- 至於語言方面，不同的處理器在 `xsl:sort.` 中未指定之特定語言上的排序方式會有所不同。

下表說明針對使用 <xref:System.Xml.Xsl.XslTransform> 之 .NET Framework 轉換實作中的每個資料類型，所實作的排序行為：

|資料類型|排序行為|
|---------------|----------------------|
|Text|資料使用 Common Language Runtime (CLR) 字串進行排序。比較方法和文化地區設定 (Locale)。 當資料型別等於 "text" 時，<xref:System.Xml.Xsl.XslTransform> 類別中的排序行為會與 CLR 字串比較行為相同。|
|number|數值會視為 XML 路徑語言 (XPath) 數字，並會依據 W3C [XML 路徑語言 (XPath) 1.0 版建議事項 3.5 節](https://www.w3.org/TR/1999/REC-xpath-19991116/#numbers)中的詳細描述進行排序。|

## <a name="optional-features-supported"></a>支援的選擇性功能

下表說明 XSLT 處理器於 <xref:System.Xml.Xsl.XslTransform> 類別中實作的選擇性功能。

|功能|參考位置|注意|
|-------------|------------------------|-----------|
|`disable-output-escaping` 和 `<xsl:text...>` 標記上的 `<xsl:value-of...>` 屬性。|W3C XSLT 1.0 版建議事項，<br /><br /> 16.4 節|在 `disable-output-escaping`、`xsl:text` 或 `xsl:value-of` 項目中使用 `xsl:comment` 或 `xsl:processing-instruction` 項目時，會忽略 `xsl:attribute` 屬性。<br /><br /> 不支援包含文字且文字輸出已被逸出的結果樹狀結構片段。<br /><br /> 當轉換為 <xref:System.Xml.XmlReader> 或 <xref:System.Xml.XmlWriter> 物件時，disable-output-escaping 屬性會被忽略。|

## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Xsl.XslTransform>
- [XslTransform 類別實作 XSLT 處理器](xsltransform-class-implements-the-xslt-processor.md)
- [使用 XslTransform 類別進行 XSLT 轉換](xslt-transformations-with-the-xsltransform-class.md)
- [轉換中的 XPathNavigator](xpathnavigator-in-transformations.md)
- [轉換中的 XPathNodeIterator](xpathnodeiterator-in-transformations.md)
- [XslTransform 的 XPathDocument 輸入](xpathdocument-input-to-xsltransform.md)
- [XslTransform 的 XmlDataDocument 輸入](xmldatadocument-input-to-xsltransform.md)
- [XslTransform 的 XmlDocument 輸入](xmldocument-input-to-xsltransform.md)
