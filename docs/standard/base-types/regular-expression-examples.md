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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4d2d3aced78d2afed3f0d1396efe5e954ef84102
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="regular-expression-examples"></a><span data-ttu-id="f2906-102">規則運算式範例</span><span class="sxs-lookup"><span data-stu-id="f2906-102">Regular Expression Examples</span></span>
<span data-ttu-id="f2906-103">本節包含程式碼範例，說明規則運算式在常見應用程式中的使用方式。</span><span class="sxs-lookup"><span data-stu-id="f2906-103">This section contains code examples that illustrate the use of regular expressions in common applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2906-104"><xref:System.Web.RegularExpressions> 命名空間包含一些規則運算式物件，這些物件會實作預先定義的規則運算式模式，以用於剖析來自 HTML、XML 和 ASP.NET 文件的字串。</span><span class="sxs-lookup"><span data-stu-id="f2906-104">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="f2906-105">例如，<xref:System.Web.RegularExpressions.TagRegex> 類別會識別字串中的開始標記，而 <xref:System.Web.RegularExpressions.CommentRegex> 類別會識別字串中的 ASP.NET 註解。</span><span class="sxs-lookup"><span data-stu-id="f2906-105">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f2906-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="f2906-106">In This Section</span></span>  
 [<span data-ttu-id="f2906-107">範例：掃描 HREF</span><span class="sxs-lookup"><span data-stu-id="f2906-107">Example: Scanning for HREFs</span></span>](../../../docs/standard/base-types/regular-expression-example-scanning-for-hrefs.md)  
 <span data-ttu-id="f2906-108">提供搜尋輸入字串的範例，並印出所有 href="..." 值及其在字串中的位置。</span><span class="sxs-lookup"><span data-stu-id="f2906-108">Provides an example that searches an input string and prints out all the href="…" values and their locations in the string.</span></span>  
  
 [<span data-ttu-id="f2906-109">範例：變更日期格式</span><span class="sxs-lookup"><span data-stu-id="f2906-109">Example: Changing Date Formats</span></span>](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)  
 <span data-ttu-id="f2906-110">提供以 dd-mm-yy 日期格式取代 mm/dd/yy 日期格式的範例。</span><span class="sxs-lookup"><span data-stu-id="f2906-110">Provides an example that replaces dates in the form mm/dd/yy with dates in the form dd-mm-yy.</span></span>  
  
 [<span data-ttu-id="f2906-111">操作說明：從 URL 擷取通訊協定和連接埠號碼</span><span class="sxs-lookup"><span data-stu-id="f2906-111">How to: Extract a Protocol and Port Number from a URL</span></span>](../../../docs/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url.md)  
 <span data-ttu-id="f2906-112">提供從包含 URL 的字串中擷取通訊協定與連接埠號碼的範例。</span><span class="sxs-lookup"><span data-stu-id="f2906-112">Provides an example that extracts a protocol and port number from a string that contains a URL.</span></span> <span data-ttu-id="f2906-113">例如，"http://www.contoso.com:8080/letters/readme.html" 會傳回 "http:8080"。</span><span class="sxs-lookup"><span data-stu-id="f2906-113">For example, "http://www.contoso.com:8080/letters/readme.html" returns "http:8080".</span></span>  
  
 [<span data-ttu-id="f2906-114">操作說明：從字串中刪除無效的字元</span><span class="sxs-lookup"><span data-stu-id="f2906-114">How to: Strip Invalid Characters from a String</span></span>](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)  
 <span data-ttu-id="f2906-115">提供從字串中刪除無效非英數字元的範例。</span><span class="sxs-lookup"><span data-stu-id="f2906-115">Provides an example that strips invalid non-alphanumeric characters from a string.</span></span>  
  
 [<span data-ttu-id="f2906-116">操作說明：確認字串是否為有效的電子郵件格式</span><span class="sxs-lookup"><span data-stu-id="f2906-116">How to: Verify that Strings Are in Valid Email Format</span></span>](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)  
 <span data-ttu-id="f2906-117">提供可用來驗證字串是否為有效電子郵件格式的範例。</span><span class="sxs-lookup"><span data-stu-id="f2906-117">Provides an example that you can use to verify that a string is in valid email format.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f2906-118">參考資料</span><span class="sxs-lookup"><span data-stu-id="f2906-118">Reference</span></span>  
 <xref:System.Text.RegularExpressions>  
 <span data-ttu-id="f2906-119">提供適用於 .NET **System.Text.RegularExpressions** 命名空間的類別庫參考資訊。</span><span class="sxs-lookup"><span data-stu-id="f2906-119">Provides class library reference information for the .NET **System.Text.RegularExpressions** namespace.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f2906-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="f2906-120">Related Sections</span></span>  
 [<span data-ttu-id="f2906-121">.NET 規則運算式</span><span class="sxs-lookup"><span data-stu-id="f2906-121">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="f2906-122">提供規則運算式的程式設計語言方面的概觀。</span><span class="sxs-lookup"><span data-stu-id="f2906-122">Provides an overview of the programming language aspect of regular expressions.</span></span>  
  
 [<span data-ttu-id="f2906-123">規則運算式物件模型</span><span class="sxs-lookup"><span data-stu-id="f2906-123">The Regular Expression Object Model</span></span>](../../../docs/standard/base-types/the-regular-expression-object-model.md)  
 <span data-ttu-id="f2906-124">說明包含在 `System.Text.RegularExpression` 命名空間的規則運算式類別，並提供其使用範例。</span><span class="sxs-lookup"><span data-stu-id="f2906-124">Describes the regular expression classes contained in the `System.Text.RegularExpression` namespace and provides examples of their use.</span></span>  
  
 [<span data-ttu-id="f2906-125">規則運算式行為的詳細資訊</span><span class="sxs-lookup"><span data-stu-id="f2906-125">Details of Regular Expression Behavior</span></span>](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)  
 <span data-ttu-id="f2906-126">提供 .NET 規則運算式之功能和行為的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f2906-126">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>  
  
 [<span data-ttu-id="f2906-127">規則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="f2906-127">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 <span data-ttu-id="f2906-128">提供您可以用來定義規則運算式之字元、運算子和建構組合的資訊。</span><span class="sxs-lookup"><span data-stu-id="f2906-128">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
