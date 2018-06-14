---
title: XSLT 安全性考量
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: fea695be-617c-4977-9567-140e820436fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9c448e4cd4f40865a11a23af51e134da4b8ba2f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575410"
---
# <a name="xslt-security-considerations"></a>XSLT 安全性考量
XSLT 語言具有一組豐富的功能，可讓您擁有強大的能力與彈性。 它還包含許多可由外部來源利用的功能 (若有幫助)。 若要安全使用 XSLT，您必須瞭解使用 XSLT 時會出現的各種安全性問題，以及為了減緩這些危險可使用的基本策略。  
  
## <a name="xslt-extensions"></a>XSLT 擴充  
 兩個普遍使用的 XSLT 擴充為樣式表指令碼及擴充物件。 這些擴充允許 XSLT 處理器執行程式碼。  
  
-   擴充物件會將程式設計功能加入至 XSL 轉換。  
  
-   指令碼可透過 `msxsl:script` 擴充項目內嵌在樣式表中。  
  
### <a name="extension-objects"></a>擴充物件  
 擴充物件可透過 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 方法加入。 FullTrust 使用權限集合必須支援擴充物件。 這會確保在執行擴充物件程式碼時不會提高使用權限。 嘗試呼叫沒有 FullTrust 使用權限的 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 方法，會導致擲回安全性例外狀況。  
  
### <a name="style-sheet-scripts"></a>樣式表指令碼  
 指令碼可透過 `msxsl:script` 擴充項目內嵌在樣式表中。 指令碼支援是 <xref:System.Xml.Xsl.XslCompiledTransform> 類別上的選擇性功能 (預設為停用)。 可透過將 <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> 屬性設為 `true`，並將 <xref:System.Xml.Xsl.XsltSettings> 物件傳遞至 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 方法，即可啟用指令碼。  
  
#### <a name="guidelines"></a>方針  
 僅在樣式表來自受信任來源時啟用指令碼。 如果無法驗證樣式表的來源，或樣式表不是來自受信任來源，請傳入 `null` 做為 XSLT 設定引數。  
  
## <a name="external-resources"></a>外部資源  
 對於 XSLT 語言的某些功能 (如 `xsl:import`、`xsl:include` 或 `document()` 函式)，處理器需要解析 URI 參考。 <xref:System.Xml.XmlResolver> 類別可用於解析外部資源。 在下列兩種情況下，可能需要解析外部資源：  
  
-   編譯樣式表時，會使用 <xref:System.Xml.XmlResolver> 進行 `xsl:import` 及 `xsl:include` 解析。  
  
-   執行轉換時，會使用 <xref:System.Xml.XmlResolver> 解析 `document()` 函式。  
  
    > [!NOTE]
    >  `document()` 函式在 <xref:System.Xml.Xsl.XslCompiledTransform> 類別上預設為停用。 可透過將 <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> 屬性設為 `true`，並將 <xref:System.Xml.Xsl.XsltSettings> 物件傳遞至 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 方法，即可啟用此功能。  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 及 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法都包含多載，可接受 <xref:System.Xml.XmlResolver> 做為其中一個引數。 如果未指定 <xref:System.Xml.XmlResolver>，則會使用沒有任何認證的預設 <xref:System.Xml.XmlUrlResolver>。  
  
#### <a name="guidelines"></a>方針  
 僅在樣式表來自受信任來源時啟用 `document()` 函式。  
  
 下列清單說明何時您可能想要指定 <xref:System.Xml.XmlResolver> 物件：  
  
-   如果 XSLT 處理序需要存取需要驗證的網路資源，可使用具有必要認證的 <xref:System.Xml.XmlResolver>。  
  
-   如果要限制 XSLT 處理序可存取的資源，您可使用具有正確使用權限集合的 <xref:System.Xml.XmlSecureResolver>。 如果您需要開啟不是由您控制或不受信任的資源，請使用 <xref:System.Xml.XmlSecureResolver> 類別。  
  
-   如果要自訂行為，可實作自己的 <xref:System.Xml.XmlResolver> 類別，然後使用它來解析資源。  
  
-   如果要確保不存取任何外部資源，您可對 `null` 引數指定 <xref:System.Xml.XmlResolver>。  
  
## <a name="see-also"></a>請參閱  
 [XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [XSLT 處理期間解析外部資源](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 [程式碼存取安全性](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)
