---
title: 建構函式 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: ea780fc983ed46c8a5ccb54ab618d1a0a2a928d1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597097"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="9ec70-102">建構函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="9ec70-102">Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="9ec70-103">每當建立[類別](../../language-reference/keywords/class.md)或[結構](../../language-reference/keywords/struct.md)時，都會呼叫其建構函式。</span><span class="sxs-lookup"><span data-stu-id="9ec70-103">Whenever a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="9ec70-104">類別或結構可有使用不同引數的多個建構函式。</span><span class="sxs-lookup"><span data-stu-id="9ec70-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="9ec70-105">建構函式能讓程式設計師可以設定預設值、限制具現化，以及撰寫彈性且容易閱讀的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9ec70-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="9ec70-106">如需詳細資訊和範例，請參閱[使用建構函式](./using-constructors.md)和[執行個體建構函式](./instance-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="9ec70-106">For more information and examples, see [Using Constructors](./using-constructors.md) and [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="parameterless-constructors"></a><span data-ttu-id="9ec70-107">無參數建構函式</span><span class="sxs-lookup"><span data-stu-id="9ec70-107">Parameterless constructors</span></span>
  
<span data-ttu-id="9ec70-108">如不提供類別的建構函式，C# 預設會建立一個可具現化物件的建構函式，並將成員變數設定為預設值，如[預設值表](../../language-reference/keywords/default-values-table.md)中所列。</span><span class="sxs-lookup"><span data-stu-id="9ec70-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default Values Table](../../language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="9ec70-109">若未提供結構的建構函式，C# 會依賴「隱含無參數建構函式」  來自動將實值型別的每個欄位初始化為其預設值，如[預設值表](../../language-reference/keywords/default-values-table.md)中所列。</span><span class="sxs-lookup"><span data-stu-id="9ec70-109">If you don't provide a constructor for your struct, C# relies on an *implicit parameterless constructor* to automatically initialize each field of a value type to its default value as listed in the [Default Values Table](../../language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="9ec70-110">如需詳細資訊及範例，請參閱[執行個體建構函式](./instance-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="9ec70-110">For more information and examples, see [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="9ec70-111">建構函式語法</span><span class="sxs-lookup"><span data-stu-id="9ec70-111">Constructor syntax</span></span>

<span data-ttu-id="9ec70-112">建構函式是名稱與其類型名稱相同的方法。</span><span class="sxs-lookup"><span data-stu-id="9ec70-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="9ec70-113">其方法簽章只包含方法名稱及其參數清單，不包含傳回的類型。</span><span class="sxs-lookup"><span data-stu-id="9ec70-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="9ec70-114">下例示範名為 `Person` 的類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="9ec70-114">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="9ec70-115">如果建構函式可以實作為單一陳述式，您就可以使用[運算式主體定義](../statements-expressions-operators/expression-bodied-members.md)。</span><span class="sxs-lookup"><span data-stu-id="9ec70-115">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="9ec70-116">下列範例定義 `Location` 類別，這個類別的建構函式包含名為 *name* 的單一字串參數。</span><span class="sxs-lookup"><span data-stu-id="9ec70-116">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="9ec70-117">運算式主體定義會將引數指派給 `locationName` 欄位。</span><span class="sxs-lookup"><span data-stu-id="9ec70-117">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="9ec70-118">靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="9ec70-118">Static constructors</span></span>

<span data-ttu-id="9ec70-119">前例都已顯示建立新物件的執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="9ec70-119">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="9ec70-120">類別或結構也可以有靜態建構函式，用來初始化類型的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="9ec70-120">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="9ec70-121">靜態建構函式無參數。</span><span class="sxs-lookup"><span data-stu-id="9ec70-121">Static constructors are parameterless.</span></span> <span data-ttu-id="9ec70-122">若您未提供靜態建構函式來初始化靜態欄位，C# 編譯器會將靜態欄位初始化為其預設值，如[預設值表](../../language-reference/keywords/default-values-table.md)中所列。</span><span class="sxs-lookup"><span data-stu-id="9ec70-122">If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value as listed in the [Default Values Table](../../language-reference/keywords/default-values-table.md).</span></span>

<span data-ttu-id="9ec70-123">下列範例會使用靜態建構函式來初始化靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="9ec70-123">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="9ec70-124">您也可以使用運算式主體定義來定義靜態建構函式，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="9ec70-124">You can also define a static constructor with an expression body definition, as the following example shows.</span></span> 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="9ec70-125">如需詳細資訊及範例，請參閱[靜態建構函式](./static-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="9ec70-125">For more information and examples, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ec70-126">本節內容</span><span class="sxs-lookup"><span data-stu-id="9ec70-126">In This Section</span></span>  
 [<span data-ttu-id="9ec70-127">使用建構函式</span><span class="sxs-lookup"><span data-stu-id="9ec70-127">Using Constructors</span></span>](./using-constructors.md)  
  
 [<span data-ttu-id="9ec70-128">執行個體建構函式</span><span class="sxs-lookup"><span data-stu-id="9ec70-128">Instance Constructors</span></span>](./instance-constructors.md)  
  
 [<span data-ttu-id="9ec70-129">私用建構函式</span><span class="sxs-lookup"><span data-stu-id="9ec70-129">Private Constructors</span></span>](./private-constructors.md)  
  
 [<span data-ttu-id="9ec70-130">靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="9ec70-130">Static Constructors</span></span>](./static-constructors.md)  
  
 [<span data-ttu-id="9ec70-131">如何：撰寫複製建構函式</span><span class="sxs-lookup"><span data-stu-id="9ec70-131">How to: Write a Copy Constructor</span></span>](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="9ec70-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ec70-132">See also</span></span>

- [<span data-ttu-id="9ec70-133">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="9ec70-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9ec70-134">類別和結構</span><span class="sxs-lookup"><span data-stu-id="9ec70-134">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="9ec70-135">完成項</span><span class="sxs-lookup"><span data-stu-id="9ec70-135">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="9ec70-136">static</span><span class="sxs-lookup"><span data-stu-id="9ec70-136">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="9ec70-137">為什麼初始設定式執行的順序與建構函式相反？第一部</span><span class="sxs-lookup"><span data-stu-id="9ec70-137">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
