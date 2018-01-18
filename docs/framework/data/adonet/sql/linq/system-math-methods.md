---
title: "System.Math 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cfcbf915703c72211fc9d958abfda7ffac8aafdc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="systemmath-methods"></a><span data-ttu-id="d7c72-102">System.Math 方法</span><span class="sxs-lookup"><span data-stu-id="d7c72-102">System.Math Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="d7c72-103"> 不支援下列 <xref:System.Math> 方法。</span><span class="sxs-lookup"><span data-stu-id="d7c72-103"> does not support the following <xref:System.Math> methods.</span></span>  
  
-   <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=nameWithType>  
  
-   <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=nameWithType>  
  
## <a name="differences-from-net"></a><span data-ttu-id="d7c72-104">與 .NET 的差異</span><span class="sxs-lookup"><span data-stu-id="d7c72-104">Differences from .NET</span></span>  
 <span data-ttu-id="d7c72-105">.NET Framework 使用的捨入語意 (Semantics) 與 SQL Server 不同。</span><span class="sxs-lookup"><span data-stu-id="d7c72-105">The .NET Framework has different rounding semantics from SQL Server.</span></span> <span data-ttu-id="d7c72-106"><xref:System.Math.Round%2A> .NET Framework 中的方法會執行*銀行進位*，其中以.5 的數字四捨五入到最接近的偶數位數而不是下一個較高的數字。</span><span class="sxs-lookup"><span data-stu-id="d7c72-106">The <xref:System.Math.Round%2A> method in the .NET Framework performs *Banker's rounding*, where numbers that ends in .5 round to the nearest even digit instead of to the next higher digit.</span></span> <span data-ttu-id="d7c72-107">例如，2.5 會捨入為 2，而 3.5 會進位為 4 </span><span class="sxs-lookup"><span data-stu-id="d7c72-107">For example, 2.5 rounds to 2, while 3.5 rounds to 4.</span></span> <span data-ttu-id="d7c72-108">(當資料交易很大時，此法有助於避免系統性地偏向較高位數的值)。</span><span class="sxs-lookup"><span data-stu-id="d7c72-108">(This technique helps avoid systematic bias toward higher values in large data transactions.)</span></span>  
  
 <span data-ttu-id="d7c72-109">在 SQL 中，`ROUND` 函式則會一律往遠離 0 的方向捨入。</span><span class="sxs-lookup"><span data-stu-id="d7c72-109">In SQL, the `ROUND` function instead always rounds away from 0.</span></span> <span data-ttu-id="d7c72-110">因此 2.5 會捨入為 3，這與 .NET Framework 中捨入為 2 相反。</span><span class="sxs-lookup"><span data-stu-id="d7c72-110">Therefore 2.5 rounds to 3, contrasted with its rounding to 2 in the .NET Framework.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="d7c72-111"> 會採用 SQL `ROUND` 語意，不會嘗試實作 Banker's Rounding (四捨六入五成雙)。</span><span class="sxs-lookup"><span data-stu-id="d7c72-111"> passes through to the SQL `ROUND` semantics and does not try to implement Banker's rounding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7c72-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="d7c72-112">See Also</span></span>  
 [<span data-ttu-id="d7c72-113">資料類型和函式</span><span class="sxs-lookup"><span data-stu-id="d7c72-113">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
