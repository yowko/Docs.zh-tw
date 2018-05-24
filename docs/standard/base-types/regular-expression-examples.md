---
title: 規則運算式範例
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- regular expressions [.NET Framework], examples
- regular expressions [.NET Framework]
- strings [.NET Framework], regular expressions
ms.assetid: e9fd53f2-ed56-4b09-b2ea-e9bc9d65e6d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee4d884a0efbeb6e57ed727396bf3bcb39979774
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
---
# <a name="regular-expression-examples"></a>規則運算式範例
本節包含程式碼範例，說明規則運算式在常見應用程式中的使用方式。  
  
> [!NOTE]
>  <xref:System.Web.RegularExpressions> 命名空間包含一些規則運算式物件，這些物件會實作預先定義的規則運算式模式，以用於剖析來自 HTML、XML 和 ASP.NET 文件的字串。 例如，<xref:System.Web.RegularExpressions.TagRegex> 類別會識別字串中的開始標記，而 <xref:System.Web.RegularExpressions.CommentRegex> 類別會識別字串中的 ASP.NET 註解。  
  
## <a name="in-this-section"></a>本節內容  
 [範例：掃描 HREF](../../../docs/standard/base-types/regular-expression-example-scanning-for-hrefs.md)  
 提供搜尋輸入字串的範例，並印出所有 href="..." 值及其在字串中的位置。  
  
 [範例：變更日期格式](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)  
 提供以 dd-mm-yy 日期格式取代 mm/dd/yy 日期格式的範例。  
  
 [操作說明：從 URL 擷取通訊協定和連接埠號碼](../../../docs/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url.md)  
 提供從包含 URL 的字串中擷取通訊協定與連接埠號碼的範例。 例如，"http://www.contoso.com:8080/letters/readme.html" 會傳回 "http:8080"。  
  
 [操作說明：從字串中刪除無效的字元](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)  
 提供從字串中刪除無效非英數字元的範例。  
  
 [操作說明：確認字串是否為有效的電子郵件格式](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)  
 提供驗證字串為有效的電子郵件格式的範例。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Text.RegularExpressions>  
 提供適用於 .NET **System.Text.RegularExpressions** 命名空間的類別庫參考資訊。  
  
## <a name="related-sections"></a>相關章節  
 [.NET 規則運算式](../../../docs/standard/base-types/regular-expressions.md)  
 提供規則運算式的程式設計語言方面的概觀。  
  
 [規則運算式物件模型](../../../docs/standard/base-types/the-regular-expression-object-model.md)  
 說明包含在 `System.Text.RegularExpression` 命名空間的規則運算式類別，並提供其使用範例。  
  
 [規則運算式行為的詳細資訊](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)  
 提供 .NET 規則運算式之功能和行為的相關資訊。  
  
 [規則運算式語言 - 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 提供您可以用來定義規則運算式之字元、運算子和建構組合的資訊。
