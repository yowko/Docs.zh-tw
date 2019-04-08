---
title: System.Convert 方法
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: 0d98d159c24e1a47723aeb07a9654fe22b1d9464
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198214"
---
# <a name="systemconvert-methods"></a><span data-ttu-id="b7383-102">System.Convert 方法</span><span class="sxs-lookup"><span data-stu-id="b7383-102">System.Convert Methods</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b7383-103">不支援下列<xref:System.Convert>方法。</span><span class="sxs-lookup"><span data-stu-id="b7383-103">does not support the following <xref:System.Convert> methods.</span></span>  
  
-   <span data-ttu-id="b7383-104">具有 <xref:System.IFormatProvider> 參數的版本。</span><span class="sxs-lookup"><span data-stu-id="b7383-104">Versions with an <xref:System.IFormatProvider> parameter.</span></span>  
  
-   <span data-ttu-id="b7383-105">牽涉字元陣列或位元組陣列的方法：</span><span class="sxs-lookup"><span data-stu-id="b7383-105">Methods that involve char arrays or byte arrays:</span></span>  
  
    -   <xref:System.Convert.FromBase64CharArray%2A>  
  
    -   <xref:System.Convert.ToBase64CharArray%2A>  
  
    -   <xref:System.Convert.FromBase64String%2A>  
  
    -   <xref:System.Convert.ToBase64String%2A>  
  
-   <span data-ttu-id="b7383-106">下列方法：</span><span class="sxs-lookup"><span data-stu-id="b7383-106">The following methods:</span></span>  
  
    -   `public static <Type2> To<Type2>(<Type1> value);` <span data-ttu-id="b7383-107">其中</span><span class="sxs-lookup"><span data-stu-id="b7383-107">where</span></span>  
  
         `Type1` <span data-ttu-id="b7383-108">並`Type2`各自`sbyte`， `uint`， `ulong`，或`ushort`。</span><span class="sxs-lookup"><span data-stu-id="b7383-108">and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>  
  
    -   <span data-ttu-id="b7383-109">C#: </span><span class="sxs-lookup"><span data-stu-id="b7383-109">C#:</span></span>  
  
         `int To<int type>(string value, int fromBase),`  
  
         `ToString(... value, int toBase)`  
  
    -   <span data-ttu-id="b7383-110">Visual Basic：</span><span class="sxs-lookup"><span data-stu-id="b7383-110">Visual Basic:</span></span>  
  
         `Function To(Of [Numeric])(value as String, fromBase As Integer)`  
  
         `As [Numeric], ToString( value As …, toBase As Integer)`  
  
    -   <xref:System.Convert.IsDBNull%2A>  
  
    -   <xref:System.Convert.GetTypeCode%2A>  
  
    -   <xref:System.Convert.ChangeType%2A>  
  
## <a name="see-also"></a><span data-ttu-id="b7383-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7383-111">See also</span></span>

- [<span data-ttu-id="b7383-112">資料類型與函式</span><span class="sxs-lookup"><span data-stu-id="b7383-112">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
