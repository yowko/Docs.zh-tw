---
title: Null 語意
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: 739ee95be45d7d64a4ad1678837b9706a533f07d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147537"
---
# <a name="null-semantics"></a><span data-ttu-id="4a4e3-102">Null 語意</span><span class="sxs-lookup"><span data-stu-id="4a4e3-102">Null Semantics</span></span>

<span data-ttu-id="4a4e3-103">下表提供檔的各部分連結， [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 其中 `null` `Nothing` 討論 Visual Basic) 問題的 (。</span><span class="sxs-lookup"><span data-stu-id="4a4e3-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="4a4e3-104">主題</span><span class="sxs-lookup"><span data-stu-id="4a4e3-104">Topic</span></span>|<span data-ttu-id="4a4e3-105">描述</span><span class="sxs-lookup"><span data-stu-id="4a4e3-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4a4e3-106">SQL-CLR 類型不符</span><span class="sxs-lookup"><span data-stu-id="4a4e3-106">SQL-CLR Type Mismatches</span></span>](sql-clr-type-mismatches.md)|<span data-ttu-id="4a4e3-107">本主題的「Null 語義」一節包含三種狀態 SQL 布林值與雙狀態 common language runtime (CLR) 的討論 <xref:System.Boolean> 、常值 `Nothing` (Visual Basic) 和 `null` (c # ) ，以及其他類似的問題。</span><span class="sxs-lookup"><span data-stu-id="4a4e3-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="4a4e3-108">標準查詢運算子轉譯</span><span class="sxs-lookup"><span data-stu-id="4a4e3-108">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)|<span data-ttu-id="4a4e3-109">本主題的「Null 語意」一節描述 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]中的 null 比較語意。</span><span class="sxs-lookup"><span data-stu-id="4a4e3-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="4a4e3-110">System.String 方法</span><span class="sxs-lookup"><span data-stu-id="4a4e3-110">System.String Methods</span></span>](system-string-methods.md)|<span data-ttu-id="4a4e3-111">本主題的「與 .NET 的差異」一節描述 <xref:System.String.LastIndexOf%2A> 傳回 0 即表示字串為 null 或找到的位置為 0 的原因。</span><span class="sxs-lookup"><span data-stu-id="4a4e3-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="4a4e3-112">如何：計算數值序列中各值的總和</span><span class="sxs-lookup"><span data-stu-id="4a4e3-112">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="4a4e3-113">描述運算子如何 <xref:System.Linq.Enumerable.Sum%2A> `null` `Nothing` 針對只包含 null 的序列或空的序列，評估為 (in Visual Basic) 而不是0。</span><span class="sxs-lookup"><span data-stu-id="4a4e3-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a4e3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a4e3-114">See also</span></span>

- [<span data-ttu-id="4a4e3-115">資料類型與函式</span><span class="sxs-lookup"><span data-stu-id="4a4e3-115">Data Types and Functions</span></span>](data-types-and-functions.md)
