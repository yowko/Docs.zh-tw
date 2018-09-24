---
title: 解析外部的 XSLT 樣式表和文件
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 39e8afd8c22ca757141d2a7b556b115f8380e731
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46583937"
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>解析外部的 XSLT 樣式表和文件
在轉換期間，您可能需要進行數次外部資源解析。  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> 類別在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中已過時。 您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。  
  
 在轉換期間，您可能需要進行數次外部資源解析：  
  
-   在 <xref:System.Xml.Xsl.XslTransform.Load%2A> 期間用來尋找外部樣式表。  
  
-   在 <xref:System.Xml.Xsl.XslTransform.Load%2A> 期間，用來解析樣式表中找到的任何 `<xsl:include>` 或 `<xsl:import>` 項目。  
  
-   在 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 期間，用來解析任何 `document()` 函式。  
  
## <a name="using-the-xmlresolver-class"></a>使用 XmlResolver 類別  
 如果存取網路資源需要驗證，請使用具有可傳遞 <xref:System.Xml.Xsl.XslTransform.Load%2A> 物件之 <xref:System.Xml.XmlResolver> 參數的 <xref:System.Xml.XmlResolver> 方法，該物件具有必要的認證屬性集。  
  
 若要使用自訂的 <xref:System.Xml.XmlResolver>，或需要指定不同的認證，可參考下表根據外部資源何時需進行解析所列出之必要的工作。  
  
|需要解析的程序|必要的工作|  
|--------------------------------------|-------------------|  
|在 <xref:System.Xml.Xsl.XslTransform.Load%2A> 期間用來尋找樣式表。|若樣式表位於需要認證的資源上，請指定以 <xref:System.Xml.Xsl.XslTransform.Load%2A> 當做參數的多載 <xref:System.Xml.XmlResolver> 方法。|  
|在 <xref:System.Xml.Xsl.XslTransform.Load%2A> 期間用來解析 `<xsl:include>` 或 `<xsl:import>`。|指定以 <xref:System.Xml.Xsl.XslTransform.Load%2A> 當做參數的多載 <xref:System.Xml.XmlResolver> 方法。 <xref:System.Xml.XmlResolver> 是用來載入 `import` 或 `include` 陳述式所參考的樣式表。 若傳入 `null`，則不會解析外部資源。|  
|在轉換期間用來解析任何 `document()` 函式。|在轉換期間指定 <xref:System.Xml.XmlResolver>，其方式是使用接受 <xref:System.Xml.XmlResolver> 引數的 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法。|  
  
 除了由輸入資料流所提供的初始 XML 資料之外，`document()` 函式還可從樣式表擷取其他的 XML 資源。 由於此函式可併入能夠放置於其他位置的 XML 資料，因此您可以將含有 <xref:System.Xml.XmlResolver> 值的 `null` 提供給 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法，以防止 `document()` 函式的執行。 若要使用 `document()` 函式，除了具有適當的使用權限集合外，請使用以 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 當做參數的 <xref:System.Xml.XmlResolver> 方法。  
  
 如需 <xref:System.Xml.Xsl.XslTransform.Load%2A> 方法及其使用 <xref:System.Xml.XmlResolver> 的詳細資訊，請參閱 <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>。  
  
 呼叫 <xref:System.Xml.Xsl.XslTransform.Transform%2A> 方法時，即會針對載入期間所提供的辨識項計算使用權限，接著將該使用權限集合指派給整個轉換程序。 若 `document()` 函式試圖啟始的動作所需要之使用權限，在使用權限集合中找不到，則會擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱

- [使用 XslTransform 類別進行 XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [XslTransform 類別實作 XSLT 處理器](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
- [XslTransform 的輸出](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)  
- [在不同存放區上的 XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)  
- [樣式表參數和擴充物件的 XsltArgumentList](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)  
- [使用 \<msxsl:script> 的 XSLT 樣式表指令碼](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)  
- [msxsl:node-set() 函式的支援](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)  
- [轉換中的 XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
- [轉換中的 XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
- [XslTransform 的 XPathDocument 輸入](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
- [XslTransform 的 XmlDataDocument 輸入](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
- [XslTransform 的 XmlDocument 輸入](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
