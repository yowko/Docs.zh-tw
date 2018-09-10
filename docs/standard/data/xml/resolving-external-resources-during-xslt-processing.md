---
title: XSLT 處理期間解析外部資源
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 958699b8e3a00cfe3f8fd8ac4bb96914dcd0598c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44185122"
---
# <a name="resolving-external-resources-during-xslt-processing"></a>XSLT 處理期間解析外部資源
在 XSLT 轉換期間，您可能需要進行數次外部資源解析。  
  
## <a name="using-the-xmlresolver-class"></a>使用 XmlResolver 類別  
 <xref:System.Xml.XmlResolver> 類別可用於解析外部資源。 下表說明在 XSLT 處理期間何時會使用 <xref:System.Xml.XmlResolver>。  
  
|XSLT 工作|XmlResolver 的用途|  
|---------------|--------------------------------------|  
|編譯樣式表。|解析樣式表的 URI。<br /><br /> -和-<br /><br /> 在任意 `xsl:import` 或 `xsl:include` 項目中解析 URI 參考。|  
|執行樣式表。|解析內容文件的 URI。<br /><br /> -和-<br /><br /> 在任意 XSLT `document()` 函式中解析 URI 參考。|  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 及 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法包括將 <xref:System.Xml.XmlResolver> 物件做為其中一個引數的多載。 如果未指定 <xref:System.Xml.XmlResolver>，則會使用沒有任何認證的預設 <xref:System.Xml.XmlUrlResolver>。  
  
 下列清單說明何時您可能想要指定 <xref:System.Xml.XmlResolver> 物件：  
  
-   如果 XSLT 處理序需要存取需要驗證的網路資源，可使用具有必要認證的 <xref:System.Xml.XmlResolver>。  
  
-   如果要限制 XSLT 處理序可存取的資源，您可使用具有正確使用權限集合的 <xref:System.Xml.XmlSecureResolver>。 如果您需要開啟不是由您控制或不受信任的資源，請使用 <xref:System.Xml.XmlSecureResolver> 類別。  
  
-   如果要自訂行為，可實作自己的 <xref:System.Xml.XmlResolver> 類別，然後使用它來解析資源。  
  
-   如果要確保不存取任何外部資源，您可對 `null` 引數指定 <xref:System.Xml.XmlResolver>。  
  
## <a name="example"></a>範例  
 下列範例編譯了儲存在網路資源上的樣式表。 <xref:System.Xml.XmlUrlResolver> 物件指定存取樣式表所需的認證。  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Xsl.XslCompiledTransform>  
- <xref:System.Xml.Xsl.XsltSettings>  
- [XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations.md)
