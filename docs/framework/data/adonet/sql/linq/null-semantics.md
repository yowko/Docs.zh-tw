---
title: Null 語意
ms.date: 03/30/2017
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
ms.openlocfilehash: eb1e96ba44c5d64e8366a654c2d06d89c9b46c9a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172753"
---
# <a name="null-semantics"></a><span data-ttu-id="18d79-102">Null 語意</span><span class="sxs-lookup"><span data-stu-id="18d79-102">Null Semantics</span></span>
<span data-ttu-id="18d79-103">下表提供的各部分的連結[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]文件所在`null`(`Nothing` Visual Basic 中) 問題的討論。</span><span class="sxs-lookup"><span data-stu-id="18d79-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="18d79-104">主題</span><span class="sxs-lookup"><span data-stu-id="18d79-104">Topic</span></span>|<span data-ttu-id="18d79-105">描述</span><span class="sxs-lookup"><span data-stu-id="18d79-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="18d79-106">SQL-CLR 類型不符</span><span class="sxs-lookup"><span data-stu-id="18d79-106">SQL-CLR Type Mismatches</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|<span data-ttu-id="18d79-107">此主題的 「 Null 語意 」 一節包含的三種狀態 SQL 布林值對兩個狀態 common language runtime (CLR) 的討論<xref:System.Boolean>，常`Nothing`(Visual Basic) 和`null`(C#)，及其他類似問題。</span><span class="sxs-lookup"><span data-stu-id="18d79-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="18d79-108">標準查詢運算子轉譯</span><span class="sxs-lookup"><span data-stu-id="18d79-108">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|<span data-ttu-id="18d79-109">本主題的「Null 語意」一節描述 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]中的 null 比較語意。</span><span class="sxs-lookup"><span data-stu-id="18d79-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="18d79-110">System.String 方法</span><span class="sxs-lookup"><span data-stu-id="18d79-110">System.String Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|<span data-ttu-id="18d79-111">本主題的「與 .NET 的差異」一節描述 <xref:System.String.LastIndexOf%2A> 傳回 0 即表示字串為 null 或找到的位置為 0 的原因。</span><span class="sxs-lookup"><span data-stu-id="18d79-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="18d79-112">計算數值序列中各值的總和</span><span class="sxs-lookup"><span data-stu-id="18d79-112">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="18d79-113">描述如何<xref:System.Linq.Enumerable.Sum%2A>運算子會評估為`null`(`Nothing` Visual Basic 中) 而不是 0，只包含 null 的序列或空的序列。</span><span class="sxs-lookup"><span data-stu-id="18d79-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18d79-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18d79-114">See also</span></span>

- [<span data-ttu-id="18d79-115">資料類型和函式</span><span class="sxs-lookup"><span data-stu-id="18d79-115">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
