---
title: "如何：在 COM Interop 程式設計中使用索引的屬性 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2538dae8f02b17a77cc1eb2798b8b38a7f1d7db2
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="1d2b0-102">如何：在 COM Interop 程式設計中使用索引的屬性 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="1d2b0-102">How to: Use Indexed Properties in COM Interop Programming (C# Programming Guide)</span></span>
<span data-ttu-id="1d2b0-103">「索引的屬性」 改善具有參數的 COM 屬性在 C# 程式設計中的使用方式。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="1d2b0-104">索引的屬性是與其他 Visual C# 功能 (例如[具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)、新類型 ([dynamic](../../../csharp/language-reference/keywords/dynamic.md)) 和[內嵌類型資訊](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)) 搭配運作，以加強 Microsoft Office 程式設計。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../../csharp/language-reference/keywords/dynamic.md)), and [embedded type information](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="1d2b0-105">在舊版 C# 中，只有在 `get` 方法沒有參數以及 `set` 方法只有一個值參數時，才能將方法存取為屬性。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="1d2b0-106">不過，並非所有 COM 屬性都符合這些限制。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="1d2b0-107">例如，Excel [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.range.aspx) 屬性具有需要範圍名稱參數的 `get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-107">For example, the Excel [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.range.aspx) property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="1d2b0-108">在過去，因為您無法直接存取 `Range` 屬性，所以必須改為使用 `get_Range` 方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 <span data-ttu-id="1d2b0-109">索引的屬性可讓您改為撰寫下列程式碼︰</span><span class="sxs-lookup"><span data-stu-id="1d2b0-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="1d2b0-110">先前的範例也會使用[選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)功能，以讓您略過 `Type.Missing`。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-110">The previous example also uses the [optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="1d2b0-111">與在 Visual C# 2008 和更早版本中設定 [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) 物件的 `Value` 屬性值類似，需要兩個引數。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-111">Similarly to set the value of the `Value` property of a [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) object in Visual C# 2008 and earlier, two arguments are required.</span></span> <span data-ttu-id="1d2b0-112">其中一個提供選擇性參數的引數，而選擇性參數指定範圍值類型。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="1d2b0-113">另一個則提供 `Value` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="1d2b0-114">下列範例說明這些技術。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="1d2b0-115">兩個都將 A1 儲存格的值設定為 `Name`。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 <span data-ttu-id="1d2b0-116">索引的屬性可讓您改為撰寫下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 <span data-ttu-id="1d2b0-117">您無法建立自己本身的編製過索引的屬性。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="1d2b0-118">這個功能僅支援使用現有已編製過索引的屬性。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d2b0-119">範例</span><span class="sxs-lookup"><span data-stu-id="1d2b0-119">Example</span></span>  
 <span data-ttu-id="1d2b0-120">下列程式碼顯示完整範例。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-120">The following code shows a complete example.</span></span> <span data-ttu-id="1d2b0-121">如需如何設定存取 Office API 之專案的詳細資訊，請參閱[如何：使用 Visual C# 功能存取 Office Interop 物件](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="1d2b0-121">For more information about how to set up a project that accesses the Office API, see [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1d2b0-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="1d2b0-122">See Also</span></span>  
 [<span data-ttu-id="1d2b0-123">具名和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="1d2b0-123">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [<span data-ttu-id="1d2b0-124">dynamic</span><span class="sxs-lookup"><span data-stu-id="1d2b0-124">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
 [<span data-ttu-id="1d2b0-125">使用動態型別</span><span class="sxs-lookup"><span data-stu-id="1d2b0-125">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [<span data-ttu-id="1d2b0-126">如何：在 Office 程式設計中使用具名和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="1d2b0-126">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
 [<span data-ttu-id="1d2b0-127">如何：使用 Visual C# 功能存取 Office Interop 物件</span><span class="sxs-lookup"><span data-stu-id="1d2b0-127">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 [<span data-ttu-id="1d2b0-128">逐步解說：Office 程式設計</span><span class="sxs-lookup"><span data-stu-id="1d2b0-128">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
