---
title: XslCompiledTransform 類別的輸出選項
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 91ce8cba-386c-411e-bb38-0891a0393c0a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 694d2be51d025ab054caf19e4aa2900216ad5b2e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45678369"
---
# <a name="output-options-on-the-xslcompiledtransform-class"></a>XslCompiledTransform 類別的輸出選項
本主題討論可用的 XSLT 輸出選項。 您可以指定樣式表中或 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法上的輸出選項。  
  
## <a name="xsloutput-element"></a>xsl:output 項目  
 `xsl:output` 項目指定輸出的選項。 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法指定的輸出型別決定 `xsl:output` 選項的行為。  
  
 下表說明當輸出型別是一種資料流或 `xsl:output` 時，<xref:System.IO.TextWriter> 項目上可用之每個屬性的行為。  
  
|屬性名稱|行為|  
|--------------------|--------------|  
|方法|支援。|  
|版本|忽略。 對於 XML 版本始終為 1.0，對於 HTML 則為 4.0。|  
|編碼|輸出至 <xref:System.IO.TextWriter> 時忽略。 使用 <xref:System.IO.TextWriter.Encoding%2A?displayProperty=nameWithType> 屬性代替。|  
|omit-xml-declaration|支援。|  
|獨立|支援。|  
|doctype-public|支援。|  
|doctype-system|支援。|  
|cdata-section-elements|支援。|  
|indent|支援。|  
|media-type|支援。|  
  
#### <a name="sending-output-to-an-xmlwriter"></a>傳送輸出至 XmlWriter  
 如果樣式表使用 `xsl:output` 項目，且輸出型別為 <xref:System.Xml.XmlWriter> 物件，則在建立 <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> 物件時應使用 <xref:System.Xml.XmlWriter> 屬性。 <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A?displayProperty=nameWithType> 屬性傳回 <xref:System.Xml.XmlWriterSettings> 物件，該物件包含衍生自已編譯樣式表之 `xsl:output` 項目的資訊。 可將此 <xref:System.Xml.XmlWriterSettings> 物件傳遞給 <xref:System.Xml.XmlWriter.Create%2A?displayProperty=nameWithType> 方法，以正確的設定建立 <xref:System.Xml.XmlWriter> 物件。  
  
## <a name="output-types"></a>輸出型別  
 下列清單說明可用於 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 命令的輸出型別。  
  
#### <a name="xmlwriter"></a>XmlWriter  
 <xref:System.Xml.XmlWriter> 類別可寫出 XML 資料流或檔案。 您可以藉由使用 <xref:System.Xml.XmlWriter> 類別，指定要在 <xref:System.Xml.XmlWriterSettings> 物件上支援的功能 (包含輸出選項)。 <xref:System.Xml.XmlWriter> 類別是 <xref:System.Xml> 架構不可或缺的一部分。 使用此輸出型別，將輸出結果傳遞至其他 XML 處理序。  
  
#### <a name="string"></a>String  
 使用此輸出型別，指定輸出檔案的 URI。  
  
#### <a name="stream"></a>資料流  
 資料流是位元組序列的抽象，例如，檔案、輸入/輸出裝置、處理序間的通訊管道或 TCP/IP 通訊端。 <xref:System.IO.Stream> 類別及其衍生類別提供不同類型輸入及輸出的一般檢視，可讓程式設計人員看不到作業系統及基礎裝置的特定詳細資訊。  
  
 使用此輸出型別傳送資料至 <xref:System.IO.FileStream>、<xref:System.IO.MemoryStream> 或輸出資料流 (`Response.OutputStream`)。  
  
#### <a name="textwriter"></a>TextWriter  
 <xref:System.IO.TextWriter> 會寫入連續的字元。 它會在 <xref:System.IO.StringWriter> 及 <xref:System.IO.StreamWriter> 類別中實作，這些類別會將字元分別寫入到字串或資料流。 要輸出至字串時，請使用此輸出型別。  
  
## <a name="notes"></a>注意  
  
-   寫出空白標記時，請在項目名稱的最後一個字元與反斜線之間寫入一個空格，例如 `<myElement />`。 如此可讓舊版瀏覽器正確顯示所產生的 HTML 頁面。  
  
## <a name="see-also"></a>另請參閱

- [XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations.md)
