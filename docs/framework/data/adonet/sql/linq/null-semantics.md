---
title: Null 語意
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
caps.latest.revision: 2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 3c4daa5fd37158f1af31f33ba743a56cf76670d8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="null-semantics"></a><span data-ttu-id="6a19b-102">Null 語意</span><span class="sxs-lookup"><span data-stu-id="6a19b-102">Null Semantics</span></span>
<span data-ttu-id="6a19b-103">下表提供各個組件的連結[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]文件位置`null`(`Nothing`在 Visual Basic 中) 問題的討論。</span><span class="sxs-lookup"><span data-stu-id="6a19b-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in Visual Basic) issues are discussed.</span></span>  
  
|<span data-ttu-id="6a19b-104">主題</span><span class="sxs-lookup"><span data-stu-id="6a19b-104">Topic</span></span>|<span data-ttu-id="6a19b-105">描述</span><span class="sxs-lookup"><span data-stu-id="6a19b-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="6a19b-106">SQL-CLR 類型不符</span><span class="sxs-lookup"><span data-stu-id="6a19b-106">SQL-CLR Type Mismatches</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|<span data-ttu-id="6a19b-107">此主題的 「 Null 語意 」 一節包含三種狀態 SQL 布林值對兩種狀態 common language runtime (CLR) 的討論<xref:System.Boolean>，常值`Nothing`(Visual Basic) 和`null`(C# 中)，以及其他類似問題。</span><span class="sxs-lookup"><span data-stu-id="6a19b-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` (Visual Basic) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="6a19b-108">標準查詢運算子轉譯</span><span class="sxs-lookup"><span data-stu-id="6a19b-108">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|<span data-ttu-id="6a19b-109">本主題的「Null 語意」一節描述 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]中的 null 比較語意。</span><span class="sxs-lookup"><span data-stu-id="6a19b-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="6a19b-110">System.String 方法</span><span class="sxs-lookup"><span data-stu-id="6a19b-110">System.String Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|<span data-ttu-id="6a19b-111">本主題的「與 .NET 的差異」一節描述 <xref:System.String.LastIndexOf%2A> 傳回 0 即表示字串為 null 或找到的位置為 0 的原因。</span><span class="sxs-lookup"><span data-stu-id="6a19b-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="6a19b-112">計算數值序列中各值的總和</span><span class="sxs-lookup"><span data-stu-id="6a19b-112">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="6a19b-113">描述如何<xref:System.Linq.Enumerable.Sum%2A>運算子評估為`null`(`Nothing`在 Visual Basic 中) 而不是 0，只包含 null 的序列或空的序列。</span><span class="sxs-lookup"><span data-stu-id="6a19b-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in Visual Basic) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a19b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a19b-114">See Also</span></span>  
 [<span data-ttu-id="6a19b-115">資料類型和函式</span><span class="sxs-lookup"><span data-stu-id="6a19b-115">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
