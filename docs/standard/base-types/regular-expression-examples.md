---
title: "規則運算式範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- regular expressions [.NET Framework], examples
- regular expressions [.NET Framework]
- strings [.NET Framework], regular expressions
ms.assetid: e9fd53f2-ed56-4b09-b2ea-e9bc9d65e6d6
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d7fa8fe2bade9f20f71f846c717d79d6b6ffb36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-examples"></a>規則運算式範例
本節包含程式碼範例，說明規則運算式在常見應用程式中的使用方式。  
  
> [!NOTE]
>  <xref:System.Web.RegularExpressions>命名空間包含一些實作預先定義的規則運算式模式剖析字串，從 HTML、 XML 和 ASP.NET 的文件的規則運算式物件。 例如，<xref:System.Web.RegularExpressions.TagRegex>類別會識別字串中的開始標記和<xref:System.Web.RegularExpressions.CommentRegex>類別會識別字串中的 ASP.NET 註解。  
  
## <a name="in-this-section"></a>本章節內容  
 [範例：掃描 HREF](../../../docs/standard/base-types/regular-expression-example-scanning-for-hrefs.md)  
 提供的範例會搜尋輸入的字串並列印出所有 href ="…"。  
  
 [範例：變更日期格式](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)  
 提供的範例會取代以表單為 dd-mm-yy 的日期格式為 mm/dd/yy 的日期。  
  
 [操作說明：從 URL 擷取通訊協定和連接埠號碼](../../../docs/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url.md)  
 提供的範例會從字串，其中包含 URL 擷取通訊協定和連接埠號碼。 例如，"http://www.contoso.com:8080/letters/readme.html" 會傳回 "http:8080"。  
  
 [操作說明：從字串中刪除無效的字元](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)  
 提供無效的非英數字元，從字串的範例。  
  
 [操作說明：確認字串是否為有效的電子郵件格式](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)  
 提供可用來確認字串為有效的電子郵件格式的範例。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Text.RegularExpressions>  
 提供類別程式庫參考資訊適用於.NET **System.Text.RegularExpressions**命名空間。  
  
## <a name="related-sections"></a>相關章節  
 [.NET 規則運算式](../../../docs/standard/base-types/regular-expressions.md)  
 提供規則運算式的程式設計語言方面的概觀。  
  
 [規則運算式物件模型](../../../docs/standard/base-types/the-regular-expression-object-model.md)  
 描述中包含的規則運算式類別`System.Text.RegularExpression`命名空間，並提供其用法範例。  
  
 [規則運算式行為的詳細資訊](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)  
 提供的功能和.NET 規則運算式行為的相關資訊。  
  
 [規則運算式語言 - 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 提供您可以用來定義規則運算式之字元、運算子和建構組合的資訊。
