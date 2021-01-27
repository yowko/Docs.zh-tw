---
title: 欄位 - C# 程式設計手冊
description: 'C # 中的欄位是直接在類別或結構中宣告之任何類型的變數。 欄位是其包含類型的「成員」。'
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: 58e60e1dc0b574ae922e6a27a22978b91aca4ec4
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899044"
---
# <a name="fields-c-programming-guide"></a><span data-ttu-id="1e0c9-104">欄位 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="1e0c9-104">Fields (C# Programming Guide)</span></span>

<span data-ttu-id="1e0c9-105">「欄位」是任意類型的變數，可在[類別](../../language-reference/keywords/class.md)或[結構](../../language-reference/builtin-types/struct.md)中直接宣告。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-105">A *field* is a variable of any type that is declared directly in a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md).</span></span> <span data-ttu-id="1e0c9-106">欄位是其包含類型的「成員」。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-106">Fields are *members* of their containing type.</span></span>

<span data-ttu-id="1e0c9-107">類別或結構可能具有實例欄位、靜態欄位或兩者。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-107">A class or struct may have instance fields, static fields, or both.</span></span> <span data-ttu-id="1e0c9-108">執行個體欄位是專屬於某種類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-108">Instance fields are specific to an instance of a type.</span></span> <span data-ttu-id="1e0c9-109">如果您有搭配執行個體欄位 F 的類別 T，您可以建立兩個類型 T 的物件，然後修改每個物件中的 F 值，而不會影響另一個物件中的值。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-109">If you have a class T, with an instance field F, you can create two objects of type T, and modify the value of F in each object without affecting the value in the other object.</span></span> <span data-ttu-id="1e0c9-110">相較之下，靜態欄位屬類別本身所擁有，並在該類別的所有執行個體之間共用。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-110">By contrast, a static field belongs to the class itself, and is shared among all instances of that class.</span></span> <span data-ttu-id="1e0c9-111">您只能使用類別名稱來存取靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-111">You can access the static field only by using the class name.</span></span> <span data-ttu-id="1e0c9-112">如果您以實例名稱存取靜態欄位，就會收到 [CS0176](../../misc/cs0176.md) 的編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-112">If you access the static field by an instance name, you get [CS0176](../../misc/cs0176.md) compile-time error.</span></span>

<span data-ttu-id="1e0c9-113">一般而言，您應該只針對具有 private 或 protected 存取範圍的變數使用欄位。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-113">Generally, you should use fields only for variables that have private or protected accessibility.</span></span> <span data-ttu-id="1e0c9-114">您的類別公開給用戶端程式代碼的資料應該透過 [方法](./methods.md)、 [屬性](./properties.md)和 [索引子](../indexers/index.md)提供。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-114">Data that your class exposes to client code should be provided through [methods](./methods.md), [properties](./properties.md), and [indexers](../indexers/index.md).</span></span> <span data-ttu-id="1e0c9-115">藉由使用這些建構來間接存取內部欄位，即可防範無效的輸入值。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-115">By using these constructs for indirect access to internal fields, you can guard against invalid input values.</span></span> <span data-ttu-id="1e0c9-116">儲存由公用屬性公開之資料的私用欄位稱為「備份存放區」或「支援欄位」。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-116">A private field that stores the data exposed by a public property is called a *backing store* or *backing field*.</span></span>

<span data-ttu-id="1e0c9-117">這些欄位通常會儲存必須可供多個類別方法存取的資料，以及其儲存時間必須比任何一個方法的存留期都還要長的資料。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-117">Fields typically store the data that must be accessible to more than one class method and must be stored for longer than the lifetime of any single method.</span></span> <span data-ttu-id="1e0c9-118">例如，表示行事曆日期的類別可能會有三個整數欄位，分別代表月、日和年。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-118">For example, a class that represents a calendar date might have three integer fields: one for the month, one for the day, and one for the year.</span></span> <span data-ttu-id="1e0c9-119">未在單一方法以外範圍使用的變數，應在方法主體本身內宣告為「區域變數」。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-119">Variables that are not used outside the scope of a single method should be declared as *local variables* within the method body itself.</span></span>

<span data-ttu-id="1e0c9-120">請依序指定欄位的存取層級、欄位的類型和欄位的名稱，以在類別區塊中宣告欄位。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-120">Fields are declared in the class block by specifying the access level of the field, followed by the type of the field, followed by the name of the field.</span></span> <span data-ttu-id="1e0c9-121">例如：</span><span class="sxs-lookup"><span data-stu-id="1e0c9-121">For example:</span></span>

