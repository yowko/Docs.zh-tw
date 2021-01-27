---
title: 私用建構函式 - C# 程式設計手冊
description: '私用的函式是 c # 中的特殊實例函式，用來限制物件的建立方式。 它們可搭配 factory 方法或其他結構慣用語使用。'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 980a638fbe6250b3d47a3effc7cbad5ec57fbcad
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899396"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="dc7a3-104">私用建構函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="dc7a3-104">Private Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="dc7a3-105">私用建構函式是一種特殊的執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="dc7a3-105">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="dc7a3-106">它通常會用於只包含靜態成員的類別。</span><span class="sxs-lookup"><span data-stu-id="dc7a3-106">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="dc7a3-107">如果類別具有一或多個私用建構函式，而且沒有任何公用建構函式，則其他類別 (巢狀類別除外) 無法建立此類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="dc7a3-107">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="dc7a3-108">例如：</span><span class="sxs-lookup"><span data-stu-id="dc7a3-108">For example:</span></span>  
  
 [!code-csharp[ClassWithPrivateConstructorExample#1](snippets/private-constructors/Program.cs#1)]
  
 <span data-ttu-id="dc7a3-109">宣告空的建構函式可防止自動產生無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="dc7a3-109">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="dc7a3-110">請注意，如果您未搭配建構函式使用存取修飾詞，預設仍會是私用的。</span><span class="sxs-lookup"><span data-stu-id="dc7a3-110">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="dc7a3-111">不過，通常會明確使用 [private](../../language-reference/keywords/private.md) 修飾詞來指出無法具現化類別。</span><span class="sxs-lookup"><span data-stu-id="dc7a3-111">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="dc7a3-112">當類別沒有執行個體欄位或方法 (例如 <xref:System.Math> 類別)，或是您要呼叫方法以取得類別的執行個體時，可以使用私用建構函式來防止建立類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="dc7a3-112">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="dc7a3-113">如果類別中的所有方法都是靜態的，請考慮將整個類別變為靜態。</span><span class="sxs-lookup"><span data-stu-id="dc7a3-113">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="dc7a3-114">如需詳細資訊，請參閱[靜態類別和靜態類別成員](./static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="dc7a3-114">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc7a3-115">範例</span><span class="sxs-lookup"><span data-stu-id="dc7a3-115">Example</span></span>  

 <span data-ttu-id="dc7a3-116">以下是使用私用建構函式的類別範例。</span><span class="sxs-lookup"><span data-stu-id="dc7a3-116">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[CounterClassWithPrivateConstructor#2](snippets/private-constructors/Program.cs#2)]
  
 <span data-ttu-id="dc7a3-117">請注意，如果您將範例中的下列陳述式取消註解，這時將會產生錯誤，因為建構函式會因其保護層級而無法存取：</span><span class="sxs-lookup"><span data-stu-id="dc7a3-117">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[ErrorInstantiatingUsingPrivateConstructor#13](snippets/private-constructors/Program.cs#3)]
  
## <a name="c-language-specification"></a><span data-ttu-id="dc7a3-118">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="dc7a3-118">C# Language Specification</span></span>  

<span data-ttu-id="dc7a3-119">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的[私用建構式](~/_csharplang/spec/classes.md#private-constructors)。</span><span class="sxs-lookup"><span data-stu-id="dc7a3-119">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="dc7a3-120">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="dc7a3-120">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dc7a3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc7a3-121">See also</span></span>

- [<span data-ttu-id="dc7a3-122">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="dc7a3-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="dc7a3-123">類別和結構</span><span class="sxs-lookup"><span data-stu-id="dc7a3-123">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="dc7a3-124">建構函式</span><span class="sxs-lookup"><span data-stu-id="dc7a3-124">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="dc7a3-125">完成項</span><span class="sxs-lookup"><span data-stu-id="dc7a3-125">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="dc7a3-126">私人</span><span class="sxs-lookup"><span data-stu-id="dc7a3-126">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="dc7a3-127">public</span><span class="sxs-lookup"><span data-stu-id="dc7a3-127">public</span></span>](../../language-reference/keywords/public.md)
