---
title: "欄位 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
caps.latest.revision: 29
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
ms.openlocfilehash: 8eef9bb644a28c69a1db59dcba3c12c9e3fa86b0
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="fields-c-programming-guide"></a><span data-ttu-id="e8561-102">欄位 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="e8561-102">Fields (C# Programming Guide)</span></span>
<span data-ttu-id="e8561-103">「欄位」是任意類型的變數，可在[類別](../../../csharp/language-reference/keywords/class.md)或[結構](../../../csharp/language-reference/keywords/struct.md)中直接宣告。</span><span class="sxs-lookup"><span data-stu-id="e8561-103">A *field* is a variable of any type that is declared directly in a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md).</span></span> <span data-ttu-id="e8561-104">欄位是其包含類型的「成員」。</span><span class="sxs-lookup"><span data-stu-id="e8561-104">Fields are *members* of their containing type.</span></span>  
  
 <span data-ttu-id="e8561-105">類別或結構可能會有執行個體欄位或靜態欄位，或者兩者都有。</span><span class="sxs-lookup"><span data-stu-id="e8561-105">A class or struct may have instance fields or static fields or both.</span></span> <span data-ttu-id="e8561-106">執行個體欄位是專屬於某種類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e8561-106">Instance fields are specific to an instance of a type.</span></span> <span data-ttu-id="e8561-107">如果您有搭配執行個體欄位 F 的類別 T，您可以建立兩個類型 T 的物件，然後修改每個物件中的 F 值，而不會影響另一個物件中的值。</span><span class="sxs-lookup"><span data-stu-id="e8561-107">If you have a class T, with an instance field F, you can create two objects of type T, and modify the value of F in each object without affecting the value in the other object.</span></span> <span data-ttu-id="e8561-108">相較之下，靜態欄位屬類別本身所擁有，並在該類別的所有執行個體之間共用。</span><span class="sxs-lookup"><span data-stu-id="e8561-108">By contrast, a static field belongs to the class itself, and is shared among all instances of that class.</span></span> <span data-ttu-id="e8561-109">對執行個體 A 所做的變更，執行個體 B 和 C 只要存取該欄位就會立即看到。</span><span class="sxs-lookup"><span data-stu-id="e8561-109">Changes made from instance A will be visibly immediately to instances B and C if they access the field.</span></span>  
  
 <span data-ttu-id="e8561-110">一般而言，您應該只針對具有 private 或 protected 存取範圍的變數使用欄位。</span><span class="sxs-lookup"><span data-stu-id="e8561-110">Generally, you should use fields only for variables that have private or protected accessibility.</span></span> <span data-ttu-id="e8561-111">您的類別公開給用戶端程式碼的資料應透過[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)、[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)和[索引子](../../../csharp/programming-guide/indexers/index.md)來提供。</span><span class="sxs-lookup"><span data-stu-id="e8561-111">Data that your class exposes to client code should be provided through [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md) and [indexers](../../../csharp/programming-guide/indexers/index.md).</span></span> <span data-ttu-id="e8561-112">藉由使用這些建構來間接存取內部欄位，即可防範無效的輸入值。</span><span class="sxs-lookup"><span data-stu-id="e8561-112">By using these constructs for indirect access to internal fields, you can guard against invalid input values.</span></span> <span data-ttu-id="e8561-113">儲存由公用屬性公開之資料的私用欄位稱為「備份存放區」或「支援欄位」。</span><span class="sxs-lookup"><span data-stu-id="e8561-113">A private field that stores the data exposed by a public property is called a *backing store* or *backing field*.</span></span>  
  
 <span data-ttu-id="e8561-114">這些欄位通常會儲存必須可供多個類別方法存取的資料，以及其儲存時間必須比任何一個方法的存留期都還要長的資料。</span><span class="sxs-lookup"><span data-stu-id="e8561-114">Fields typically store the data that must be accessible to more than one class method and must be stored for longer than the lifetime of any single method.</span></span> <span data-ttu-id="e8561-115">例如，表示行事曆日期的類別可能會有三個整數欄位，分別代表月、日和年。</span><span class="sxs-lookup"><span data-stu-id="e8561-115">For example, a class that represents a calendar date might have three integer fields: one for the month, one for the day, and one for the year.</span></span> <span data-ttu-id="e8561-116">未在單一方法以外範圍使用的變數，應在方法主體本身內宣告為「區域變數」。</span><span class="sxs-lookup"><span data-stu-id="e8561-116">Variables that are not used outside the scope of a single method should be declared as *local variables* within the method body itself.</span></span>  
  
 <span data-ttu-id="e8561-117">請依序指定欄位的存取層級、欄位的類型和欄位的名稱，以在類別區塊中宣告欄位。</span><span class="sxs-lookup"><span data-stu-id="e8561-117">Fields are declared in the class block by specifying the access level of the field, followed by the type of the field, followed by the name of the field.</span></span> <span data-ttu-id="e8561-118">例如: </span><span class="sxs-lookup"><span data-stu-id="e8561-118">For example:</span></span>  
  
 <span data-ttu-id="e8561-119">[!code-cs[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e8561-119">[!code-cs[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_1.cs)]</span></span>  
  
 <span data-ttu-id="e8561-120">若要存取物件中的欄位，請在物件名稱後面加上句號，再加上欄位的名稱，就像是 `objectname.fieldname`。</span><span class="sxs-lookup"><span data-stu-id="e8561-120">To access a field in an object, add a period after the object name, followed by the name of the field, as in `objectname.fieldname`.</span></span> <span data-ttu-id="e8561-121">例如: </span><span class="sxs-lookup"><span data-stu-id="e8561-121">For example:</span></span>  
  
 <span data-ttu-id="e8561-122">[!code-cs[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="e8561-122">[!code-cs[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_2.cs)]</span></span>  
  
 <span data-ttu-id="e8561-123">您可以在宣告欄位時，使用指派運算子來指定欄位的初始值。</span><span class="sxs-lookup"><span data-stu-id="e8561-123">A field can be given an initial value by using the assignment operator when the field is declared.</span></span> <span data-ttu-id="e8561-124">例如，若要將 `day` 欄位自動指派為 `"Monday"`，您可以如下列範例所示宣告 `day`：</span><span class="sxs-lookup"><span data-stu-id="e8561-124">To automatically assign the `day` field to `"Monday"`, for example, you would declare `day` as in the following example:</span></span>  
  
 <span data-ttu-id="e8561-125">[!code-cs[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="e8561-125">[!code-cs[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_3.cs)]</span></span>  
  
 <span data-ttu-id="e8561-126">欄位會在呼叫物件執行個體的建構函式之前立即初始化。</span><span class="sxs-lookup"><span data-stu-id="e8561-126">Fields are initialized immediately before the constructor for the object instance is called.</span></span> <span data-ttu-id="e8561-127">如果建構函式指派了欄位的值，該值會覆寫欄位宣告期間所指定的任何值。</span><span class="sxs-lookup"><span data-stu-id="e8561-127">If the constructor assigns the value of a field, it will overwrite any value given during field declaration.</span></span> <span data-ttu-id="e8561-128">如需詳細資訊，請參閱[使用建構函式](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="e8561-128">For more information, see [Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8561-129">欄位初始設定式無法參考其他執行個體欄位。</span><span class="sxs-lookup"><span data-stu-id="e8561-129">A field initializer cannot refer to other instance fields.</span></span>  
  
 <span data-ttu-id="e8561-130">欄位可以標記為 [public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md) 或 `protected internal`。</span><span class="sxs-lookup"><span data-stu-id="e8561-130">Fields can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or `protected internal`.</span></span> <span data-ttu-id="e8561-131">這些存取修飾詞定義類別使用者如何存取欄位。</span><span class="sxs-lookup"><span data-stu-id="e8561-131">These access modifiers define how users of the class can access the fields.</span></span> <span data-ttu-id="e8561-132">如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="e8561-132">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="e8561-133">欄位可以選擇性地宣告為 [static](../../../csharp/language-reference/keywords/static.md)。</span><span class="sxs-lookup"><span data-stu-id="e8561-133">A field can optionally be declared [static](../../../csharp/language-reference/keywords/static.md).</span></span> <span data-ttu-id="e8561-134">這可隨時向呼叫者提供欄位，即使沒有任何類別執行個體存在。</span><span class="sxs-lookup"><span data-stu-id="e8561-134">This makes the field available to callers at any time, even if no instance of the class exists.</span></span> <span data-ttu-id="e8561-135">如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="e8561-135">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="e8561-136">欄位可以宣告為 [readonly](../../../csharp/language-reference/keywords/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="e8561-136">A field can be declared [readonly](../../../csharp/language-reference/keywords/readonly.md).</span></span> <span data-ttu-id="e8561-137">您只能在初始化期間或在建構函式中指派值給唯讀欄位。</span><span class="sxs-lookup"><span data-stu-id="e8561-137">A read-only field can only be assigned a value during initialization or in a constructor.</span></span> <span data-ttu-id="e8561-138">`static``readonly` 欄位非常類似於常數，不同之處在於 C# 編譯器無法在編譯時期存取靜態唯讀欄位的值，只有在執行階段才能這麼做。</span><span class="sxs-lookup"><span data-stu-id="e8561-138">A `static``readonly` field is very similar to a constant, except that the C# compiler does not have access to the value of a static read-only field at compile time, only at run time.</span></span> <span data-ttu-id="e8561-139">如需詳細資訊，請參閱[常數](../../../csharp/programming-guide/classes-and-structs/constants.md)。</span><span class="sxs-lookup"><span data-stu-id="e8561-139">For more information, see [Constants](../../../csharp/programming-guide/classes-and-structs/constants.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e8561-140">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e8561-140">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e8561-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8561-141">See Also</span></span>  
 <span data-ttu-id="e8561-142">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e8561-142">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e8561-143">[類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="e8561-143">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="e8561-144">[使用建構函式](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) </span><span class="sxs-lookup"><span data-stu-id="e8561-144">[Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) </span></span>  
 <span data-ttu-id="e8561-145">[繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span><span class="sxs-lookup"><span data-stu-id="e8561-145">[Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md) </span></span>  
 <span data-ttu-id="e8561-146">[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="e8561-146">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 [<span data-ttu-id="e8561-147">抽象和密封類別以及類別成員</span><span class="sxs-lookup"><span data-stu-id="e8561-147">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)

