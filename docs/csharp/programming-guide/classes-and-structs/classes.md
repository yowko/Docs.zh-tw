---
title: "類別 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
caps.latest.revision: 40
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eedb087f177b1bff6f4d4177cd56ac4cca016490
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="a991c-102">類別 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="a991c-102">Classes (C# Programming Guide)</span></span>
<span data-ttu-id="a991c-103">「類別」是一種建構，可讓您將其他類型、方法和事件的變數群組在一起，以建立您自己的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="a991c-103">A *class* is a construct that enables you to create your own custom types by grouping together variables of other types, methods and events.</span></span> <span data-ttu-id="a991c-104">類別就像藍圖。</span><span class="sxs-lookup"><span data-stu-id="a991c-104">A class is like a blueprint.</span></span> <span data-ttu-id="a991c-105">它會定義類型的資料和行為。</span><span class="sxs-lookup"><span data-stu-id="a991c-105">It defines the data and behavior of a type.</span></span> <span data-ttu-id="a991c-106">如果類別未宣告為 static，則用戶端程式碼可以使用它，方法是建立指派給變數的「物件」或「執行個體」。</span><span class="sxs-lookup"><span data-stu-id="a991c-106">If the class is not declared as static, client code can use it by creating *objects* or *instances* which are assigned to a variable.</span></span> <span data-ttu-id="a991c-107">除非變數的所有參考都超出範圍，否則變數會保留在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="a991c-107">The variable remains in memory until all references to it go out of scope.</span></span> <span data-ttu-id="a991c-108">此時，CLR 會將它標記為適合進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a991c-108">At that time, the CLR marks it as eligible for garbage collection.</span></span> <span data-ttu-id="a991c-109">如果類別宣告為 [static](../../../csharp/language-reference/keywords/static.md)，則記憶體中只會有一個複本，而且用戶端程式碼只能透過類別本身存取它，而非「執行個體變數」。</span><span class="sxs-lookup"><span data-stu-id="a991c-109">If the class is declared as [static](../../../csharp/language-reference/keywords/static.md), then only one copy exists in memory and client code can only access it through the class itself, not an *instance variable*.</span></span> <span data-ttu-id="a991c-110">如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="a991c-110">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="a991c-111">與結構不同，類別支援「繼承」，這是物件導向程式設計的基礎特性。</span><span class="sxs-lookup"><span data-stu-id="a991c-111">Unlike structs, classes support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="a991c-112">如需詳細資訊，請參閱[繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="a991c-112">For more information, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="a991c-113">宣告類別</span><span class="sxs-lookup"><span data-stu-id="a991c-113">Declaring Classes</span></span>  
 <span data-ttu-id="a991c-114">使用 [class](../../../csharp/language-reference/keywords/class.md) 關鍵字宣告類別，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="a991c-114">Classes are declared by using the [class](../../../csharp/language-reference/keywords/class.md) keyword, as shown in the following example:</span></span>  
  
 <span data-ttu-id="a991c-115">[!code-cs[csProgGuideObjects#79](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a991c-115">[!code-cs[csProgGuideObjects#79](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_1.cs)]</span></span>  
  
 <span data-ttu-id="a991c-116">`class` 關鍵字的前面會加上存取層級。</span><span class="sxs-lookup"><span data-stu-id="a991c-116">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="a991c-117">因為在此情況下使用 [public](../../../csharp/language-reference/keywords/public.md)，所以所有人都可以從這個類別建立物件。</span><span class="sxs-lookup"><span data-stu-id="a991c-117">Because [public](../../../csharp/language-reference/keywords/public.md) is used in this case, anyone can create objects from this class.</span></span> <span data-ttu-id="a991c-118">類別的名稱遵循 `class` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a991c-118">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="a991c-119">定義的其餘部分是定義行為和資料的類別主體。</span><span class="sxs-lookup"><span data-stu-id="a991c-119">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="a991c-120">類別上的欄位、屬性、方法和事件統稱為「類別成員」。</span><span class="sxs-lookup"><span data-stu-id="a991c-120">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="a991c-121">建立物件</span><span class="sxs-lookup"><span data-stu-id="a991c-121">Creating Objects</span></span>  
 <span data-ttu-id="a991c-122">雖然它們有時會交換使用，但是類別和物件不同。</span><span class="sxs-lookup"><span data-stu-id="a991c-122">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="a991c-123">類別會定義一種類型的物件，但不是物件本身。</span><span class="sxs-lookup"><span data-stu-id="a991c-123">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="a991c-124">物件是根據類別的具體實體，而且有時稱為類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a991c-124">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="a991c-125">使用後面接著為物件基礎之類別名稱的 [new](../../../csharp/language-reference/keywords/new.md) 關鍵字，即可建立物件，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="a991c-125">Objects can be created by using the [new](../../../csharp/language-reference/keywords/new.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  
  
 <span data-ttu-id="a991c-126">[!code-cs[csProgGuideObjects#80](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="a991c-126">[!code-cs[csProgGuideObjects#80](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_2.cs)]</span></span>  
  
 <span data-ttu-id="a991c-127">建立類別的執行個體時，會將物件的參考傳回給程式設計人員。</span><span class="sxs-lookup"><span data-stu-id="a991c-127">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="a991c-128">在上述範例中，`object1` 是根據 `Customer` 之物件的參考。</span><span class="sxs-lookup"><span data-stu-id="a991c-128">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="a991c-129">這個參考參照新的物件，但不包含物件資料本身。</span><span class="sxs-lookup"><span data-stu-id="a991c-129">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="a991c-130">事實上，您可以建立物件參考，而根本不需要建立物件︰</span><span class="sxs-lookup"><span data-stu-id="a991c-130">In fact, you can create an object reference without creating an object at all:</span></span>  
  
 <span data-ttu-id="a991c-131">[!code-cs[csProgGuideObjects#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="a991c-131">[!code-cs[csProgGuideObjects#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_3.cs)]</span></span>  
  
 <span data-ttu-id="a991c-132">不建議建立物件參考，例如未參照物件的物件參考，因為在執行階段嘗試透過這類參考來存取物件將會失敗。</span><span class="sxs-lookup"><span data-stu-id="a991c-132">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="a991c-133">不過，可以進行這類參考來參照某個物件，方法是建立新的物件，或將它指派給現有物件，如下︰</span><span class="sxs-lookup"><span data-stu-id="a991c-133">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it to an existing object, such as this:</span></span>  
  
 <span data-ttu-id="a991c-134">[!code-cs[csProgGuideObjects#82](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="a991c-134">[!code-cs[csProgGuideObjects#82](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_4.cs)]</span></span>  
  
 <span data-ttu-id="a991c-135">這個程式碼會建立同時參照相同物件的兩個物件參考。</span><span class="sxs-lookup"><span data-stu-id="a991c-135">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="a991c-136">因此，任何透過 `object3` 進行的物件變更都會反映在後續使用 `object4` 時。</span><span class="sxs-lookup"><span data-stu-id="a991c-136">Therefore, any changes to the object made through `object3` will be reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="a991c-137">因為以傳址方式參照根據類別的物件，所以類別稱為參考型別。</span><span class="sxs-lookup"><span data-stu-id="a991c-137">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="a991c-138">類別繼承</span><span class="sxs-lookup"><span data-stu-id="a991c-138">Class Inheritance</span></span>  
 <span data-ttu-id="a991c-139">使用「衍生」可完成繼承，這表示使用從中繼承資料和行為的「基底類別」來宣告類別。</span><span class="sxs-lookup"><span data-stu-id="a991c-139">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="a991c-140">附加冒號以及接著衍生類別名稱後面的基底類別名稱，以指定基底類別，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="a991c-140">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  
  
 <span data-ttu-id="a991c-141">[!code-cs[csProgGuideObjects#83](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="a991c-141">[!code-cs[csProgGuideObjects#83](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_5.cs)]</span></span>  
  
 <span data-ttu-id="a991c-142">類別宣告基底類別時，會繼承基底類別的所有成員，但建構函式除外。</span><span class="sxs-lookup"><span data-stu-id="a991c-142">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span>  
  
 <span data-ttu-id="a991c-143">與 C++ 不同，C# 中的類別只能直接繼承自一個基底類別。</span><span class="sxs-lookup"><span data-stu-id="a991c-143">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="a991c-144">不過，因為基底類別本身可以繼承自另一個類別，所以類別可能會間接繼承多個基底類別。</span><span class="sxs-lookup"><span data-stu-id="a991c-144">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="a991c-145">基至，類別可以直接實作多個介面。</span><span class="sxs-lookup"><span data-stu-id="a991c-145">Furthermore, a class can directly implement more than one interface.</span></span> <span data-ttu-id="a991c-146">如需詳細資訊，請參閱[介面](../../../csharp/programming-guide/interfaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a991c-146">For more information, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="a991c-147">類別可以宣告為 [abstract](../../../csharp/language-reference/keywords/abstract.md)。</span><span class="sxs-lookup"><span data-stu-id="a991c-147">A class can be declared [abstract](../../../csharp/language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="a991c-148">抽象類別包含具有簽章定義但沒有實作的抽象方法。</span><span class="sxs-lookup"><span data-stu-id="a991c-148">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="a991c-149">無法具現化抽象類別。</span><span class="sxs-lookup"><span data-stu-id="a991c-149">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="a991c-150">它們僅用於實作抽象方法的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="a991c-150">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="a991c-151">相較之下，[sealed](../../../csharp/language-reference/keywords/sealed.md) 類別不允許從它衍生其他類別。</span><span class="sxs-lookup"><span data-stu-id="a991c-151">By contrast, a [sealed](../../../csharp/language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="a991c-152">如需詳細資訊，請參閱[抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="a991c-152">For more information, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="a991c-153">類別定義可以在不同的原始程式檔之間進行分割。</span><span class="sxs-lookup"><span data-stu-id="a991c-153">Class definitions can be split between different source files.</span></span> <span data-ttu-id="a991c-154">如需詳細資訊，請參閱[部分類別和方法](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="a991c-154">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="a991c-155">描述</span><span class="sxs-lookup"><span data-stu-id="a991c-155">Description</span></span>  
 <span data-ttu-id="a991c-156">在下列範例中，定義包含單一欄位、方法以及稱為建構函式之特殊方法的公用類別。</span><span class="sxs-lookup"><span data-stu-id="a991c-156">In the following example, a public class that contains a single field, a method, and a special method called a constructor is defined.</span></span> <span data-ttu-id="a991c-157">如需詳細資訊，請參閱[建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="a991c-157">For more information, see [Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span></span> <span data-ttu-id="a991c-158">然後使用 `new` 關鍵字具現化類別。</span><span class="sxs-lookup"><span data-stu-id="a991c-158">The class is then instantiated with the `new` keyword.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a991c-159">範例</span><span class="sxs-lookup"><span data-stu-id="a991c-159">Example</span></span>  
 <span data-ttu-id="a991c-160">[!code-cs[csProgGuideObjects#84](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="a991c-160">[!code-cs[csProgGuideObjects#84](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_6.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a991c-161">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="a991c-161">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a991c-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a991c-162">See Also</span></span>  
 <span data-ttu-id="a991c-163">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a991c-163">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="a991c-164">[物件導向程式設計](../concepts/object-oriented-programming.md) </span><span class="sxs-lookup"><span data-stu-id="a991c-164">[Object-Oriented Programming](../concepts/object-oriented-programming.md) </span></span>  
 <span data-ttu-id="a991c-165">[多型](../../../csharp/programming-guide/classes-and-structs/polymorphism.md) </span><span class="sxs-lookup"><span data-stu-id="a991c-165">[Polymorphism](../../../csharp/programming-guide/classes-and-structs/polymorphism.md) </span></span>  
 <span data-ttu-id="a991c-166">[成員](../../../csharp/programming-guide/classes-and-structs/members.md) </span><span class="sxs-lookup"><span data-stu-id="a991c-166">[Members](../../../csharp/programming-guide/classes-and-structs/members.md) </span></span>  
 <span data-ttu-id="a991c-167">[方法](../../../csharp/programming-guide/classes-and-structs/methods.md) </span><span class="sxs-lookup"><span data-stu-id="a991c-167">[Methods](../../../csharp/programming-guide/classes-and-structs/methods.md) </span></span>  
 <span data-ttu-id="a991c-168">[建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span><span class="sxs-lookup"><span data-stu-id="a991c-168">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span></span>  
 <span data-ttu-id="a991c-169">[完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span><span class="sxs-lookup"><span data-stu-id="a991c-169">[Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span></span>  
 [<span data-ttu-id="a991c-170">物件</span><span class="sxs-lookup"><span data-stu-id="a991c-170">Objects</span></span>](../../../csharp/programming-guide/classes-and-structs/objects.md)

