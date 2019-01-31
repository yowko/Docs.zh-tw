---
title: 使用 XslCompiledTransform 類別
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce9a06c14141bb658eb665e643d8da27e18dd94f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590363"
---
# <a name="using-the-xslcompiledtransform-class"></a>使用 XslCompiledTransform 類別
<xref:System.Xml.Xsl.XslCompiledTransform> 類別為 Microsoft .NET Framework XSLT 處理器。 此類別用於編譯樣式表，並執行 XSLT 轉換。  
  
> [!NOTE]
>  雖然 <xref:System.Xml.Xsl.XslCompiledTransform> 類別的整體效能優於 <xref:System.Xml.Xsl.XslTransform> 類別，但是在轉換時第一次呼叫 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 類別的 <xref:System.Xml.Xsl.XslCompiledTransform> 方法之執行速度可能會比 <xref:System.Xml.Xsl.XslTransform.Load%2A> 類別的 <xref:System.Xml.Xsl.XslTransform> 方法慢許多。 這是因為在載入之前必須先編譯 XSLT 檔案。 如需詳細資訊，請參閱下列部落格文章：[XslCompiledTransform Slower than XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/) (XslCompiledTransform 比 XslTransform 還慢嗎？)  
  
## <a name="in-this-section"></a>本節內容  
 [XslCompiledTransform 類別的輸入](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 說明可用的 XSLT 輸入選項。  
  
 [XslCompiledTransform 類別的輸出選項](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 說明可用的 XSLT 輸出選項。  
  
 [XSLT 處理期間解析外部資源](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 討論如何使用 <xref:System.Xml.XmlResolver> 類別解析外部資源。  
  
 [延伸 XSLT 樣式表](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 討論如何支援 XSLT 擴充。  
  
|||  
|-|-|  
|[可復原的 XSLT 錯誤](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|列出全球資訊網協會 (W3C) XSLT 1.0 版建議事項所允許的判別行為，以及說明 <xref:System.Xml.Xsl.XslCompiledTransform> 類別如何處理這些行為。|  
|[如何：轉換節點片段](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|描述如何轉換節點片段。|  
  
## <a name="related-sections"></a>相關章節  
 [從 XslTransform 類別移轉](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 討論如何從 <xref:System.Xml.Xsl.XslTransform> 類別移轉程式碼  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
