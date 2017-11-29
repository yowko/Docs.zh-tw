---
title: "System.String 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce307f14-87e6-4816-8694-8a4147f6b784
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3cfddba1bfa7bf7cefba917be0026b1c366f3513
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="systemstring-methods"></a><span data-ttu-id="cd92d-102">System.String 方法</span><span class="sxs-lookup"><span data-stu-id="cd92d-102">System.String Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="cd92d-103"> 不支援下列 <xref:System.String> 方法。</span><span class="sxs-lookup"><span data-stu-id="cd92d-103"> does not support the following <xref:System.String> methods.</span></span>  
  
## <a name="unsupported-systemstring-methods-in-general"></a><span data-ttu-id="cd92d-104">一般不支援的 System.String 方法</span><span class="sxs-lookup"><span data-stu-id="cd92d-104">Unsupported System.String Methods in General</span></span>  
 <span data-ttu-id="cd92d-105">一般不支援的 <xref:System.String> 方法：</span><span class="sxs-lookup"><span data-stu-id="cd92d-105">Unsupported <xref:System.String> methods in general:</span></span>  
  
-   <span data-ttu-id="cd92d-106">文化特性感知的多載 (這些方法會採用`CultureInfo`  /  `StringComparison`  /  `IFormatProvider`)。</span><span class="sxs-lookup"><span data-stu-id="cd92d-106">Culture-aware overloads (methods that take a `CultureInfo` / `StringComparison` / `IFormatProvider`).</span></span>  
  
-   <span data-ttu-id="cd92d-107">取用或產生 `char` 陣列的方法。</span><span class="sxs-lookup"><span data-stu-id="cd92d-107">Methods that take or produce a `char` array.</span></span>  
  
## <a name="unsupported-systemstring-static-methods"></a><span data-ttu-id="cd92d-108">不支援的 System.String 靜態方法</span><span class="sxs-lookup"><span data-stu-id="cd92d-108">Unsupported System.String Static Methods</span></span>  
  
|<span data-ttu-id="cd92d-109">不支援的 System.String 靜態方法</span><span class="sxs-lookup"><span data-stu-id="cd92d-109">Unsupported System.String Static Methods</span></span>|  
|----------------------------------------------|  
|<xref:System.String.Copy%28System.String%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%29?displayProperty=nameWithType>|  
|<xref:System.String.Compare%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.String%29?displayProperty=nameWithType>|  
|<xref:System.String.CompareOrdinal%28System.String%2CSystem.Int32%2CSystem.String%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|  
  
## <a name="unsupported-systemstring-non-static-methods"></a><span data-ttu-id="cd92d-110">不支援的 System.String 非靜態方法</span><span class="sxs-lookup"><span data-stu-id="cd92d-110">Unsupported System.String Non-static Methods</span></span>  
  
|<span data-ttu-id="cd92d-111">不支援的 System.String 非靜態方法</span><span class="sxs-lookup"><span data-stu-id="cd92d-111">Unsupported System.String Non-static Methods</span></span>|  
|---------------------------------------------------|  
|<xref:System.String.IndexOfAny%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.Split%2A?displayProperty=nameWithType>|  
|<xref:System.String.ToCharArray?displayProperty=nameWithType>|  
|<xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimEnd%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
|<xref:System.String.TrimStart%28System.Char%5B%5D%29?displayProperty=nameWithType>|  
  
## <a name="differences-from-net"></a><span data-ttu-id="cd92d-112">與 .NET 的差異</span><span class="sxs-lookup"><span data-stu-id="cd92d-112">Differences from .NET</span></span>  
  
-   <span data-ttu-id="cd92d-113">查詢不會考慮伺服器上可能作用中的 SQL Server 定序 (Collation)，因此預設會提供區分文化特性、但不區分大小寫的比較。</span><span class="sxs-lookup"><span data-stu-id="cd92d-113">Queries do not account for SQL Server collations that might be in effect on the server, and therefore will provide culture-sensitive, case-insensitive comparisons by default.</span></span> <span data-ttu-id="cd92d-114">這個行為與 .NET Framework 的預設區分大小寫語意 (Semantics) 不同。</span><span class="sxs-lookup"><span data-stu-id="cd92d-114">This behavior differs from the default, case-sensitive semantics of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="cd92d-115">當`LastIndexOf`是，則傳回 0，在字串`NULL`或找到的位置為 0。</span><span class="sxs-lookup"><span data-stu-id="cd92d-115">When `LastIndexOf` returns 0, either the string is `NULL` or the found position is 0.</span></span>  
  
-   <span data-ttu-id="cd92d-116">固定長度字串 (`CHAR`、`NCHAR`) 上的串連或其他作業可能會傳回未預期的結果，原因是這些型別已自動將填補套用至資料庫中。</span><span class="sxs-lookup"><span data-stu-id="cd92d-116">Unexpected results might be returned from concatenation or other operations on fixed-length strings (`CHAR`, `NCHAR`), because these types automatically have padding applied in the database.</span></span>  
  
-   <span data-ttu-id="cd92d-117">因為許多方法 (如 `Replace`、`ToLower`、`ToUpper` 和字元索引子 (Indexer)) 都沒有 `TEXT` 或 `NTEXT` 資料行和 XML 的有效轉譯，所以如果正常轉譯，則會發生 `SqlExceptions`。</span><span class="sxs-lookup"><span data-stu-id="cd92d-117">Because many methods, such as `Replace`, `ToLower`, `ToUpper`, and the character indexer, have no valid translation for `TEXT` or `NTEXT` columns and XML, `SqlExceptions` occur if translated normally.</span></span> <span data-ttu-id="cd92d-118">對這些型別而言，這個行為是可接受的行為。</span><span class="sxs-lookup"><span data-stu-id="cd92d-118">This behavior is considered acceptable for these types.</span></span> <span data-ttu-id="cd92d-119">不過，所有字串作業都必須符合 `VARCHAR`、`NVARCHAR`、`VARCHAR(max)` 和 `NVARCHAR(max)` 的 Common Language Runtime (CLR) 語意。</span><span class="sxs-lookup"><span data-stu-id="cd92d-119">However, all string operations must match common language runtime (CLR) semantics for `VARCHAR`, `NVARCHAR`, `VARCHAR(max)`, and `NVARCHAR(max)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd92d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd92d-120">See Also</span></span>  
 [<span data-ttu-id="cd92d-121">資料型別和函式</span><span class="sxs-lookup"><span data-stu-id="cd92d-121">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
