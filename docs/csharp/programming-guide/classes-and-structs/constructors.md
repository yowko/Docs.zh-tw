---
title: 建構函式 - C# 程式設計手冊
description: '建立類別或結構時，會呼叫 c # 中的函式。 使用函式來設定預設值、限制具現化，以及撰寫有彈性且容易閱讀的程式碼。'
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: e8758d7322d7fde45ccbd9eaf9248a3168980bd3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555337"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="7c13a-104">建構函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="7c13a-104">Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="7c13a-105">每當建立[類別](../../language-reference/keywords/class.md)或[結構](../../language-reference/builtin-types/struct.md)時，都會呼叫其建構函式。</span><span class="sxs-lookup"><span data-stu-id="7c13a-105">Whenever a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="7c13a-106">類別或結構可有使用不同引數的多個建構函式。</span><span class="sxs-lookup"><span data-stu-id="7c13a-106">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="7c13a-107">建構函式能讓程式設計師可以設定預設值、限制具現化，以及撰寫彈性且容易閱讀的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7c13a-107">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="7c13a-108">如需詳細資訊和範例，請參閱[使用建構函式](./using-constructors.md)和[執行個體建構函式](./instance-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="7c13a-108">For more information and examples, see [Using Constructors](./using-constructors.md) and [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="parameterless-constructors"></a><span data-ttu-id="7c13a-109">無參數建構函式</span><span class="sxs-lookup"><span data-stu-id="7c13a-109">Parameterless constructors</span></span>
  
<span data-ttu-id="7c13a-110">如果您未提供類別的函式，c # 會根據預設建立一個函式，以具現化物件，並將成員變數設定為預設值，如 [c # 類型的預設值](../../language-reference/builtin-types/default-values.md) 一文所列。</span><span class="sxs-lookup"><span data-stu-id="7c13a-110">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span> <span data-ttu-id="7c13a-111">如果您未提供結構的函式，c # 會依賴 *隱含無參數* 的函式，將每個欄位自動初始化為其預設值。</span><span class="sxs-lookup"><span data-stu-id="7c13a-111">If you don't provide a constructor for your struct, C# relies on an *implicit parameterless constructor* to automatically initialize each field to its default value.</span></span> <span data-ttu-id="7c13a-112">如需詳細資訊和範例，請參閱 [實例](instance-constructors.md)的函式。</span><span class="sxs-lookup"><span data-stu-id="7c13a-112">For more information and examples, see [Instance constructors](instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="7c13a-113">建構函式語法</span><span class="sxs-lookup"><span data-stu-id="7c13a-113">Constructor syntax</span></span>

<span data-ttu-id="7c13a-114">建構函式是名稱與其類型名稱相同的方法。</span><span class="sxs-lookup"><span data-stu-id="7c13a-114">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="7c13a-115">其方法簽章只包含方法名稱及其參數清單，不包含傳回的類型。</span><span class="sxs-lookup"><span data-stu-id="7c13a-115">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="7c13a-116">下例示範名為 `Person` 的類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="7c13a-116">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="7c13a-117">如果建構函式可以實作為單一陳述式，您就可以使用[運算式主體定義](../statements-expressions-operators/expression-bodied-members.md)。</span><span class="sxs-lookup"><span data-stu-id="7c13a-117">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="7c13a-118">下列範例定義 `Location` 類別，這個類別的建構函式包含名為 *name* 的單一字串參數。</span><span class="sxs-lookup"><span data-stu-id="7c13a-118">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="7c13a-119">運算式主體定義會將引數指派給 `locationName` 欄位。</span><span class="sxs-lookup"><span data-stu-id="7c13a-119">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="7c13a-120">靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="7c13a-120">Static constructors</span></span>

<span data-ttu-id="7c13a-121">前例都已顯示建立新物件的執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="7c13a-121">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="7c13a-122">類別或結構也可以有靜態建構函式，用來初始化類型的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="7c13a-122">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="7c13a-123">靜態建構函式無參數。</span><span class="sxs-lookup"><span data-stu-id="7c13a-123">Static constructors are parameterless.</span></span> <span data-ttu-id="7c13a-124">如果您未提供靜態的函式來初始化靜態欄位，c # 編譯器會將靜態欄位初始化為其預設值，如 [c # 類型的預設值一](../../language-reference/builtin-types/default-values.md) 文所列。</span><span class="sxs-lookup"><span data-stu-id="7c13a-124">If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span>

<span data-ttu-id="7c13a-125">下列範例會使用靜態建構函式來初始化靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="7c13a-125">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="7c13a-126">您也可以使用運算式主體定義來定義靜態建構函式，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="7c13a-126">You can also define a static constructor with an expression body definition, as the following example shows.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="7c13a-127">如需詳細資訊及範例，請參閱[靜態建構函式](./static-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="7c13a-127">For more information and examples, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c13a-128">本節內容</span><span class="sxs-lookup"><span data-stu-id="7c13a-128">In This Section</span></span>  
 [<span data-ttu-id="7c13a-129">使用建構函式</span><span class="sxs-lookup"><span data-stu-id="7c13a-129">Using Constructors</span></span>](./using-constructors.md)  
  
 [<span data-ttu-id="7c13a-130">執行個體建構函式</span><span class="sxs-lookup"><span data-stu-id="7c13a-130">Instance Constructors</span></span>](./instance-constructors.md)  
  
 [<span data-ttu-id="7c13a-131">私用建構函式</span><span class="sxs-lookup"><span data-stu-id="7c13a-131">Private Constructors</span></span>](./private-constructors.md)  
  
 [<span data-ttu-id="7c13a-132">靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="7c13a-132">Static Constructors</span></span>](./static-constructors.md)  
  
 [<span data-ttu-id="7c13a-133">如何撰寫複製建構函式</span><span class="sxs-lookup"><span data-stu-id="7c13a-133">How to write a copy constructor</span></span>](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="7c13a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c13a-134">See also</span></span>

- [<span data-ttu-id="7c13a-135">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="7c13a-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7c13a-136">類別和結構</span><span class="sxs-lookup"><span data-stu-id="7c13a-136">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="7c13a-137">完成項</span><span class="sxs-lookup"><span data-stu-id="7c13a-137">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="7c13a-138">static</span><span class="sxs-lookup"><span data-stu-id="7c13a-138">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="7c13a-139">為什麼初始化運算式的執行順序與處理函式相反？第一部</span><span class="sxs-lookup"><span data-stu-id="7c13a-139">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
