---
title: System.Convert 方法
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: c3b8c7105578c57547b79bc95b633bcc6449a0ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591707"
---
# <a name="systemconvert-methods"></a><span data-ttu-id="05da9-102">System.Convert 方法</span><span class="sxs-lookup"><span data-stu-id="05da9-102">System.Convert Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="05da9-103">不支援下列 <xref:System.Convert> 方法。</span><span class="sxs-lookup"><span data-stu-id="05da9-103">does not support the following <xref:System.Convert> methods.</span></span>  
  
-   <span data-ttu-id="05da9-104">具有 <xref:System.IFormatProvider> 參數的版本。</span><span class="sxs-lookup"><span data-stu-id="05da9-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>  
  
-   <span data-ttu-id="05da9-105">牽涉字元陣列或位元組陣列的方法：</span><span class="sxs-lookup"><span data-stu-id="05da9-105">Methods that involve char arrays or byte arrays:</span></span>  
  
    -   <xref:System.Convert.FromBase64CharArray%2A>  
  
    -   <xref:System.Convert.ToBase64CharArray%2A>  
  
    -   <xref:System.Convert.FromBase64String%2A>  
  
    -   <xref:System.Convert.ToBase64String%2A>  
  
-   <span data-ttu-id="05da9-106">下列方法：</span><span class="sxs-lookup"><span data-stu-id="05da9-106">The following methods:</span></span>  
  
    -   <span data-ttu-id="05da9-107">`public static <Type2> To<Type2>(<Type1> value);` 其中</span><span class="sxs-lookup"><span data-stu-id="05da9-107">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>  
  
         <span data-ttu-id="05da9-108">`Type1` 和 `Type2` 各自為 `sbyte`、`uint`、`ulong` 或 `ushort`。</span><span class="sxs-lookup"><span data-stu-id="05da9-108">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>  
  
    -   <span data-ttu-id="05da9-109">C#: </span><span class="sxs-lookup"><span data-stu-id="05da9-109">C#:</span></span>  
  
         `int To<int type>(string value, int fromBase),`  
  
         `ToString(... value, int toBase)`  
  
    -   <span data-ttu-id="05da9-110">Visual Basic：</span><span class="sxs-lookup"><span data-stu-id="05da9-110">Visual Basic:</span></span>  
  
         `Function To(Of [Numeric])(value as String, fromBase As Integer)`  
  
         `As [Numeric], ToString( value As …, toBase As Integer)`  
  
    -   <xref:System.Convert.IsDBNull%2A>  
  
    -   <xref:System.Convert.GetTypeCode%2A>  
  
    -   <xref:System.Convert.ChangeType%2A>  
  
## <a name="see-also"></a><span data-ttu-id="05da9-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05da9-111">See also</span></span>
- [<span data-ttu-id="05da9-112">資料類型和函式</span><span class="sxs-lookup"><span data-stu-id="05da9-112">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
