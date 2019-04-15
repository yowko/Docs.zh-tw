---
title: XSLT 擴充物件
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b10ab992089e2e9280162c4cd2273bc1d9dc35e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320414"
---
# <a name="xslt-extension-objects"></a>XSLT 擴充物件
擴充物件可用來擴充樣式表的功能。 <xref:System.Xml.Xsl.XsltArgumentList> 類別會維護擴充物件。  
  
 以下是使用擴充物件而不使用內嵌指令碼的優點：  
  
-   提供較佳的類別封裝和重複使用。  
  
-   允許樣式表更簡潔且更易於維護。  
  
 使用 <xref:System.Xml.Xsl.XsltArgumentList> 方法，將 XSLT 擴充物件加入至 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 物件。 限定名稱和命名空間 URI 於當時與擴充物件產生關聯。  
  
> [!NOTE]
>  呼叫 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 方法，需要 FullTrust 使用權限集合。 如需詳細資訊，請參閱[程式碼存取安全性](../../../../docs/framework/misc/code-access-security.md)和[具名使用權限集合](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100))。  
  
 從擴充物件傳回的資料型別，是 `number`、`string`、`Boolean` 及 `node set` 這四種基本 XPath 資料型別之一。  
  
 `params` 類別目前不支援任何允許傳遞未指定的參數數目，並以 <xref:System.Xml.Xsl.XslCompiledTransform> 關鍵字定義的方法。 使用以 `params` 關鍵字定義之任何方法的 XSLT 樣式表將無法正常運作。 如需詳細資訊，請查看 [params](~/docs/csharp/language-reference/keywords/params.md)。  
  
### <a name="to-use-an-xslt-extension-object"></a>使用 XSLT 擴充物件  
  
1. 使用 <xref:System.Xml.Xsl.XsltArgumentList> 方法，建立 <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> 物件並加入擴充物件。  
  
2. 從樣式表呼叫擴充物件。  
  
3. 將 <xref:System.Xml.Xsl.XsltArgumentList> 物件傳遞至 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 方法。  
  
## <a name="see-also"></a>另請參閱

- [XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations.md)
- [XSLT 安全性考量](../../../../docs/standard/data/xml/xslt-security-considerations.md)
