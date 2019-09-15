---
title: HOW TO：定義抽象屬性 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 57fd2ed3a26bf5986f9c8a1a6cae6b041811e84c
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970891"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="2cf88-102">作法：定義抽象屬性 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="2cf88-102">How to: Define Abstract Properties (C# Programming Guide)</span></span>
<span data-ttu-id="2cf88-103">下例示範如何定義[抽象](../../language-reference/keywords/abstract.md)屬性。</span><span class="sxs-lookup"><span data-stu-id="2cf88-103">The following example shows how to define [abstract](../../language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="2cf88-104">抽象屬性宣告不提供屬性存取子實作 -- 它會宣告類別支援屬性，但保留衍生類別的存取子實作。</span><span class="sxs-lookup"><span data-stu-id="2cf88-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="2cf88-105">下例示範如何實作繼承自基底類別的抽象屬性。</span><span class="sxs-lookup"><span data-stu-id="2cf88-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="2cf88-106">這個範例包含三個檔案，每個檔案都是各自編譯，產生的組件是下次編譯參考的對象：</span><span class="sxs-lookup"><span data-stu-id="2cf88-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
- <span data-ttu-id="2cf88-107">abstractshape.cs：包含抽象 `Area` 屬性的 `Shape` 類別。</span><span class="sxs-lookup"><span data-stu-id="2cf88-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
- <span data-ttu-id="2cf88-108">shapes.cs：`Shape` 類別的子類別。</span><span class="sxs-lookup"><span data-stu-id="2cf88-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
- <span data-ttu-id="2cf88-109">shapetest.cs：要顯示某些 `Shape` 衍生物件區域的測試程式。</span><span class="sxs-lookup"><span data-stu-id="2cf88-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="2cf88-110">若要編譯範例，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="2cf88-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="2cf88-111">這會建立可執行檔 shapetest.exe。</span><span class="sxs-lookup"><span data-stu-id="2cf88-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cf88-112">範例</span><span class="sxs-lookup"><span data-stu-id="2cf88-112">Example</span></span>  
 <span data-ttu-id="2cf88-113">這個檔案會宣告包含 `double` 類型 `Area` 屬性的 `Shape` 類別。</span><span class="sxs-lookup"><span data-stu-id="2cf88-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- <span data-ttu-id="2cf88-114">屬性的修飾詞是放在屬性宣告中。</span><span class="sxs-lookup"><span data-stu-id="2cf88-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="2cf88-115">例如：</span><span class="sxs-lookup"><span data-stu-id="2cf88-115">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- <span data-ttu-id="2cf88-116">宣告抽象屬性時 (例如本例的 `Area`)，您只要指出有哪些屬性存取子可用即可，不用實作它們。</span><span class="sxs-lookup"><span data-stu-id="2cf88-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="2cf88-117">本例中只有 [get](../../language-reference/keywords/get.md) 存取子可用，所以此屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="2cf88-117">In this example, only a [get](../../language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cf88-118">範例</span><span class="sxs-lookup"><span data-stu-id="2cf88-118">Example</span></span>  
 <span data-ttu-id="2cf88-119">下列程式碼會示範 `Shape` 的三個子類別，以及它們如何覆寫 `Area` 屬性以提供它們自己的實作。</span><span class="sxs-lookup"><span data-stu-id="2cf88-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="2cf88-120">範例</span><span class="sxs-lookup"><span data-stu-id="2cf88-120">Example</span></span>  
 <span data-ttu-id="2cf88-121">下列程式碼會示範測試程式，建立多個 `Shape` 衍生物件並列印其區域。</span><span class="sxs-lookup"><span data-stu-id="2cf88-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="2cf88-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cf88-122">See also</span></span>

- [<span data-ttu-id="2cf88-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2cf88-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2cf88-124">類別和結構</span><span class="sxs-lookup"><span data-stu-id="2cf88-124">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="2cf88-125">抽象和密封類別以及類別成員</span><span class="sxs-lookup"><span data-stu-id="2cf88-125">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="2cf88-126">屬性</span><span class="sxs-lookup"><span data-stu-id="2cf88-126">Properties</span></span>](./properties.md)
