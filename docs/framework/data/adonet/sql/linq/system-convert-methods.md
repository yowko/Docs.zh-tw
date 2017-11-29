---
title: "System.Convert 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7f4ed9cc6ae4668fe978b0e7f685e360f1044e6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="systemconvert-methods"></a><span data-ttu-id="28396-102">System.Convert 方法</span><span class="sxs-lookup"><span data-stu-id="28396-102">System.Convert Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="28396-103"> 不支援下列 <xref:System.Convert> 方法。</span><span class="sxs-lookup"><span data-stu-id="28396-103"> does not support the following <xref:System.Convert> methods.</span></span>  
  
-   <span data-ttu-id="28396-104">具有 <xref:System.IFormatProvider> 參數的版本。</span><span class="sxs-lookup"><span data-stu-id="28396-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>  
  
-   <span data-ttu-id="28396-105">牽涉字元陣列或位元組陣列的方法：</span><span class="sxs-lookup"><span data-stu-id="28396-105">Methods that involve char arrays or byte arrays:</span></span>  
  
    -   <xref:System.Convert.FromBase64CharArray%2A>  
  
    -   <xref:System.Convert.ToBase64CharArray%2A>  
  
    -   <xref:System.Convert.FromBase64String%2A>  
  
    -   <xref:System.Convert.ToBase64String%2A>  
  
-   <span data-ttu-id="28396-106">下列方法：</span><span class="sxs-lookup"><span data-stu-id="28396-106">The following methods:</span></span>  
  
    -   <span data-ttu-id="28396-107">`public static <Type2> To<Type2>(<Type1> value);` 其中</span><span class="sxs-lookup"><span data-stu-id="28396-107">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>  
  
         <span data-ttu-id="28396-108">`Type1` 和 `Type2` 各自為 `sbyte`、`uint`、`ulong` 或 `ushort`。</span><span class="sxs-lookup"><span data-stu-id="28396-108">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>  
  
    -   <span data-ttu-id="28396-109">C#: </span><span class="sxs-lookup"><span data-stu-id="28396-109">C#:</span></span>  
  
         `int To<int type>(string value, int fromBase),`  
  
         `ToString(... value, int toBase)`  
  
    -   <span data-ttu-id="28396-110">Visual Basic：</span><span class="sxs-lookup"><span data-stu-id="28396-110">Visual Basic:</span></span>  
  
         `Function To(Of [Numeric])(value as String, fromBase As Integer)`  
  
         `As [Numeric], ToString( value As …, toBase As Integer)`  
  
    -   <xref:System.Convert.IsDBNull%2A>  
  
    -   <xref:System.Convert.GetTypeCode%2A>  
  
    -   <xref:System.Convert.ChangeType%2A>  
  
## <a name="see-also"></a><span data-ttu-id="28396-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28396-111">See Also</span></span>  
 [<span data-ttu-id="28396-112">資料型別和函式</span><span class="sxs-lookup"><span data-stu-id="28396-112">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
