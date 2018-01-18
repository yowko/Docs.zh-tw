---
title: "Null 語意"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8d32f73c8c2095c23ec164ad40fd1ab27ef1153a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="null-semantics"></a><span data-ttu-id="4580d-102">Null 語意</span><span class="sxs-lookup"><span data-stu-id="4580d-102">Null Semantics</span></span>
<span data-ttu-id="4580d-103">下表提供了 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 文件的各部分連結，其中包含 `null` (在`Nothing` 中為 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) 問題的討論。</span><span class="sxs-lookup"><span data-stu-id="4580d-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) issues are discussed.</span></span>  
  
|<span data-ttu-id="4580d-104">主題</span><span class="sxs-lookup"><span data-stu-id="4580d-104">Topic</span></span>|<span data-ttu-id="4580d-105">描述</span><span class="sxs-lookup"><span data-stu-id="4580d-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4580d-106">SQL-CLR 類型不符</span><span class="sxs-lookup"><span data-stu-id="4580d-106">SQL-CLR Type Mismatches</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|<span data-ttu-id="4580d-107">本主題的「Null 語意」一節包含三種狀態 SQL 布林值對兩種狀態 Common Language Runtime (CLR) <xref:System.Boolean>、常值 `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) 與 `null` (C#)，以及其他類似問題的討論。</span><span class="sxs-lookup"><span data-stu-id="4580d-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="4580d-108">標準查詢運算子轉譯</span><span class="sxs-lookup"><span data-stu-id="4580d-108">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|<span data-ttu-id="4580d-109">本主題的「Null 語意」一節描述 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]中的 null 比較語意。</span><span class="sxs-lookup"><span data-stu-id="4580d-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="4580d-110">System.String 方法</span><span class="sxs-lookup"><span data-stu-id="4580d-110">System.String Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|<span data-ttu-id="4580d-111">本主題的「與 .NET 的差異」一節描述 <xref:System.String.LastIndexOf%2A> 傳回 0 即表示字串為 null 或找到的位置為 0 的原因。</span><span class="sxs-lookup"><span data-stu-id="4580d-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="4580d-112">計算數值序列中各值的總和</span><span class="sxs-lookup"><span data-stu-id="4580d-112">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="4580d-113">描述 <xref:System.Linq.Enumerable.Sum%2A> 運算子在只包含 null 的序列或空序列中，評估為 `null` (在`Nothing` 中為 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) 而非 0 的原因。</span><span class="sxs-lookup"><span data-stu-id="4580d-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4580d-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="4580d-114">See Also</span></span>  
 [<span data-ttu-id="4580d-115">資料類型和函式</span><span class="sxs-lookup"><span data-stu-id="4580d-115">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
