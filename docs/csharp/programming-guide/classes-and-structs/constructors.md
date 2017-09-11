---
title: "建構函式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2017-05-05
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: 064d8f8b3068596cd1d4fc2dd073f165f0ebadcb
ms.contentlocale: zh-tw
ms.lasthandoff: 05/15/2017

---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="b397c-102">建構函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="b397c-102">Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="b397c-103">每當建立[類別](../../../csharp/language-reference/keywords/class.md)或[結構](../../../csharp/language-reference/keywords/struct.md)時，都會呼叫其建構函式。</span><span class="sxs-lookup"><span data-stu-id="b397c-103">Whenever a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="b397c-104">類別或結構可有使用不同引數的多個建構函式。</span><span class="sxs-lookup"><span data-stu-id="b397c-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="b397c-105">建構函式能讓程式設計師可以設定預設值、限制具現化，以及撰寫彈性且容易閱讀的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b397c-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="b397c-106">如需詳細資訊和範例，請參閱[使用建構函式](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)和[執行個體建構函式](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="b397c-106">For more information and examples, see [Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) and [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="default-constructors"></a><span data-ttu-id="b397c-107">預設建構函式</span><span class="sxs-lookup"><span data-stu-id="b397c-107">Default constructors</span></span>
  
<span data-ttu-id="b397c-108">如不提供類別的建構函式，C# 預設會建立一個可具現化物件的建構函式，並將成員變數設定為預設值，如[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)中所列。</span><span class="sxs-lookup"><span data-stu-id="b397c-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="b397c-109">如不提供結構的建構函式，C# 會回覆「隱含的預設建構函式」，自動將實值型別的每個欄位初始化為其預設值，如[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)中所列。</span><span class="sxs-lookup"><span data-stu-id="b397c-109">If you don't provide a constructor for your struct, C# replies on an *implicit default constructor* to automatically initialize each field of a value type to its default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="b397c-110">如需詳細資訊及範例，請參閱[執行個體建構函式](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="b397c-110">For more information and examples, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="b397c-111">建構函式語法</span><span class="sxs-lookup"><span data-stu-id="b397c-111">Constructor syntax</span></span>

<span data-ttu-id="b397c-112">建構函式是名稱與其類型名稱相同的方法。</span><span class="sxs-lookup"><span data-stu-id="b397c-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="b397c-113">其方法簽章只包含方法名稱及其參數清單，不包含傳回的類型。</span><span class="sxs-lookup"><span data-stu-id="b397c-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="b397c-114">下例示範名為 `Person` 的類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="b397c-114">The following example shows the constructor for a class named `Person`.</span></span>

<span data-ttu-id="b397c-115">[!code-cs[建構函式](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="b397c-115">[!code-cs[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]</span></span>  

<span data-ttu-id="b397c-116">如果建構函式可以實作為單一陳述式，您就可以使用[運算式主體定義](../statements-expressions-operators/expression-bodied-members.md)。</span><span class="sxs-lookup"><span data-stu-id="b397c-116">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="b397c-117">下列範例定義 `Location` 類別，這個類別的建構函式包含名為 *name* 的單一字串參數。</span><span class="sxs-lookup"><span data-stu-id="b397c-117">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="b397c-118">運算式主體定義會將引數指派給 `Name` 屬性。</span><span class="sxs-lookup"><span data-stu-id="b397c-118">The expression body definition assigns the argument to the `Name` property.</span></span>

<span data-ttu-id="b397c-119">[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="b397c-119">[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]</span></span>  

## <a name="static-constructors"></a><span data-ttu-id="b397c-120">靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="b397c-120">Static constructors</span></span>

<span data-ttu-id="b397c-121">前例都已顯示建立新物件的執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="b397c-121">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="b397c-122">類別或結構也可以有靜態建構函式，用來初始化類型的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="b397c-122">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="b397c-123">靜態建構函式無參數。</span><span class="sxs-lookup"><span data-stu-id="b397c-123">Static constructors are parameterless.</span></span> <span data-ttu-id="b397c-124">如不提供靜態建構函式來初始化靜態欄位，C# 編譯器會提供預設的靜態建構函式，將欄位初始化為其預設值，如[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)中所列。</span><span class="sxs-lookup"><span data-stu-id="b397c-124">If you don't provide a static constructor to initialize static fields, the C# compiler will supply a default static constructor that initializes fields to their default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> 

<span data-ttu-id="b397c-125">下列範例會使用靜態建構函式來初始化靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="b397c-125">The following example uses a static constructor to initialize a static field.</span></span>

<span data-ttu-id="b397c-126">[!code-cs[建構函式](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="b397c-126">[!code-cs[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]</span></span>  

<span data-ttu-id="b397c-127">您也可以使用運算式主體定義來定義靜態建構函式，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="b397c-127">You can also define a static constructor with an expression body definition, as the following example shows.</span></span> 

<span data-ttu-id="b397c-128">[!code-cs[建構函式](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]</span><span class="sxs-lookup"><span data-stu-id="b397c-128">[!code-cs[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]</span></span>  

<span data-ttu-id="b397c-129">如需詳細資訊及範例，請參閱[靜態建構函式](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="b397c-129">For more information and examples, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b397c-130">本章節內容</span><span class="sxs-lookup"><span data-stu-id="b397c-130">In This Section</span></span>  
 [<span data-ttu-id="b397c-131">使用建構函式</span><span class="sxs-lookup"><span data-stu-id="b397c-131">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [<span data-ttu-id="b397c-132">執行個體建構函式</span><span class="sxs-lookup"><span data-stu-id="b397c-132">Instance Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [<span data-ttu-id="b397c-133">私用建構函式</span><span class="sxs-lookup"><span data-stu-id="b397c-133">Private Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [<span data-ttu-id="b397c-134">靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="b397c-134">Static Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [<span data-ttu-id="b397c-135">如何：撰寫複製建構函式</span><span class="sxs-lookup"><span data-stu-id="b397c-135">How to: Write a Copy Constructor</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="b397c-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b397c-136">See Also</span></span>  
 <span data-ttu-id="b397c-137">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b397c-137">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="b397c-138"> [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="b397c-138"> [Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
<span data-ttu-id="b397c-139"> [完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span><span class="sxs-lookup"><span data-stu-id="b397c-139"> [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span></span>  
<span data-ttu-id="b397c-140"> [static](../../../csharp/language-reference/keywords/static.md) </span><span class="sxs-lookup"><span data-stu-id="b397c-140"> [static](../../../csharp/language-reference/keywords/static.md) </span></span>  
<span data-ttu-id="b397c-141"> [為什麼初始設定式執行的順序與建構函式相反？第一部](http://go.microsoft.com/fwlink/?LinkId=112374)</span><span class="sxs-lookup"><span data-stu-id="b397c-141"> [Why Do Initializers Run In The Opposite Order As Constructors? Part One](http://go.microsoft.com/fwlink/?LinkId=112374)</span></span>
