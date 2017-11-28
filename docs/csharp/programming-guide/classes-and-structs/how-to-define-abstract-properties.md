---
title: "如何：定義抽象屬性 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cd8a42c1040180c19bc58627ab0c6a21ace77773
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="0240a-102">如何：定義抽象屬性 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="0240a-102">How to: Define Abstract Properties (C# Programming Guide)</span></span>
<span data-ttu-id="0240a-103">下例示範如何定義[抽象](../../../csharp/language-reference/keywords/abstract.md)屬性。</span><span class="sxs-lookup"><span data-stu-id="0240a-103">The following example shows how to define [abstract](../../../csharp/language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="0240a-104">抽象屬性宣告不提供屬性存取子實作 -- 它會宣告類別支援屬性，但保留衍生類別的存取子實作。</span><span class="sxs-lookup"><span data-stu-id="0240a-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="0240a-105">下例示範如何實作繼承自基底類別的抽象屬性。</span><span class="sxs-lookup"><span data-stu-id="0240a-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="0240a-106">這個範例包含三個檔案，每個檔案都是各自編譯，產生的組件是下次編譯參考的對象：</span><span class="sxs-lookup"><span data-stu-id="0240a-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
-   <span data-ttu-id="0240a-107">abstractshape.cs：包含抽象 `Area` 屬性的 `Shape` 類別。</span><span class="sxs-lookup"><span data-stu-id="0240a-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
-   <span data-ttu-id="0240a-108">shapes.cs：`Shape` 類別的子類別。</span><span class="sxs-lookup"><span data-stu-id="0240a-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
-   <span data-ttu-id="0240a-109">shapetest.cs：要顯示某些 `Shape` 衍生物件區域的測試程式。</span><span class="sxs-lookup"><span data-stu-id="0240a-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="0240a-110">若要編譯範例，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="0240a-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="0240a-111">這會建立可執行檔 shapetest.exe。</span><span class="sxs-lookup"><span data-stu-id="0240a-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0240a-112">範例</span><span class="sxs-lookup"><span data-stu-id="0240a-112">Example</span></span>  
 <span data-ttu-id="0240a-113">這個檔案會宣告包含 `double` 類型 `Area` 屬性的 `Shape` 類別。</span><span class="sxs-lookup"><span data-stu-id="0240a-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   <span data-ttu-id="0240a-114">屬性的修飾詞是放在屬性宣告中。</span><span class="sxs-lookup"><span data-stu-id="0240a-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="0240a-115">例如：</span><span class="sxs-lookup"><span data-stu-id="0240a-115">For example:</span></span>  
  
    ```  
    public abstract double Area  
    ```  
  
-   <span data-ttu-id="0240a-116">宣告抽象屬性時 (例如本例的 `Area`)，您只要指出有哪些屬性存取子可用即可，不用實作它們。</span><span class="sxs-lookup"><span data-stu-id="0240a-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="0240a-117">本例中只有 [get](../../../csharp/language-reference/keywords/get.md) 存取子可用，所以此屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="0240a-117">In this example, only a [get](../../../csharp/language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0240a-118">範例</span><span class="sxs-lookup"><span data-stu-id="0240a-118">Example</span></span>  
 <span data-ttu-id="0240a-119">下列程式碼會示範 `Shape` 的三個子類別，以及它們如何覆寫 `Area` 屬性以提供它們自己的實作。</span><span class="sxs-lookup"><span data-stu-id="0240a-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="0240a-120">範例</span><span class="sxs-lookup"><span data-stu-id="0240a-120">Example</span></span>  
 <span data-ttu-id="0240a-121">下列程式碼會示範測試程式，建立多個 `Shape` 衍生物件並列印其區域。</span><span class="sxs-lookup"><span data-stu-id="0240a-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0240a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0240a-122">See Also</span></span>  
 [<span data-ttu-id="0240a-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0240a-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0240a-124">類別和結構</span><span class="sxs-lookup"><span data-stu-id="0240a-124">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="0240a-125">抽象和密封類別以及類別成員</span><span class="sxs-lookup"><span data-stu-id="0240a-125">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [<span data-ttu-id="0240a-126">屬性</span><span class="sxs-lookup"><span data-stu-id="0240a-126">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="0240a-127">如何：使用命令列建立和使用組件</span><span class="sxs-lookup"><span data-stu-id="0240a-127">How to: Create and Use Assemblies Using the Command Line</span></span>](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)
