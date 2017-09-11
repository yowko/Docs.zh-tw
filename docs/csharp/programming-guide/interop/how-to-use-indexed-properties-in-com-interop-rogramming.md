---
title: "如何：在 COM Interop 程式設計中使用索引的屬性 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 19e620415adefd6190d3896377eaf6a7cf944f28
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="5cccc-102">如何：在 COM Interop 程式設計中使用索引的屬性 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="5cccc-102">How to: Use Indexed Properties in COM Interop Programming (C# Programming Guide)</span></span>
<span data-ttu-id="5cccc-103">「索引的屬性」 改善具有參數的 COM 屬性在 C# 程式設計中的使用方式。</span><span class="sxs-lookup"><span data-stu-id="5cccc-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="5cccc-104">索引的屬性是與其他 Visual C# 功能 (例如[具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)、新類型 ([dynamic](../../../csharp/language-reference/keywords/dynamic.md)) 和[內嵌類型資訊](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)) 搭配運作，以加強 Microsoft Office 程式設計。</span><span class="sxs-lookup"><span data-stu-id="5cccc-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../../csharp/language-reference/keywords/dynamic.md)), and [embedded type information](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="5cccc-105">在舊版 C# 中，只有在 `get` 方法沒有參數以及 `set` 方法只有一個值參數時，才能將方法存取為屬性。</span><span class="sxs-lookup"><span data-stu-id="5cccc-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="5cccc-106">不過，並非所有 COM 屬性都符合這些限制。</span><span class="sxs-lookup"><span data-stu-id="5cccc-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="5cccc-107">例如，Excel [Range](http://go.microsoft.com/fwlink/?LinkId=166053) 屬性具有需要範圍名稱參數的 `get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="5cccc-107">For example, the Excel [Range](http://go.microsoft.com/fwlink/?LinkId=166053) property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="5cccc-108">在過去，因為您無法直接存取 `Range` 屬性，所以必須改為使用 `get_Range` 方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="5cccc-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 <span data-ttu-id="5cccc-109">[!code-cs[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="5cccc-109">[!code-cs[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]</span></span>  
  
 <span data-ttu-id="5cccc-110">索引的屬性可讓您改為撰寫下列程式碼︰</span><span class="sxs-lookup"><span data-stu-id="5cccc-110">Indexed properties enable you to write the following instead:</span></span>  
  
 <span data-ttu-id="5cccc-111">[!code-cs[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="5cccc-111">[!code-cs[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cccc-112">先前的範例也會使用[選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)功能，以讓您略過 `Type.Missing`。</span><span class="sxs-lookup"><span data-stu-id="5cccc-112">The previous example also uses the [optional arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="5cccc-113">與在 Visual C# 2008 和更早版本中設定 [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) 物件的 `Value` 屬性值類似，需要兩個引數。</span><span class="sxs-lookup"><span data-stu-id="5cccc-113">Similarly to set the value of the `Value` property of a [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) object in Visual C# 2008 and earlier, two arguments are required.</span></span> <span data-ttu-id="5cccc-114">其中一個提供選擇性參數的引數，而選擇性參數指定範圍值類型。</span><span class="sxs-lookup"><span data-stu-id="5cccc-114">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="5cccc-115">另一個則提供 `Value` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="5cccc-115">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="5cccc-116">下列範例說明這些技術。</span><span class="sxs-lookup"><span data-stu-id="5cccc-116">The following examples illustrate these techniques.</span></span> <span data-ttu-id="5cccc-117">兩個都將 A1 儲存格的值設定為 `Name`。</span><span class="sxs-lookup"><span data-stu-id="5cccc-117">Both set the value of the A1 cell to `Name`.</span></span>
  
 <span data-ttu-id="5cccc-118">[!code-cs[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="5cccc-118">[!code-cs[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]</span></span>  
  
 <span data-ttu-id="5cccc-119">索引的屬性可讓您改為撰寫下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="5cccc-119">Indexed properties enable you to write the following code instead.</span></span>  
  
 <span data-ttu-id="5cccc-120">[!code-cs[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="5cccc-120">[!code-cs[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]</span></span>  
  
 <span data-ttu-id="5cccc-121">您無法建立自己本身的編製過索引的屬性。</span><span class="sxs-lookup"><span data-stu-id="5cccc-121">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="5cccc-122">這個功能僅支援使用現有已編製過索引的屬性。</span><span class="sxs-lookup"><span data-stu-id="5cccc-122">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cccc-123">範例</span><span class="sxs-lookup"><span data-stu-id="5cccc-123">Example</span></span>  
 <span data-ttu-id="5cccc-124">下列程式碼顯示完整範例。</span><span class="sxs-lookup"><span data-stu-id="5cccc-124">The following code shows a complete example.</span></span> <span data-ttu-id="5cccc-125">如需如何設定存取 Office API 之專案的詳細資訊，請參閱[如何：使用 Visual C# 功能存取 Office Interop 物件](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="5cccc-125">For more information about how to set up a project that accesses the Office API, see [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
 <span data-ttu-id="5cccc-126">[!code-cs[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="5cccc-126">[!code-cs[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cccc-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cccc-127">See Also</span></span>  
 <span data-ttu-id="5cccc-128">[具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="5cccc-128">[Named and Optional Arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) </span></span>  
 <span data-ttu-id="5cccc-129">[dynamic](../../../csharp/language-reference/keywords/dynamic.md) </span><span class="sxs-lookup"><span data-stu-id="5cccc-129">[dynamic](../../../csharp/language-reference/keywords/dynamic.md) </span></span>  
 <span data-ttu-id="5cccc-130">[使用動態類型](../../../csharp/programming-guide/types/using-type-dynamic.md) </span><span class="sxs-lookup"><span data-stu-id="5cccc-130">[Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md) </span></span>  
 <span data-ttu-id="5cccc-131">[如何：在 Office 程式設計中使用具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) </span><span class="sxs-lookup"><span data-stu-id="5cccc-131">[How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) </span></span>  
 <span data-ttu-id="5cccc-132">[如何：使用 Visual C# 功能存取 Office Interop 物件](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md) </span><span class="sxs-lookup"><span data-stu-id="5cccc-132">[How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md) </span></span>  
 [<span data-ttu-id="5cccc-133">逐步解說：Office 程式設計</span><span class="sxs-lookup"><span data-stu-id="5cccc-133">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)

