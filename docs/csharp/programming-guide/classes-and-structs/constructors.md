---
title: 建構函式 (C# 程式設計手冊)
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 3d07fe5f6164885a994838376887edccc260e291
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44185333"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="165cf-102">建構函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="165cf-102">Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="165cf-103">每當建立[類別](../../../csharp/language-reference/keywords/class.md)或[結構](../../../csharp/language-reference/keywords/struct.md)時，都會呼叫其建構函式。</span><span class="sxs-lookup"><span data-stu-id="165cf-103">Whenever a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="165cf-104">類別或結構可有使用不同引數的多個建構函式。</span><span class="sxs-lookup"><span data-stu-id="165cf-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="165cf-105">建構函式能讓程式設計師可以設定預設值、限制具現化，以及撰寫彈性且容易閱讀的程式碼。</span><span class="sxs-lookup"><span data-stu-id="165cf-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="165cf-106">如需詳細資訊和範例，請參閱[使用建構函式](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)和[執行個體建構函式](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="165cf-106">For more information and examples, see [Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) and [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="default-constructors"></a><span data-ttu-id="165cf-107">預設建構函式</span><span class="sxs-lookup"><span data-stu-id="165cf-107">Default constructors</span></span>
  
<span data-ttu-id="165cf-108">如不提供類別的建構函式，C# 預設會建立一個可具現化物件的建構函式，並將成員變數設定為預設值，如[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)中所列。</span><span class="sxs-lookup"><span data-stu-id="165cf-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="165cf-109">如不提供結構的建構函式，C# 會回覆「隱含的預設建構函式」，自動將實值型別的每個欄位初始化為其預設值，如[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)中所列。</span><span class="sxs-lookup"><span data-stu-id="165cf-109">If you don't provide a constructor for your struct, C# relies on an *implicit default constructor* to automatically initialize each field of a value type to its default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="165cf-110">如需詳細資訊及範例，請參閱[執行個體建構函式](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="165cf-110">For more information and examples, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="165cf-111">建構函式語法</span><span class="sxs-lookup"><span data-stu-id="165cf-111">Constructor syntax</span></span>

<span data-ttu-id="165cf-112">建構函式是名稱與其類型名稱相同的方法。</span><span class="sxs-lookup"><span data-stu-id="165cf-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="165cf-113">其方法簽章只包含方法名稱及其參數清單，不包含傳回的類型。</span><span class="sxs-lookup"><span data-stu-id="165cf-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="165cf-114">下例示範名為 `Person` 的類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="165cf-114">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="165cf-115">如果建構函式可以實作為單一陳述式，您就可以使用[運算式主體定義](../statements-expressions-operators/expression-bodied-members.md)。</span><span class="sxs-lookup"><span data-stu-id="165cf-115">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="165cf-116">下列範例定義 `Location` 類別，這個類別的建構函式包含名為 *name* 的單一字串參數。</span><span class="sxs-lookup"><span data-stu-id="165cf-116">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="165cf-117">運算式主體定義會將引數指派給 `locationName` 欄位。</span><span class="sxs-lookup"><span data-stu-id="165cf-117">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="165cf-118">靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="165cf-118">Static constructors</span></span>

<span data-ttu-id="165cf-119">前例都已顯示建立新物件的執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="165cf-119">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="165cf-120">類別或結構也可以有靜態建構函式，用來初始化類型的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="165cf-120">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="165cf-121">靜態建構函式無參數。</span><span class="sxs-lookup"><span data-stu-id="165cf-121">Static constructors are parameterless.</span></span> <span data-ttu-id="165cf-122">如不提供靜態建構函式來初始化靜態欄位，C# 編譯器會提供預設的靜態建構函式，將靜態欄位初始化為其預設值，如[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)中所列。</span><span class="sxs-lookup"><span data-stu-id="165cf-122">If you don't provide a static constructor to initialize static fields, the C# compiler will supply a default static constructor that initializes static fields to their default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> 

<span data-ttu-id="165cf-123">下列範例會使用靜態建構函式來初始化靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="165cf-123">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="165cf-124">您也可以使用運算式主體定義來定義靜態建構函式，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="165cf-124">You can also define a static constructor with an expression body definition, as the following example shows.</span></span> 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="165cf-125">如需詳細資訊及範例，請參閱[靜態建構函式](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="165cf-125">For more information and examples, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="165cf-126">本節內容</span><span class="sxs-lookup"><span data-stu-id="165cf-126">In This Section</span></span>  
 [<span data-ttu-id="165cf-127">使用建構函式</span><span class="sxs-lookup"><span data-stu-id="165cf-127">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [<span data-ttu-id="165cf-128">執行個體建構函式</span><span class="sxs-lookup"><span data-stu-id="165cf-128">Instance Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [<span data-ttu-id="165cf-129">私用建構函式</span><span class="sxs-lookup"><span data-stu-id="165cf-129">Private Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [<span data-ttu-id="165cf-130">靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="165cf-130">Static Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [<span data-ttu-id="165cf-131">如何：撰寫複製建構函式</span><span class="sxs-lookup"><span data-stu-id="165cf-131">How to: Write a Copy Constructor</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="165cf-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="165cf-132">See Also</span></span>

- [<span data-ttu-id="165cf-133">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="165cf-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="165cf-134">類別和結構</span><span class="sxs-lookup"><span data-stu-id="165cf-134">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="165cf-135">完成項</span><span class="sxs-lookup"><span data-stu-id="165cf-135">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
- [<span data-ttu-id="165cf-136">static</span><span class="sxs-lookup"><span data-stu-id="165cf-136">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
- [<span data-ttu-id="165cf-137">為什麼初始設定式執行的順序與建構函式相反？第一部</span><span class="sxs-lookup"><span data-stu-id="165cf-137">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
