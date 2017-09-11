---
title: "分割資料 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2f1690dac93d5e74f1305bd457f8bc749bec5449
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="partitioning-data-c"></a><span data-ttu-id="370ed-102">分割資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="370ed-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="370ed-103">LINQ 中的分割是指將輸入序列分成兩個區段的作業，不用重新排列項目，然後傳回其中一個區段。</span><span class="sxs-lookup"><span data-stu-id="370ed-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="370ed-104">下圖顯示字元序列三種不同分割作業的結果。</span><span class="sxs-lookup"><span data-stu-id="370ed-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="370ed-105">第一項作業會傳回序列中的前三個項目。</span><span class="sxs-lookup"><span data-stu-id="370ed-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="370ed-106">第二項作業會略過前三個項目，傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="370ed-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="370ed-107">第三個作業會略過序列中的前兩個項目，傳回接下來的三個元項目。</span><span class="sxs-lookup"><span data-stu-id="370ed-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="370ed-108">![LINQ 分割作業](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="370ed-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="370ed-109">分割序列的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="370ed-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="370ed-110">運算子</span><span class="sxs-lookup"><span data-stu-id="370ed-110">Operators</span></span>  
  
|<span data-ttu-id="370ed-111">運算子名稱</span><span class="sxs-lookup"><span data-stu-id="370ed-111">Operator Name</span></span>|<span data-ttu-id="370ed-112">描述</span><span class="sxs-lookup"><span data-stu-id="370ed-112">Description</span></span>|<span data-ttu-id="370ed-113">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="370ed-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="370ed-114">更多資訊</span><span class="sxs-lookup"><span data-stu-id="370ed-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="370ed-115">Skip</span><span class="sxs-lookup"><span data-stu-id="370ed-115">Skip</span></span>|<span data-ttu-id="370ed-116">略過項目直至序列中指定的位置為止。</span><span class="sxs-lookup"><span data-stu-id="370ed-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="370ed-117">不適用。</span><span class="sxs-lookup"><span data-stu-id="370ed-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName>|  
|<span data-ttu-id="370ed-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="370ed-118">SkipWhile</span></span>|<span data-ttu-id="370ed-119">根據述詞函式跳過項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="370ed-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="370ed-120">不適用。</span><span class="sxs-lookup"><span data-stu-id="370ed-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName>|  
|<span data-ttu-id="370ed-121">Take</span><span class="sxs-lookup"><span data-stu-id="370ed-121">Take</span></span>|<span data-ttu-id="370ed-122">採用序列中最多到指定位置為止的項目。</span><span class="sxs-lookup"><span data-stu-id="370ed-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="370ed-123">不適用。</span><span class="sxs-lookup"><span data-stu-id="370ed-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=fullName>|  
|<span data-ttu-id="370ed-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="370ed-124">TakeWhile</span></span>|<span data-ttu-id="370ed-125">根據述詞函式採用項目，直到不符合條件的項目為止。</span><span class="sxs-lookup"><span data-stu-id="370ed-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="370ed-126">不適用。</span><span class="sxs-lookup"><span data-stu-id="370ed-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a><span data-ttu-id="370ed-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="370ed-127">See Also</span></span>  
 <span data-ttu-id="370ed-128"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="370ed-128"><xref:System.Linq></span></span>   
 [<span data-ttu-id="370ed-129">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="370ed-129">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)