[!code-csharp[fields#1](snippets/fields/Program.cs#1)]

<span data-ttu-id="1e0c9-122">若要存取物件中的欄位，請在物件名稱後面加上句號，再加上欄位的名稱，就像是 `objectname.fieldname`。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-122">To access a field in an object, add a period after the object name, followed by the name of the field, as in `objectname.fieldname`.</span></span> <span data-ttu-id="1e0c9-123">例如：</span><span class="sxs-lookup"><span data-stu-id="1e0c9-123">For example:</span></span>

[!code-csharp[fields#2](snippets/fields/Program.cs#2)]

<span data-ttu-id="1e0c9-124">您可以在宣告欄位時，使用指派運算子來指定欄位的初始值。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-124">A field can be given an initial value by using the assignment operator when the field is declared.</span></span> <span data-ttu-id="1e0c9-125">例如，若要將 `day` 欄位自動指派為 `"Monday"`，您可以如下列範例所示宣告 `day`：</span><span class="sxs-lookup"><span data-stu-id="1e0c9-125">To automatically assign the `day` field to `"Monday"`, for example, you would declare `day` as in the following example:</span></span>

[!code-csharp[fields#3](snippets/fields/Program.cs#3)]

<span data-ttu-id="1e0c9-126">欄位會在呼叫物件執行個體的建構函式之前立即初始化。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-126">Fields are initialized immediately before the constructor for the object instance is called.</span></span> <span data-ttu-id="1e0c9-127">如果建構函式指派了欄位的值，該值會覆寫欄位宣告期間所指定的任何值。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-127">If the constructor assigns the value of a field, it will overwrite any value given during field declaration.</span></span> <span data-ttu-id="1e0c9-128">如需詳細資訊，請參閱[使用建構函式](./using-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-128">For more information, see [Using Constructors](./using-constructors.md).</span></span>

> [!NOTE]
> <span data-ttu-id="1e0c9-129">欄位初始設定式無法參考其他執行個體欄位。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-129">A field initializer cannot refer to other instance fields.</span></span>

<span data-ttu-id="1e0c9-130">欄位可以標示為 [public](../../language-reference/keywords/public.md)、 [private](../../language-reference/keywords/private.md)、 [protected](../../language-reference/keywords/protected.md)、 [internal](../../language-reference/keywords/internal.md)、 [protected internal](../../language-reference/keywords/protected-internal.md)或 [private protected](../../language-reference/keywords/private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-130">Fields can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="1e0c9-131">這些存取修飾詞定義類別使用者如何存取欄位。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-131">These access modifiers define how users of the class can access the fields.</span></span> <span data-ttu-id="1e0c9-132">如需詳細資訊，請參閱[存取修飾詞](./access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-132">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>

<span data-ttu-id="1e0c9-133">欄位可以選擇性地宣告為 [static](../../language-reference/keywords/static.md)。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-133">A field can optionally be declared [static](../../language-reference/keywords/static.md).</span></span> <span data-ttu-id="1e0c9-134">這可隨時向呼叫者提供欄位，即使沒有任何類別執行個體存在。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-134">This makes the field available to callers at any time, even if no instance of the class exists.</span></span> <span data-ttu-id="1e0c9-135">如需詳細資訊，請參閱 [靜態類別和靜態類別成員](./static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-135">For more information, see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>

<span data-ttu-id="1e0c9-136">欄位可以宣告為 [readonly](../../language-reference/keywords/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-136">A field can be declared [readonly](../../language-reference/keywords/readonly.md).</span></span> <span data-ttu-id="1e0c9-137">您只能在初始化期間或在建構函式中指派值給唯讀欄位。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-137">A read-only field can only be assigned a value during initialization or in a constructor.</span></span> <span data-ttu-id="1e0c9-138">`static readonly` 欄位非常類似於常數，不同之處在於 C# 編譯器無法在編譯時期存取靜態唯讀欄位的值，只有在執行階段才能這麼做。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-138">A `static readonly` field is very similar to a constant, except that the C# compiler does not have access to the value of a static read-only field at compile time, only at run time.</span></span> <span data-ttu-id="1e0c9-139">如需詳細資訊，請參閱[常數](./constants.md)。</span><span class="sxs-lookup"><span data-stu-id="1e0c9-139">For more information, see [Constants](./constants.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1e0c9-140">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1e0c9-140">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1e0c9-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e0c9-141">See also</span></span>

- [<span data-ttu-id="1e0c9-142">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1e0c9-142">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1e0c9-143">類別和結構</span><span class="sxs-lookup"><span data-stu-id="1e0c9-143">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="1e0c9-144">使用建構函式</span><span class="sxs-lookup"><span data-stu-id="1e0c9-144">Using Constructors</span></span>](./using-constructors.md)
- [<span data-ttu-id="1e0c9-145">繼承</span><span class="sxs-lookup"><span data-stu-id="1e0c9-145">Inheritance</span></span>](./inheritance.md)
- [<span data-ttu-id="1e0c9-146">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="1e0c9-146">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="1e0c9-147">抽象和密封類別以及類別成員</span><span class="sxs-lookup"><span data-stu-id="1e0c9-147">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
