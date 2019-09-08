---
title: Null 語意
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: d0b18c0a699840d11f5e4add05147672f9bb69e9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792975"
---
# <a name="null-semantics"></a><span data-ttu-id="c13da-102">Null 語意</span><span class="sxs-lookup"><span data-stu-id="c13da-102">Null Semantics</span></span>
<span data-ttu-id="c13da-103">下表提供[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]檔的各部分連結，其中`null`會討論（`Nothing`在 Visual Basic）問題。</span><span class="sxs-lookup"><span data-stu-id="c13da-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="c13da-104">主題</span><span class="sxs-lookup"><span data-stu-id="c13da-104">Topic</span></span>|<span data-ttu-id="c13da-105">描述</span><span class="sxs-lookup"><span data-stu-id="c13da-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c13da-106">SQL-CLR 類型不符</span><span class="sxs-lookup"><span data-stu-id="c13da-106">SQL-CLR Type Mismatches</span></span>](sql-clr-type-mismatches.md)|<span data-ttu-id="c13da-107">本主題的「Null 語義」一節包含三個狀態的 SQL 布林值與雙狀態 common language runtime <xref:System.Boolean>（CLR）、常`Nothing`值（Visual Basic）和`null` （C#）以及其他類似的討論發出.</span><span class="sxs-lookup"><span data-stu-id="c13da-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="c13da-108">標準查詢運算子轉譯</span><span class="sxs-lookup"><span data-stu-id="c13da-108">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)|<span data-ttu-id="c13da-109">本主題的「Null 語意」一節描述 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]中的 null 比較語意。</span><span class="sxs-lookup"><span data-stu-id="c13da-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="c13da-110">System.String 方法</span><span class="sxs-lookup"><span data-stu-id="c13da-110">System.String Methods</span></span>](system-string-methods.md)|<span data-ttu-id="c13da-111">本主題的「與 .NET 的差異」一節描述 <xref:System.String.LastIndexOf%2A> 傳回 0 即表示字串為 null 或找到的位置為 0 的原因。</span><span class="sxs-lookup"><span data-stu-id="c13da-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="c13da-112">計算數值序列中各值的總和</span><span class="sxs-lookup"><span data-stu-id="c13da-112">Compute the Sum of Values in a Numeric Sequence</span></span>](compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="c13da-113">描述<xref:System.Linq.Enumerable.Sum%2A>運算子如何針對只包含 null`Nothing`的序列或空的序列，評估為（在 Visual Basic 中）， `null`而不是0。</span><span class="sxs-lookup"><span data-stu-id="c13da-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c13da-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c13da-114">See also</span></span>

- [<span data-ttu-id="c13da-115">資料類型和函式</span><span class="sxs-lookup"><span data-stu-id="c13da-115">Data Types and Functions</span></span>](data-types-and-functions.md)
