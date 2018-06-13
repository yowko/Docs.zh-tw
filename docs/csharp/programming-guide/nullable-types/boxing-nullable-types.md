---
title: Box 處理可為 Null 的類型 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
ms.openlocfilehash: e2c7602bf45f1861d3a32a73824e9fedf0a4d29d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334752"
---
# <a name="boxing-nullable-types-c-programming-guide"></a><span data-ttu-id="d4f56-102">Box 處理可為 Null 的類型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="d4f56-102">Boxing Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="d4f56-103">如為非 Null 的物件，以可為 Null 的型別為基礎的物件僅能以 boxing 處理。</span><span class="sxs-lookup"><span data-stu-id="d4f56-103">Objects based on nullable types are only boxed if the object is non-null.</span></span> <span data-ttu-id="d4f56-104">如果 <xref:System.Nullable%601.HasValue%2A> 是 `false`，則物件參考會指派給 `null` 而不是 boxing。</span><span class="sxs-lookup"><span data-stu-id="d4f56-104">If <xref:System.Nullable%601.HasValue%2A> is `false`, the object reference is assigned to `null` instead of boxing.</span></span> <span data-ttu-id="d4f56-105">例如: </span><span class="sxs-lookup"><span data-stu-id="d4f56-105">For example:</span></span>  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 <span data-ttu-id="d4f56-106">如果為非 Null 的物件 - 如果 <xref:System.Nullable%601.HasValue%2A> 是 `true` - 則發生 boxing，但只有可為 Null 物件依據的基礎類型會經過 boxing 處理。</span><span class="sxs-lookup"><span data-stu-id="d4f56-106">If the object is non-null -- if <xref:System.Nullable%601.HasValue%2A> is `true` -- then boxing occurs, but only the underlying type that the nullable object is based on is boxed.</span></span> <span data-ttu-id="d4f56-107">以 boxing 處理非 Null 的可為 Null 的實值型別，會以 boxing 處理實值型別本身，不會處理包裝實值型別的 <xref:System.Nullable%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="d4f56-107">Boxing a non-null nullable value type boxes the value type itself, not the <xref:System.Nullable%601?displayProperty=nameWithType> that wraps the value type.</span></span> <span data-ttu-id="d4f56-108">例如: </span><span class="sxs-lookup"><span data-stu-id="d4f56-108">For example:</span></span>  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 <span data-ttu-id="d4f56-109">兩個經過 boxing 處理的物件，和經過 boxing 處理的不可為 Null 的型別所建立的物件相同。</span><span class="sxs-lookup"><span data-stu-id="d4f56-109">The two boxed objects are identical to those created by boxing non-nullable types.</span></span> <span data-ttu-id="d4f56-110">而且，就像經過 boxing 處理的不可為 Null 的型別，它們可以取消 boxing 處理成為可為 Null 的型別，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="d4f56-110">And, just like non-nullable boxed types, they can be unboxed into nullable types, as in the following example:</span></span>  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a><span data-ttu-id="d4f56-111">備註</span><span class="sxs-lookup"><span data-stu-id="d4f56-111">Remarks</span></span>  
 <span data-ttu-id="d4f56-112">經過 boxing 處理後，可為 Null 之型別的行為提供兩個優點︰</span><span class="sxs-lookup"><span data-stu-id="d4f56-112">The behavior of nullable types when boxed provides two advantages:</span></span>  
  
1.  <span data-ttu-id="d4f56-113">可為 Null 的物件及其經過 boxing 處理過的對應項目，可進行 Null 測試︰</span><span class="sxs-lookup"><span data-stu-id="d4f56-113">Nullable objects and their boxed counterpart can be tested for null:</span></span>  
  
    ```csharp  
    bool? b = null;  
    object boxedB = b;  
    if (b == null)  
    {  
      // True.  
    }  
    if (boxedB == null)  
    {  
      // Also true.  
    }  
    ```  
  
2.  <span data-ttu-id="d4f56-114">經過 boxing 處理的可為 Null 的型別完全支援基礎類型的功能︰</span><span class="sxs-lookup"><span data-stu-id="d4f56-114">Boxed nullable types fully support the functionality of the underlying type:</span></span>  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d4f56-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="d4f56-115">See Also</span></span>  
 [<span data-ttu-id="d4f56-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d4f56-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d4f56-117">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="d4f56-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="d4f56-118">如何：識別可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="d4f56-118">How to: Identify a Nullable Type</span></span>](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)
