---
title: 共變數和反變數 (C#)
description: 瞭解共變數和反變數，以及它們如何影響指派相容性。 請參閱示範它們之間差異的程式碼範例。
ms.date: 07/20/2015
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
ms.openlocfilehash: ad4b2a7d7925d7893eb5a8e1d2d7c9ee3dcbd527
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465659"
---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="b627e-104">共變數和反變數 (C#)</span><span class="sxs-lookup"><span data-stu-id="b627e-104">Covariance and Contravariance (C#)</span></span>
<span data-ttu-id="b627e-105">在 C# 中，共變數和反變數可讓您進行陣列類型、委派類型和泛型型別引數的隱含參考轉換。</span><span class="sxs-lookup"><span data-stu-id="b627e-105">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="b627e-106">共變數會保留指派相容性，而反變數則會將它反轉。</span><span class="sxs-lookup"><span data-stu-id="b627e-106">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="b627e-107">下列程式碼示範指派相容性、共變數和反變數之間的差異。</span><span class="sxs-lookup"><span data-stu-id="b627e-107">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
```csharp  
// Assignment compatibility.
string str = "test";  
// An object of a more derived type is assigned to an object of a less derived type.
object obj = str;  
  
// Covariance.
IEnumerable<string> strings = new List<string>();  
// An object that is instantiated with a more derived type argument
// is assigned to an object instantiated with a less derived type argument.
// Assignment compatibility is preserved.
IEnumerable<object> objects = strings;  
  
// Contravariance.
// Assume that the following method is in the class:
// static void SetObject(object o) { }
Action<object> actObject = SetObject;  
// An object that is instantiated with a less derived type argument
// is assigned to an object instantiated with a more derived type argument.
// Assignment compatibility is reversed.
Action<string> actString = actObject;  
```  
  
 <span data-ttu-id="b627e-108">陣列的共變數可將衍生程度較大類型的陣列，隱含轉換成衍生程度較小類型的陣列。</span><span class="sxs-lookup"><span data-stu-id="b627e-108">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="b627e-109">但這項作業不是型別安全的，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="b627e-109">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="b627e-110">共變數和反變數的方法群組支援可讓您比對方法簽章和委派類型。</span><span class="sxs-lookup"><span data-stu-id="b627e-110">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="b627e-111">這可讓您指派方法給委派，不只是具有相符簽章的方法，也可以是會傳回衍生程度較大類型 (共變數) 的方法，或接受衍生程度比委派類型所指定更小類型 (反變數) 的方法。</span><span class="sxs-lookup"><span data-stu-id="b627e-111">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="b627e-112">如需詳細資訊，請參閱[委派中的變異數 (C#)](./variance-in-delegates.md) 和[在委派中使用變異數 (C#)](./using-variance-in-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="b627e-112">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance in Delegates (C#)](./using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="b627e-113">下列程式碼範例示範共變數和反變數的方法群組支援。</span><span class="sxs-lookup"><span data-stu-id="b627e-113">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
```csharp  
static object GetObject() { return null; }  
static void SetObject(object obj) { }  
  
static string GetString() { return ""; }  
static void SetString(string str) { }  
  
static void Test()  
{  
    // Covariance. A delegate specifies a return type as object,  
    // but you can assign a method that returns a string.  
    Func<object> del = GetString;  
  
    // Contravariance. A delegate specifies a parameter type as string,  
    // but you can assign a method that takes an object.  
    Action<string> del2 = SetObject;  
}  
```  
  
 <span data-ttu-id="b627e-114">在 .NET Framework 4 和更新版本中，c # 支援泛型介面和委派中的共變數和反變數，並允許泛型型別參數的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="b627e-114">In .NET Framework 4 and later versions, C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="b627e-115">如需詳細資訊，請參閱[泛型介面中的變異數 (C#)](./variance-in-generic-interfaces.md) 和[委派中的變異數 (C#)](./variance-in-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="b627e-115">For more information, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="b627e-116">下列程式碼範例示範泛型介面的隱含參考轉換。</span><span class="sxs-lookup"><span data-stu-id="b627e-116">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="b627e-117">如果泛型介面或委派的泛型參數宣告為共變數或反變數，此泛型介面或委派稱為 *variant*。</span><span class="sxs-lookup"><span data-stu-id="b627e-117">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="b627e-118">C# 可讓您建立自己的 Variant 介面和委派。</span><span class="sxs-lookup"><span data-stu-id="b627e-118">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="b627e-119">如需詳細資訊，請參閱[建立 Variant 泛型介面 (C#)](./creating-variant-generic-interfaces.md) 和[委派中的差異 (C#)](./variance-in-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="b627e-119">For more information, see [Creating Variant Generic Interfaces (C#)](./creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="b627e-120">[相關主題]</span><span class="sxs-lookup"><span data-stu-id="b627e-120">Related Topics</span></span>  
  
|<span data-ttu-id="b627e-121">Title</span><span class="sxs-lookup"><span data-stu-id="b627e-121">Title</span></span>|<span data-ttu-id="b627e-122">描述</span><span class="sxs-lookup"><span data-stu-id="b627e-122">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b627e-123">泛型介面中的差異 (C#)</span><span class="sxs-lookup"><span data-stu-id="b627e-123">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)|<span data-ttu-id="b627e-124">討論泛型介面中的共變數和反變數，並在 .NET 中提供 variant 泛型介面的清單。</span><span class="sxs-lookup"><span data-stu-id="b627e-124">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in .NET.</span></span>|  
|[<span data-ttu-id="b627e-125">建立 Variant 泛型介面 (C#)</span><span class="sxs-lookup"><span data-stu-id="b627e-125">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)|<span data-ttu-id="b627e-126">示範如何建立自訂 Variant 介面。</span><span class="sxs-lookup"><span data-stu-id="b627e-126">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="b627e-127">針對泛型集合使用介面中的變異數 (C#)</span><span class="sxs-lookup"><span data-stu-id="b627e-127">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="b627e-128">示範 <xref:System.Collections.Generic.IEnumerable%601> 和 <xref:System.IComparable%601> 介面中的共變數和反變數支援如何協助您重複使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="b627e-128">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="b627e-129">委派中的差異 (C#)</span><span class="sxs-lookup"><span data-stu-id="b627e-129">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)|<span data-ttu-id="b627e-130">討論泛型和非泛型委派中的共變數和反變數，並在 .NET 中提供 variant 泛型委派的清單。</span><span class="sxs-lookup"><span data-stu-id="b627e-130">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in .NET.</span></span>|  
|[<span data-ttu-id="b627e-131">在委派中使用變異數 (C#)</span><span class="sxs-lookup"><span data-stu-id="b627e-131">Using Variance in Delegates (C#)</span></span>](./using-variance-in-delegates.md)|<span data-ttu-id="b627e-132">示範如何在非泛型委派中使用共變數和反變數支援，以比對方法簽章和委派類型。</span><span class="sxs-lookup"><span data-stu-id="b627e-132">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="b627e-133">針對 Func 與 Action 泛型委派使用變異數 (C#)</span><span class="sxs-lookup"><span data-stu-id="b627e-133">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="b627e-134">示範 `Func` 和 `Action` 委派中的共變數和反變數支援如何協助您重複使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="b627e-134">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
