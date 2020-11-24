---
title: XslTransform 的輸出
ms.date: 03/30/2017
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
ms.openlocfilehash: ebe276a9627a36f1248f0043af6c82e76fe7fd78
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691366"
---
# <a name="outputs-from-an-xsltransform"></a>XslTransform 的輸出

由於樣式表可以使用 `<xsl:output>` 陳述式以及 `method` 屬性決定輸出格式，因此下表將說明在使用 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法寫入輸出，且輸出格式宣告為 <xref:System.IO.Stream> 或 <xref:System.IO.TextWriter> 時，將產生何種輸出格式。  
  
> [!NOTE]
> 在 .NET Framework 2.0 中，<xref:System.Xml.Xsl.XslTransform> 類別已過時。 您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。 如需詳細資訊，請參閱[使用 XslCompiledTransform 類別](using-the-xslcompiledtransform-class.md)和[從 XslTransform 類別移轉](migrating-from-the-xsltransform-class.md)。  
  
 由於樣式表可以使用 `<xsl:output>` 陳述式以及 `method` 屬性決定輸出格式，因此下表將說明在使用 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法寫入輸出，且輸出格式宣告為 <xref:System.IO.Stream> 或 <xref:System.IO.TextWriter> 時，將產生何種輸出格式。 下表說明在輸出型別由 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法進行宣告，並且搭配使用 `<xsl:output>` 陳述式時，將發生哪些情況：  
  
|\<xsl:output method = > 屬性|結果格式|  
|-----------------------------------------|-------------------|  
|method="xml"|XML|  
|method="html"|HTML|  
|method="text"|文字|  
  
> [!NOTE]
> 注意：當 `<xsl:output>` 方法的輸出是 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 或 <xref:System.Xml.XmlReader> 時，將會忽略 <xref:System.Xml.XmlWriter> 陳述式。  
  
 當 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法輸出為 <xref:System.IO.Stream> 或 <xref:System.IO.TextWriter> 時，可支援下列屬性：  
  
- encoding*  
  
- omit-xml-declaration  
  
- 獨立  
  
- doctype-public  
  
- doctype-system  
  
- cdata-section-elements  
  
- indent  
  
    > [!NOTE]
    > \*當 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法傳送其輸出給 <xref:System.IO.TextWriter> 時，將會忽略編碼屬性。 會改用 <xref:System.IO.TextWriter> 上的編碼屬性。
  
 當 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法輸出是 <xref:System.IO.Stream> 時，將會忽略下列屬性：  
  
- 版本：版本一律為 1.0  
  
- 媒體類型：媒體類型  
  
## <a name="escaping-special-characters"></a>逸出特殊字元  

 `<xsl:text disable-output-escaping>` 標記可用來指示特殊字元是否必須逸出為 XML 格式 (例如，以 `<&lt>` 取代 `"<"` 符號)，或必須保持現有的狀況。 當轉換為 `disable-output-escaping` 或 <xref:System.Xml.XmlReader> 物件時，會忽略 <xref:System.Xml.XmlWriter> 屬性，這對於特殊字元不會有任何影響。  
  
## <a name="see-also"></a>另請參閱

- [XslTransform 類別實作 XSLT 處理器](xsltransform-class-implements-the-xslt-processor.md)
