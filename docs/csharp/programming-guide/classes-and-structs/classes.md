---
title: 類別 - C# 程式設計手冊
ms.custom: seodec18
description: 了解類別類型和其建立方式
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: ad19099242a3bedbb7283219dfd7733db13231ec
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398583"
---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="176e2-103">類別 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="176e2-103">Classes (C# Programming Guide)</span></span>

## <a name="reference-types"></a><span data-ttu-id="176e2-104">參考型別</span><span class="sxs-lookup"><span data-stu-id="176e2-104">Reference types</span></span>  
<span data-ttu-id="176e2-105">定義為 [class](../../../csharp/language-reference/keywords/class.md) 的類型即為「參考型別」  。</span><span class="sxs-lookup"><span data-stu-id="176e2-105">A type that is defined as a [class](../../../csharp/language-reference/keywords/class.md) is a *reference type*.</span></span> <span data-ttu-id="176e2-106">在執行階段，當您宣告參考型別的變數時，該變數會包含 [null](../../../csharp/language-reference/keywords/null.md) 值，直到您使用 [new](../../../csharp/language-reference/operators/new-operator.md) 運算子明確地建立類別的執行個體，或為其指派在他處建立的相容類型物件為止，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="176e2-106">At run time, when you declare a variable of a reference type, the variable contains the value [null](../../../csharp/language-reference/keywords/null.md) until you explicitly create an instance of the class by using the [new](../../../csharp/language-reference/operators/new-operator.md) operator, or assign it an object of a compatible type that may have been created elsewhere, as shown in the following example:</span></span>

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

<span data-ttu-id="176e2-107">建立物件時，會在受控堆積上配置足夠的記憶體給該特定物件，而變數只會保留該物件位置的參考。</span><span class="sxs-lookup"><span data-stu-id="176e2-107">When the object is created, enough memory is allocated on the managed heap for that specific object, and the variable holds only a reference to the location of said object.</span></span> <span data-ttu-id="176e2-108">配置和由 CLR 的自動記憶體管理功能 (也就是「記憶體回收」  ) 回收 Managed 堆積上的型別時，都需要額外負荷。</span><span class="sxs-lookup"><span data-stu-id="176e2-108">Types on the managed heap require overhead both when they are allocated and when they are reclaimed by the automatic memory management functionality of the CLR, which is known as *garbage collection*.</span></span> <span data-ttu-id="176e2-109">不過，記憶體回收也已獲得高度最佳化，因此在大部分情況下並不會產生效能問題。</span><span class="sxs-lookup"><span data-stu-id="176e2-109">However, garbage collection is also highly optimized and in most scenarios, it does not create a performance issue.</span></span> <span data-ttu-id="176e2-110">如需記憶體回收的詳細資訊，請參閱[自動記憶體管理和記憶體回收](../../../standard/garbage-collection/gc.md)。</span><span class="sxs-lookup"><span data-stu-id="176e2-110">For more information about garbage collection, see [Automatic memory management and garbage collection](../../../standard/garbage-collection/gc.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="176e2-111">宣告類別</span><span class="sxs-lookup"><span data-stu-id="176e2-111">Declaring Classes</span></span>

 <span data-ttu-id="176e2-112">使用 [class](../../../csharp/language-reference/keywords/class.md) 關鍵字並在後面接著唯一識別碼來宣告類別，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="176e2-112">Classes are declared by using the [class](../../../csharp/language-reference/keywords/class.md) keyword followed by a unique identifier, as shown in the following example:</span></span>

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 <span data-ttu-id="176e2-113">`class` 關鍵字的前面會加上存取層級。</span><span class="sxs-lookup"><span data-stu-id="176e2-113">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="176e2-114">因為在此情況下會使用 [public](../../language-reference/keywords/public.md)，所以所有人都可以從這個類別建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="176e2-114">Because [public](../../language-reference/keywords/public.md) is used in this case, anyone can create instances of this class.</span></span> <span data-ttu-id="176e2-115">類別的名稱遵循 `class` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="176e2-115">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="176e2-116">類別名稱必須是有效的 C# [識別碼名稱](../inside-a-program/identifier-names.md)。</span><span class="sxs-lookup"><span data-stu-id="176e2-116">The name of the class must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="176e2-117">定義的其餘部分是定義行為和資料的類別主體。</span><span class="sxs-lookup"><span data-stu-id="176e2-117">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="176e2-118">類別上的欄位、屬性、方法和事件統稱為「類別成員」  。</span><span class="sxs-lookup"><span data-stu-id="176e2-118">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="176e2-119">建立物件</span><span class="sxs-lookup"><span data-stu-id="176e2-119">Creating objects</span></span>

<span data-ttu-id="176e2-120">雖然它們有時會交換使用，但是類別和物件不同。</span><span class="sxs-lookup"><span data-stu-id="176e2-120">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="176e2-121">類別會定義一種類型的物件，但不是物件本身。</span><span class="sxs-lookup"><span data-stu-id="176e2-121">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="176e2-122">物件是根據類別的具體實體，而且有時稱為類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="176e2-122">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="176e2-123">使用後面接著為物件基礎之類別名稱的 [new](../../language-reference/operators/new-operator.md) 關鍵字，即可建立物件，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="176e2-123">Objects can be created by using the [new](../../language-reference/operators/new-operator.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  

 ```csharp
 Customer object1 = new Customer();
 ```

 <span data-ttu-id="176e2-124">建立類別的執行個體時，會將物件的參考傳回給程式設計人員。</span><span class="sxs-lookup"><span data-stu-id="176e2-124">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="176e2-125">在上述範例中，`object1` 是根據 `Customer` 之物件的參考。</span><span class="sxs-lookup"><span data-stu-id="176e2-125">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="176e2-126">這個參考參照新的物件，但不包含物件資料本身。</span><span class="sxs-lookup"><span data-stu-id="176e2-126">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="176e2-127">事實上，您可以建立物件參考，而根本不需要建立物件︰</span><span class="sxs-lookup"><span data-stu-id="176e2-127">In fact, you can create an object reference without creating an object at all:</span></span>  
 
```csharp
 Customer object2;
```
 
 <span data-ttu-id="176e2-128">不建議建立物件參考，例如未參照物件的物件參考，因為在執行階段嘗試透過這類參考來存取物件將會失敗。</span><span class="sxs-lookup"><span data-stu-id="176e2-128">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="176e2-129">不過，可以進行這類參考來參照某個物件，方法是建立新的物件，或將它指派給現有物件，如下︰</span><span class="sxs-lookup"><span data-stu-id="176e2-129">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it to an existing object, such as this:</span></span>  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 <span data-ttu-id="176e2-130">這個程式碼會建立同時參照相同物件的兩個物件參考。</span><span class="sxs-lookup"><span data-stu-id="176e2-130">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="176e2-131">因此，任何透過 `object3` 進行的物件變更都會反映在後續使用 `object4` 時。</span><span class="sxs-lookup"><span data-stu-id="176e2-131">Therefore, any changes to the object made through `object3` are reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="176e2-132">因為以傳址方式參照根據類別的物件，所以類別稱為參考型別。</span><span class="sxs-lookup"><span data-stu-id="176e2-132">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="176e2-133">類別繼承</span><span class="sxs-lookup"><span data-stu-id="176e2-133">Class inheritance</span></span>  

<span data-ttu-id="176e2-134">類別完全支援「繼承」  ，這是物件導向程式設計的基礎特性。</span><span class="sxs-lookup"><span data-stu-id="176e2-134">Classes fully support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="176e2-135">當您建立類別時，可以繼承自任何未定義為 [sealed](../../../csharp/language-reference/keywords/sealed.md) 的介面或類別，而其他類別可以繼承自您的類別並覆寫類別虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="176e2-135">When you create a class, you can inherit from any other interface or class that is not defined as [sealed](../../../csharp/language-reference/keywords/sealed.md), and other classes can inherit from your class and override class virtual methods.</span></span>

<span data-ttu-id="176e2-136">使用「衍生」  可完成繼承，這表示使用從中繼承資料和行為的「基底類別」  來宣告類別。</span><span class="sxs-lookup"><span data-stu-id="176e2-136">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="176e2-137">附加冒號以及接著衍生類別名稱後面的基底類別名稱，以指定基底類別，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="176e2-137">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

<span data-ttu-id="176e2-138">類別宣告基底類別時，會繼承基底類別的所有成員，但建構函式除外。</span><span class="sxs-lookup"><span data-stu-id="176e2-138">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span> <span data-ttu-id="176e2-139">如需詳細資訊，請參閱[繼承](inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="176e2-139">For more information, see [Inheritance](inheritance.md).</span></span>
  
<span data-ttu-id="176e2-140">與 C++ 不同，C# 中的類別只能直接繼承自一個基底類別。</span><span class="sxs-lookup"><span data-stu-id="176e2-140">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="176e2-141">不過，因為基底類別本身可以繼承自另一個類別，所以類別可能會間接繼承多個基底類別。</span><span class="sxs-lookup"><span data-stu-id="176e2-141">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="176e2-142">基至，類別可以直接實作多個介面。</span><span class="sxs-lookup"><span data-stu-id="176e2-142">Furthermore, a class can directly implement more than one interface.</span></span> <span data-ttu-id="176e2-143">如需詳細資訊，請參閱[介面](../interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="176e2-143">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
<span data-ttu-id="176e2-144">類別可以宣告為 [abstract](../../language-reference/keywords/abstract.md)。</span><span class="sxs-lookup"><span data-stu-id="176e2-144">A class can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="176e2-145">抽象類別包含具有簽章定義但沒有實作的抽象方法。</span><span class="sxs-lookup"><span data-stu-id="176e2-145">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="176e2-146">無法具現化抽象類別。</span><span class="sxs-lookup"><span data-stu-id="176e2-146">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="176e2-147">它們僅用於實作抽象方法的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="176e2-147">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="176e2-148">相較之下，[sealed](../../language-reference/keywords/sealed.md) 類別不允許從它衍生其他類別。</span><span class="sxs-lookup"><span data-stu-id="176e2-148">By contrast, a [sealed](../../language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="176e2-149">如需詳細資訊，請參閱[抽象和密封類別以及類別成員](abstract-and-sealed-classes-and-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="176e2-149">For more information, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
<span data-ttu-id="176e2-150">類別定義可以在不同的原始程式檔之間進行分割。</span><span class="sxs-lookup"><span data-stu-id="176e2-150">Class definitions can be split between different source files.</span></span> <span data-ttu-id="176e2-151">如需詳細資訊，請參閱[部分類別和方法](partial-classes-and-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="176e2-151">For more information, see [Partial Classes and Methods](partial-classes-and-methods.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="176e2-152">範例</span><span class="sxs-lookup"><span data-stu-id="176e2-152">Example</span></span>

<span data-ttu-id="176e2-153">下列範例定義了一個公用類別，其中包含[自動實作屬性](auto-implemented-properties.md)、方法以及稱為建構函式的特殊方法。</span><span class="sxs-lookup"><span data-stu-id="176e2-153">The following example defines a public class that contains an [auto-implemented property](auto-implemented-properties.md), a method, and a special method called a constructor.</span></span> <span data-ttu-id="176e2-154">如需詳細資訊，請參閱[屬性](properties.md)，[方法](methods.md)和[建構函式](constructors.md)主題。</span><span class="sxs-lookup"><span data-stu-id="176e2-154">For more information, see [Properties](properties.md), [Methods](methods.md), and [Constructors](constructors.md) topics.</span></span> <span data-ttu-id="176e2-155">然後使用 `new` 關鍵字具現化類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="176e2-155">The instances of the class are then instantiated with the `new` keyword.</span></span>  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a><span data-ttu-id="176e2-156">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="176e2-156">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="176e2-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="176e2-157">See also</span></span>

- [<span data-ttu-id="176e2-158">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="176e2-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="176e2-159">物件導向程式設計</span><span class="sxs-lookup"><span data-stu-id="176e2-159">Object-Oriented Programming</span></span>](../concepts/object-oriented-programming.md)
- [<span data-ttu-id="176e2-160">多型</span><span class="sxs-lookup"><span data-stu-id="176e2-160">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="176e2-161">識別碼名稱</span><span class="sxs-lookup"><span data-stu-id="176e2-161">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="176e2-162">成員</span><span class="sxs-lookup"><span data-stu-id="176e2-162">Members</span></span>](members.md)
- [<span data-ttu-id="176e2-163">方法</span><span class="sxs-lookup"><span data-stu-id="176e2-163">Methods</span></span>](methods.md)
- [<span data-ttu-id="176e2-164">建構函式</span><span class="sxs-lookup"><span data-stu-id="176e2-164">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="176e2-165">完成項</span><span class="sxs-lookup"><span data-stu-id="176e2-165">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="176e2-166">物件</span><span class="sxs-lookup"><span data-stu-id="176e2-166">Objects</span></span>](objects.md)
