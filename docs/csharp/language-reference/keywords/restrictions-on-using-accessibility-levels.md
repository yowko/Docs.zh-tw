---
description: 使用存取範圍層級的限制 - C# 參考
title: 使用存取範圍層級的限制 - C# 參考
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 542e463e41c70f2e8aed5c20dc1294e296a88518
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136990"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="6fada-103">使用存取範圍層級的限制 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6fada-103">Restrictions on using accessibility levels (C# Reference)</span></span>

<span data-ttu-id="6fada-104">當您在宣告中指定類型時，請檢查類型的存取範圍層級是否相依於成員或另一個類型的存取範圍層級。</span><span class="sxs-lookup"><span data-stu-id="6fada-104">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="6fada-105">例如，直接基底類別至少必須可以像衍生類別一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="6fada-105">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="6fada-106">下列宣告會導致編譯器錯誤，因為基底類別 `BaseClass` 比 `MyClass` 更少存取：</span><span class="sxs-lookup"><span data-stu-id="6fada-106">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

<span data-ttu-id="6fada-107">下表摘要說明所宣告存取範圍層級的限制。</span><span class="sxs-lookup"><span data-stu-id="6fada-107">The following table summarizes the restrictions on declared accessibility levels.</span></span>

|<span data-ttu-id="6fada-108">Context</span><span class="sxs-lookup"><span data-stu-id="6fada-108">Context</span></span>|<span data-ttu-id="6fada-109">備註</span><span class="sxs-lookup"><span data-stu-id="6fada-109">Remarks</span></span>|
|-------------|-------------|
|[<span data-ttu-id="6fada-110">類別</span><span class="sxs-lookup"><span data-stu-id="6fada-110">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="6fada-111">類別類型的直接基底類別至少必須可以像類別類型本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="6fada-111">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|
|[<span data-ttu-id="6fada-112">介面</span><span class="sxs-lookup"><span data-stu-id="6fada-112">Interfaces</span></span>](../../programming-guide/interfaces/index.md)|<span data-ttu-id="6fada-113">介面類型的明確基底介面至少必須可以像介面類型本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="6fada-113">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|
|[<span data-ttu-id="6fada-114">委派</span><span class="sxs-lookup"><span data-stu-id="6fada-114">Delegates</span></span>](../../programming-guide/delegates/index.md)|<span data-ttu-id="6fada-115">委派類型的傳回類型和參數類型至少必須可以像委派類型本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="6fada-115">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|
|[<span data-ttu-id="6fada-116">常數</span><span class="sxs-lookup"><span data-stu-id="6fada-116">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="6fada-117">常數的類型至少必須可以像常數本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="6fada-117">The type of a constant must be at least as accessible as the constant itself.</span></span>|
|[<span data-ttu-id="6fada-118">欄位</span><span class="sxs-lookup"><span data-stu-id="6fada-118">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="6fada-119">欄位的類型至少必須可以像欄位本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="6fada-119">The type of a field must be at least as accessible as the field itself.</span></span>|
|[<span data-ttu-id="6fada-120">方法</span><span class="sxs-lookup"><span data-stu-id="6fada-120">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="6fada-121">方法的傳回類型和參數類型至少必須可以像方法本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="6fada-121">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|
|[<span data-ttu-id="6fada-122">屬性</span><span class="sxs-lookup"><span data-stu-id="6fada-122">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="6fada-123">屬性的類型至少必須可以像屬性本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="6fada-123">The type of a property must be at least as accessible as the property itself.</span></span>|
|[<span data-ttu-id="6fada-124">事件</span><span class="sxs-lookup"><span data-stu-id="6fada-124">Events</span></span>](../../programming-guide/events/index.md)|<span data-ttu-id="6fada-125">事件的類型至少必須可以像事件本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="6fada-125">The type of an event must be at least as accessible as the event itself.</span></span>|
|[<span data-ttu-id="6fada-126">索引子</span><span class="sxs-lookup"><span data-stu-id="6fada-126">Indexers</span></span>](../../programming-guide/indexers/index.md)|<span data-ttu-id="6fada-127">索引子的類型和參數類型至少必須可以像索引子本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="6fada-127">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|
|[<span data-ttu-id="6fada-128">運算子</span><span class="sxs-lookup"><span data-stu-id="6fada-128">Operators</span></span>](../operators/index.md)|<span data-ttu-id="6fada-129">運算子的傳回類型和參數類型至少必須可以像運算子本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="6fada-129">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|
|[<span data-ttu-id="6fada-130">建構函式</span><span class="sxs-lookup"><span data-stu-id="6fada-130">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="6fada-131">建構函式的參數類型至少必須可以像建構函式本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="6fada-131">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|

## <a name="example"></a><span data-ttu-id="6fada-132">範例</span><span class="sxs-lookup"><span data-stu-id="6fada-132">Example</span></span>

<span data-ttu-id="6fada-133">下列範例包含不同類型的錯誤宣告。</span><span class="sxs-lookup"><span data-stu-id="6fada-133">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="6fada-134">每個宣告之後的註解都指出預期的編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="6fada-134">The comment following each declaration indicates the expected compiler error.</span></span>

```csharp
// Restrictions on Using Accessibility Levels
// CS0052 expected as well as CS0053, CS0056, and CS0057
// To make the program work, change access level of both class B
// and MyPrivateMethod() to public.

using System;

// A delegate:
delegate int MyDelegate();

class B
{
    // A private method:
    static int MyPrivateMethod()
    {
        return 0;
    }
}

public class A
{
    // Error: The type B is less accessible than the field A.myField.
    public B myField = new B();

    // Error: The type B is less accessible
    // than the constant A.myConst.
    public readonly B myConst = new B();

    public B MyMethod()
    {
        // Error: The type B is less accessible
        // than the method A.MyMethod.
        return new B();
    }

    // Error: The type B is less accessible than the property A.MyProp
    public B MyProp
    {
        set
        {
        }
    }

    MyDelegate d = new MyDelegate(B.MyPrivateMethod);
    // Even when B is declared public, you still get the error:
    // "The parameter B.MyPrivateMethod is not accessible due to
    // protection level."

    public static B operator +(A m1, B m2)
    {
        // Error: The type B is less accessible
        // than the operator A.operator +(A,B)
        return new B();
    }

    static void Main()
    {
        Console.Write("Compiled successfully");
    }
}
```

## <a name="c-language-specification"></a><span data-ttu-id="6fada-135">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="6fada-135">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6fada-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fada-136">See also</span></span>

- [<span data-ttu-id="6fada-137">C # 參考</span><span class="sxs-lookup"><span data-stu-id="6fada-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6fada-138">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6fada-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6fada-139">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="6fada-139">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6fada-140">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="6fada-140">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="6fada-141">協助工具定義域</span><span class="sxs-lookup"><span data-stu-id="6fada-141">Accessibility Domain</span></span>](accessibility-domain.md)
- [<span data-ttu-id="6fada-142">協助工具層級</span><span class="sxs-lookup"><span data-stu-id="6fada-142">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="6fada-143">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="6fada-143">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="6fada-144">public</span><span class="sxs-lookup"><span data-stu-id="6fada-144">public</span></span>](public.md)
- [<span data-ttu-id="6fada-145">私人</span><span class="sxs-lookup"><span data-stu-id="6fada-145">private</span></span>](private.md)
- [<span data-ttu-id="6fada-146">protected</span><span class="sxs-lookup"><span data-stu-id="6fada-146">protected</span></span>](protected.md)
- [<span data-ttu-id="6fada-147">internal</span><span class="sxs-lookup"><span data-stu-id="6fada-147">internal</span></span>](internal.md)
