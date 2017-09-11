---
title: "使用存取範圍層級的限制 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
caps.latest.revision: 21
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
ms.openlocfilehash: 8e49afd38fd776593b87f065a079da0d546df4a6
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="f1d35-102">使用存取範圍層級的限制 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="f1d35-102">Restrictions on Using Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="f1d35-103">當您在宣告中指定類型時，請檢查類型的存取範圍層級是否相依於成員或另一個類型的存取範圍層級。</span><span class="sxs-lookup"><span data-stu-id="f1d35-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="f1d35-104">例如，直接基底類別至少必須可以像衍生類別一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="f1d35-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="f1d35-105">下列宣告會導致編譯器錯誤，因為基底類別 `BaseClass` 比 `MyClass` 更少存取：</span><span class="sxs-lookup"><span data-stu-id="f1d35-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>  
  
```  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 <span data-ttu-id="f1d35-106">下表摘要說明所宣告存取範圍層級的限制。</span><span class="sxs-lookup"><span data-stu-id="f1d35-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>  
  
|<span data-ttu-id="f1d35-107">內容</span><span class="sxs-lookup"><span data-stu-id="f1d35-107">Context</span></span>|<span data-ttu-id="f1d35-108">備註</span><span class="sxs-lookup"><span data-stu-id="f1d35-108">Remarks</span></span>|  
|-------------|-------------|  
|[<span data-ttu-id="f1d35-109">類別</span><span class="sxs-lookup"><span data-stu-id="f1d35-109">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="f1d35-110">類別類型的直接基底類別至少必須可以像類別類型本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="f1d35-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|  
|[<span data-ttu-id="f1d35-111">介面</span><span class="sxs-lookup"><span data-stu-id="f1d35-111">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)|<span data-ttu-id="f1d35-112">介面類型的明確基底介面至少必須可以像介面類型本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="f1d35-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|  
|[<span data-ttu-id="f1d35-113">委派</span><span class="sxs-lookup"><span data-stu-id="f1d35-113">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)|<span data-ttu-id="f1d35-114">委派類型的傳回類型和參數類型至少必須可以像委派類型本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="f1d35-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|  
|[<span data-ttu-id="f1d35-115">常數</span><span class="sxs-lookup"><span data-stu-id="f1d35-115">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="f1d35-116">常數的類型至少必須可以像常數本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="f1d35-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|  
|[<span data-ttu-id="f1d35-117">欄位</span><span class="sxs-lookup"><span data-stu-id="f1d35-117">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="f1d35-118">欄位的類型至少必須可以像欄位本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="f1d35-118">The type of a field must be at least as accessible as the field itself.</span></span>|  
|[<span data-ttu-id="f1d35-119">方法</span><span class="sxs-lookup"><span data-stu-id="f1d35-119">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="f1d35-120">方法的傳回類型和參數類型至少必須可以像方法本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="f1d35-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|  
|[<span data-ttu-id="f1d35-121">屬性</span><span class="sxs-lookup"><span data-stu-id="f1d35-121">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="f1d35-122">屬性的類型至少必須可以像屬性本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="f1d35-122">The type of a property must be at least as accessible as the property itself.</span></span>|  
|[<span data-ttu-id="f1d35-123">事件</span><span class="sxs-lookup"><span data-stu-id="f1d35-123">Events</span></span>](../../../csharp/programming-guide/events/index.md)|<span data-ttu-id="f1d35-124">事件的類型至少必須可以像事件本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="f1d35-124">The type of an event must be at least as accessible as the event itself.</span></span>|  
|[<span data-ttu-id="f1d35-125">索引子</span><span class="sxs-lookup"><span data-stu-id="f1d35-125">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)|<span data-ttu-id="f1d35-126">索引子的類型和參數類型至少必須可以像索引子本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="f1d35-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|  
|[<span data-ttu-id="f1d35-127">運算子</span><span class="sxs-lookup"><span data-stu-id="f1d35-127">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|<span data-ttu-id="f1d35-128">運算子的傳回類型和參數類型至少必須可以像運算子本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="f1d35-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|  
|[<span data-ttu-id="f1d35-129">建構函式</span><span class="sxs-lookup"><span data-stu-id="f1d35-129">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="f1d35-130">建構函式的參數類型至少必須可以像建構函式本身一樣地存取。</span><span class="sxs-lookup"><span data-stu-id="f1d35-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f1d35-131">範例</span><span class="sxs-lookup"><span data-stu-id="f1d35-131">Example</span></span>  
 <span data-ttu-id="f1d35-132">下列範例包含不同類型的錯誤宣告。</span><span class="sxs-lookup"><span data-stu-id="f1d35-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="f1d35-133">每個宣告之後的註解都指出預期的編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="f1d35-133">The comment following each declaration indicates the expected compiler error.</span></span>  
  
```  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="f1d35-134">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f1d35-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f1d35-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1d35-135">See Also</span></span>  
 <span data-ttu-id="f1d35-136">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f1d35-136">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f1d35-137">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f1d35-137">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f1d35-138">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="f1d35-138">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="f1d35-139">[存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="f1d35-139">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="f1d35-140">[存取範圍定義域](../../../csharp/language-reference/keywords/accessibility-domain.md) </span><span class="sxs-lookup"><span data-stu-id="f1d35-140">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md) </span></span>  
 <span data-ttu-id="f1d35-141">[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="f1d35-141">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="f1d35-142">[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="f1d35-142">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="f1d35-143">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="f1d35-143">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="f1d35-144">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="f1d35-144">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="f1d35-145">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="f1d35-145">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 [<span data-ttu-id="f1d35-146">internal</span><span class="sxs-lookup"><span data-stu-id="f1d35-146">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

