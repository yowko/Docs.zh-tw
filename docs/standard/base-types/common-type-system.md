---
title: "深入了解一般型別系統"
description: "深入了解一般型別系統"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: b5482a1d-7bdc-40fe-aa45-10df930ceb5b
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 6be672acc84a76106e25b82574acad16beb4a8ac
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="common-type-system-in-depth"></a><span data-ttu-id="05c7c-104">深入了解一般型別系統</span><span class="sxs-lookup"><span data-stu-id="05c7c-104">Common type system in depth</span></span>

<span data-ttu-id="05c7c-105">本主題中的下列各節將深入探索一般型別系統：</span><span class="sxs-lookup"><span data-stu-id="05c7c-105">This topic contains the following sections that explore the common type system in depth:</span></span>

* [<span data-ttu-id="05c7c-106">.NET 中的類型</span><span class="sxs-lookup"><span data-stu-id="05c7c-106">Types in .NET</span></span>](#types-in-net)

* [<span data-ttu-id="05c7c-107">類型定義</span><span class="sxs-lookup"><span data-stu-id="05c7c-107">Type definitions</span></span>](#type-definitions)

* [<span data-ttu-id="05c7c-108">類型成員</span><span class="sxs-lookup"><span data-stu-id="05c7c-108">Type members</span></span>](#type-members)

* [<span data-ttu-id="05c7c-109">類型成員的特性</span><span class="sxs-lookup"><span data-stu-id="05c7c-109">Characteristics of type members</span></span>](#characteristics-of-type-members)


## <a name="types-in-net"></a><span data-ttu-id="05c7c-110">.NET 中的類型</span><span class="sxs-lookup"><span data-stu-id="05c7c-110">Types in .NET</span></span>

<span data-ttu-id="05c7c-111">.NET 中的所有型別屬於實值型別或是參考型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-111">All types in .NET are either value types or reference types.</span></span> 

<span data-ttu-id="05c7c-112">如果資料型別的物件是由物件的實際值來表示，那麼這個資料型別就是實值型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-112">Value types are data types whose objects are represented by the object's actual value.</span></span> <span data-ttu-id="05c7c-113">如果將實值型別的執行個體指派給變數，該變數會取得這個值的全新複本。</span><span class="sxs-lookup"><span data-stu-id="05c7c-113">If an instance of a value type is assigned to a variable, that variable is given a fresh copy of the value.</span></span>

<span data-ttu-id="05c7c-114">如果資料型別的物件是由物件之實際值的參考 (類似於指標) 來表示，那麼這個資料型別就是參考型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-114">Reference types are data types whose objects are represented by a reference (similar to a pointer) to the object's actual value.</span></span> <span data-ttu-id="05c7c-115">如果將參考型別指派給變數，該變數就會參考 (指向) 原始值。</span><span class="sxs-lookup"><span data-stu-id="05c7c-115">If a reference type is assigned to a variable, that variable references (points to) the original value.</span></span> <span data-ttu-id="05c7c-116">不會進行複製。</span><span class="sxs-lookup"><span data-stu-id="05c7c-116">No copy is made.</span></span> 

<span data-ttu-id="05c7c-117">.NET 中的一般型別系統支援下列五種型別：</span><span class="sxs-lookup"><span data-stu-id="05c7c-117">The common type system in .NET supports the following five categories of types:</span></span>

* [<span data-ttu-id="05c7c-118">類別</span><span class="sxs-lookup"><span data-stu-id="05c7c-118">Classes</span></span>](#classes)

* [<span data-ttu-id="05c7c-119">結構</span><span class="sxs-lookup"><span data-stu-id="05c7c-119">Structures</span></span>](#structures)

* [<span data-ttu-id="05c7c-120">列舉</span><span class="sxs-lookup"><span data-stu-id="05c7c-120">Enumerations</span></span>](#enumerations)

* [<span data-ttu-id="05c7c-121">介面</span><span class="sxs-lookup"><span data-stu-id="05c7c-121">Interfaces</span></span>](#interfaces)

* [<span data-ttu-id="05c7c-122">委派</span><span class="sxs-lookup"><span data-stu-id="05c7c-122">Delegates</span></span>](#delegates)

### <a name="classes"></a><span data-ttu-id="05c7c-123">類別</span><span class="sxs-lookup"><span data-stu-id="05c7c-123">Classes</span></span>

<span data-ttu-id="05c7c-124">類別是指可以直接衍生自其他類別且隱含衍生自 [System.Object](xref:System.Object) 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-124">A class is a reference type that can be derived directly from another class and that is derived implicitly from [System.Object](xref:System.Object).</span></span> <span data-ttu-id="05c7c-125">類別會定義物件 (類別的執行個體) 可以執行的作業 (方法、事件或屬性) 以及物件包含的資料 (欄位)。</span><span class="sxs-lookup"><span data-stu-id="05c7c-125">The class defines the operations that an object (which is an instance of the class) can perform (methods, events, or properties) and the data that the object contains (fields).</span></span> <span data-ttu-id="05c7c-126">雖然類別通常包括定義和實作 (不同於介面，例如介面只包含定義而不含實作)，但是類別可以有一個或多個不具實作的成員。</span><span class="sxs-lookup"><span data-stu-id="05c7c-126">Although a class generally includes both definition and implementation (unlike interfaces, for example, which contain only definition without implementation), it can have one or more members that have no implementation.</span></span>

<span data-ttu-id="05c7c-127">下表將說明類別可以具有的某些特性。</span><span class="sxs-lookup"><span data-stu-id="05c7c-127">The following table describes some of the characteristics that a class may have.</span></span> <span data-ttu-id="05c7c-128">每一個支援執行階段的語言都會提供一種方式，指出類別或類別成員具有這些其中一個或多個特性。</span><span class="sxs-lookup"><span data-stu-id="05c7c-128">Each language that supports the runtime provides a way to indicate that a class or class member has one or more of these characteristics.</span></span> <span data-ttu-id="05c7c-129">然而，以 .NET 為目標的程式設計語言則無法使用所有這些特性。</span><span class="sxs-lookup"><span data-stu-id="05c7c-129">However, individual programming languages that target .NET may not make all these characteristics available.</span></span>

<span data-ttu-id="05c7c-130">特性</span><span class="sxs-lookup"><span data-stu-id="05c7c-130">Characteristic</span></span> | <span data-ttu-id="05c7c-131">描述</span><span class="sxs-lookup"><span data-stu-id="05c7c-131">Description</span></span>
-------------- | -----------
<span data-ttu-id="05c7c-132">sealed</span><span class="sxs-lookup"><span data-stu-id="05c7c-132">sealed</span></span> | <span data-ttu-id="05c7c-133">指定無法從這個型別衍生出其他類別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-133">Specifies that another class cannot be derived from this type.</span></span>
<span data-ttu-id="05c7c-134">實作</span><span class="sxs-lookup"><span data-stu-id="05c7c-134">implements</span></span> | <span data-ttu-id="05c7c-135">指出類別會以提供介面成員實作的方式來使用一個或多個介面。</span><span class="sxs-lookup"><span data-stu-id="05c7c-135">Indicates that the class uses one or more interfaces by providing implementations of interface members.</span></span>
<span data-ttu-id="05c7c-136">abstract</span><span class="sxs-lookup"><span data-stu-id="05c7c-136">abstract</span></span> | <span data-ttu-id="05c7c-137">表示這個類別無法執行個體化。</span><span class="sxs-lookup"><span data-stu-id="05c7c-137">Indicates that the class cannot be instantiated.</span></span> <span data-ttu-id="05c7c-138">若要使用這個特性，必須從它衍生出其他類別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-138">To use it, you must derive another class from it.</span></span>
<span data-ttu-id="05c7c-139">繼承</span><span class="sxs-lookup"><span data-stu-id="05c7c-139">inherits</span></span> | <span data-ttu-id="05c7c-140">指出類別的執行個體可用於已指定基底類別 (Base Class) 的任何位置。</span><span class="sxs-lookup"><span data-stu-id="05c7c-140">Indicates that instances of the class can be used anywhere the base class is specified.</span></span> <span data-ttu-id="05c7c-141">從基底類別繼承的衍生類別可以使用基底類別所提供的任何公用成員實作，或者衍生類別可以利用本身的實作來覆寫公用成員的實作。</span><span class="sxs-lookup"><span data-stu-id="05c7c-141">A derived class that inherits from a base class can use the implementation of any public members provided by the base class, or the derived class can override the implementation of the public members with its own implementation.</span></span>
<span data-ttu-id="05c7c-142">exported 或 not exported</span><span class="sxs-lookup"><span data-stu-id="05c7c-142">exported or not exported</span></span> | <span data-ttu-id="05c7c-143">指出是否可在定義類別的組件中看見類別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-143">Indicates whether a class is visible outside the assembly in which it is defined.</span></span> <span data-ttu-id="05c7c-144">這項特性僅適用於最上層類別，並不適用於巢狀類別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-144">This characteristic applies only to top-level classes and not to nested classes.</span></span>

> [!NOTE]
> <span data-ttu-id="05c7c-145">類別也可以透過巢狀方式置於父類別或結構中。</span><span class="sxs-lookup"><span data-stu-id="05c7c-145">A class can also be nested in a parent class or structure.</span></span> <span data-ttu-id="05c7c-146">巢狀類別也具有成員特性。</span><span class="sxs-lookup"><span data-stu-id="05c7c-146">Nested classes also have member characteristics.</span></span> <span data-ttu-id="05c7c-147">如需詳細資訊，請參閱[巢狀類型](#nested-types)。</span><span class="sxs-lookup"><span data-stu-id="05c7c-147">For more information, see [Nested types](#nested-types).</span></span>

<span data-ttu-id="05c7c-148">沒有實作的類別成員是抽象成員。</span><span class="sxs-lookup"><span data-stu-id="05c7c-148">Class members that have no implementation are abstract members.</span></span> <span data-ttu-id="05c7c-149">有一個或多個抽象成員的類別本身就是抽象的；所以無法建立它的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="05c7c-149">A class that has one or more abstract members is itself abstract; new instances of it cannot be created.</span></span> <span data-ttu-id="05c7c-150">有些以執行階段為目標的語言即使沒有任何抽象的成員，也允許您將類別標記為抽象。</span><span class="sxs-lookup"><span data-stu-id="05c7c-150">Some languages that target the runtime let you mark a class as abstract even if none of its members are abstract.</span></span> <span data-ttu-id="05c7c-151">當您需要封裝一組衍生類別在適當時可繼承或覆寫的基本功能時，可以使用抽象類別 (Abstract Class)。</span><span class="sxs-lookup"><span data-stu-id="05c7c-151">You can use an abstract class when you want to encapsulate a basic set of functionality that derived classes can inherit or override when appropriate.</span></span> <span data-ttu-id="05c7c-152">非抽象的類別即稱為實體類別 (Concrete Class)。</span><span class="sxs-lookup"><span data-stu-id="05c7c-152">Classes that are not abstract are referred to as concrete classes.</span></span>

<span data-ttu-id="05c7c-153">一個類別可以實作任意數量的介面，但是除了所有類別都會隱含繼承的來源 [System.Object](xref:System.Object) 以外，只能繼承一個基底類別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-153">A class can implement any number of interfaces, but it can inherit from only one base class in addition to [System.Object](xref:System.Object), from which all classes inherit implicitly.</span></span> <span data-ttu-id="05c7c-154">所有類別都至少必須有一個建構函式，用來初始化類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="05c7c-154">All classes must have at least one constructor, which initializes new instances of the class.</span></span> <span data-ttu-id="05c7c-155">如果您沒有明確定義建構函式，大多數的編譯器會自動提供預設 (無參數) 建構函式。</span><span class="sxs-lookup"><span data-stu-id="05c7c-155">If you do not explicitly define a constructor, most compilers will automatically provide a default (parameterless) constructor.</span></span>

### <a name="structures"></a><span data-ttu-id="05c7c-156">結構</span><span class="sxs-lookup"><span data-stu-id="05c7c-156">Structures</span></span>

<span data-ttu-id="05c7c-157">結構是自 [System.ValueType](xref:System.ValueType) (衍生自 [System.Object](xref:System.Object)) 隱含衍生的實值型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-157">A structure is a value type that derives implicitly from [System.ValueType](xref:System.ValueType), which in turn is derived from [System.Object](xref:System.Object).</span></span> <span data-ttu-id="05c7c-158">在表示記憶體需求相當小的實質型別時，以及將值當做傳值參考傳遞給具有強型別參數的方法時，結構將相當實用。</span><span class="sxs-lookup"><span data-stu-id="05c7c-158">A structure is very useful for representing values whose memory requirements are small, and for passing values as by-value parameters to methods that have strongly typed parameters.</span></span> <span data-ttu-id="05c7c-159">在 .NET 中，所有基本資料型別 ([Boolean](xref:System.Boolean)、[Byte](xref:System.Byte)、[Char](xref:System.Char)、[DateTime](xref:System.DateTime)、[Decimal](xref:System.Decimal)、[Double](xref:System.Double)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[SByte](xref:System.SByte)、[Single](xref:System.Single)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32) 和 [UInt64](xref:System.UInt64)) 都會定義為結構。</span><span class="sxs-lookup"><span data-stu-id="05c7c-159">In .NET, all primitive data types ([Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [Char](xref:System.Char), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), and [UInt64](xref:System.UInt64)) are defined as structures.</span></span>

<span data-ttu-id="05c7c-160">與類別一樣，結構會定義資料 (結構的欄位) 以及可以在該資料上定義的作業 (結構的方法)。</span><span class="sxs-lookup"><span data-stu-id="05c7c-160">Like classes, structures define both data (the fields of the structure) and the operations that can be performed on that data (the methods of the structure).</span></span> <span data-ttu-id="05c7c-161">這表示您可以在結構上呼叫方法，包括在 [System.Object](xref:System.Object) 和 [System.ValueType](xref:System.ValueType) 類別上定義的虛擬方法，以及在實值型別本身定義的任何方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-161">This means that you can call methods on structures, including the virtual methods defined on the [System.Object](xref:System.Object) and [System.ValueType](xref:System.ValueType) classes, and any methods defined on the value type itself.</span></span> <span data-ttu-id="05c7c-162">換言之，除了靜態與非靜態方法之外，結構還可以具有欄位、屬性和事件。</span><span class="sxs-lookup"><span data-stu-id="05c7c-162">In other words, structures can have fields, properties, and events, as well as static and nonstatic methods.</span></span> <span data-ttu-id="05c7c-163">您可以建立結構的執行個體，將它們當做參數傳遞，並將它們當做區域變數儲存或將它們儲存到其他實值型別或參考型別的欄位中。</span><span class="sxs-lookup"><span data-stu-id="05c7c-163">You can create instances of structures, pass them as parameters, store them as local variables, or store them in a field of another value type or reference type.</span></span> <span data-ttu-id="05c7c-164">結構也可以實作介面。</span><span class="sxs-lookup"><span data-stu-id="05c7c-164">Structures can also implement interfaces.</span></span>

<span data-ttu-id="05c7c-165">實值型別在許多層面上與類別不同。</span><span class="sxs-lookup"><span data-stu-id="05c7c-165">Value types also differ from classes in several respects.</span></span> <span data-ttu-id="05c7c-166">首先，雖然它們隱含繼承自 [System.ValueType](xref:System.ValueType)，但是卻無法直接繼承自任何型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-166">First, although they implicitly inherit from [System.ValueType](xref:System.ValueType), they cannot directly inherit from any type.</span></span> <span data-ttu-id="05c7c-167">同樣地，所有實值型別都是密封型別，表示無法從中衍生其他型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-167">Similarly, all value types are sealed, which means that no other type can be derived from them.</span></span> <span data-ttu-id="05c7c-168">實值型別不需要建構函式。</span><span class="sxs-lookup"><span data-stu-id="05c7c-168">They also do not require constructors.</span></span>

<span data-ttu-id="05c7c-169">對每一個實值型別而言，Common Language Runtime 都提供了對應的 Boxed 型別，這是具有與實值型別相同狀態和行為的類別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-169">For each value type, the common language runtime supplies a corresponding boxed type, which is a class that has the same state and behavior as the value type.</span></span> <span data-ttu-id="05c7c-170">實值型別的執行個體傳遞給接受型別為 [System.Object](xref:System.Object) 之參數的方法時，會進行 Boxed 處理。</span><span class="sxs-lookup"><span data-stu-id="05c7c-170">An instance of a value type is boxed when it is passed to a method that accepts a parameter of type [System.Object](xref:System.Object).</span></span> <span data-ttu-id="05c7c-171">當控制項從接受實質型別做為傳址參數的方法呼叫傳回時，它會 Unboxed (意即由類別的執行個體轉換回實質型別的執行個體)。</span><span class="sxs-lookup"><span data-stu-id="05c7c-171">It is unboxed (that is, converted from an instance of a class back to an instance of a value type) when control returns from a method call that accepts a value type as a by-reference parameter.</span></span> <span data-ttu-id="05c7c-172">需要 Boxed 型別時，有些語言會要求您使用特殊的語法；其他語言則會在需要時自動使用 Boxed 型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-172">Some languages require that you use special syntax when the boxed type is required; others automatically use the boxed type when it is needed.</span></span> <span data-ttu-id="05c7c-173">當您定義實值型別時，會同時定義 Boxed 和 Unboxed 型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-173">When you define a value type, you are defining both the boxed and the unboxed type.</span></span>

### <a name="enumerations"></a><span data-ttu-id="05c7c-174">列舉</span><span class="sxs-lookup"><span data-stu-id="05c7c-174">Enumerations</span></span>

<span data-ttu-id="05c7c-175">列舉 (Enum) 是直接繼承自 [System.Enum](xref:System.Enum) 的實值型別，並且可以為基礎的基本型別數值提供替代名稱。</span><span class="sxs-lookup"><span data-stu-id="05c7c-175">An enumeration (enum) is a value type that inherits directly from [System.Enum](xref:System.Enum) and that supplies alternate names for the values of an underlying primitive type.</span></span> <span data-ttu-id="05c7c-176">列舉型別具有名稱、必須為內建帶正負號或不帶正負號之整數型別 (例如 [Byte](xref:System.Byte)、[Int32](xref:System.Int32) 或 [UInt64](xref:System.UInt64)) 的基礎型別，以及一組欄位。</span><span class="sxs-lookup"><span data-stu-id="05c7c-176">An enumeration type has a name, an underlying type that must be one of the built-in signed or unsigned integer types (such as [Byte](xref:System.Byte), [Int32](xref:System.Int32), or [UInt64](xref:System.UInt64)), and a set of fields.</span></span> <span data-ttu-id="05c7c-177">欄位為靜態的常值欄位，每一個欄位各代表一個常數。</span><span class="sxs-lookup"><span data-stu-id="05c7c-177">The fields are static literal fields, each of which represents a constant.</span></span> <span data-ttu-id="05c7c-178">相同的數值可指定給多個欄位。</span><span class="sxs-lookup"><span data-stu-id="05c7c-178">The same value can be assigned to multiple fields.</span></span> <span data-ttu-id="05c7c-179">發生這種情況時，必須將其中一個數值標記為反映和字串轉換的主要列舉值。</span><span class="sxs-lookup"><span data-stu-id="05c7c-179">When this occurs, you must mark one of the values as the primary enumeration value for reflection and string conversion.</span></span>

<span data-ttu-id="05c7c-180">您可以將基礎型別的值指定給列舉型別，反之亦然 (Runtime 不需要轉型)。</span><span class="sxs-lookup"><span data-stu-id="05c7c-180">You can assign a value of the underlying type to an enumeration and vice versa (no cast is required by the runtime).</span></span> <span data-ttu-id="05c7c-181">您可以建立列舉的執行個體，然後呼叫 [System.Enum](xref:System.Enum) 的方法以及在列舉的基礎型別上定義的任何方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-181">You can create an instance of an enumeration and call the methods of [System.Enum](xref:System.Enum), as well as any methods defined on the enumeration's underlying type.</span></span> <span data-ttu-id="05c7c-182">但是，在需要基礎型別的執行個體時，有些語言可能不允許您將列舉型別當成參數傳遞，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="05c7c-182">However, some languages might not let you pass an enumeration as a parameter when an instance of the underlying type is required (or vice versa).</span></span>

<span data-ttu-id="05c7c-183">下列限制適用於列舉型別：</span><span class="sxs-lookup"><span data-stu-id="05c7c-183">The following additional restrictions apply to enumerations:</span></span> 

* <span data-ttu-id="05c7c-184">不能定義自己的方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-184">They cannot define their own methods.</span></span>

* <span data-ttu-id="05c7c-185">不能實作介面。</span><span class="sxs-lookup"><span data-stu-id="05c7c-185">They cannot implement interfaces.</span></span>

* <span data-ttu-id="05c7c-186">不能定義屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="05c7c-186">They cannot define properties or events.</span></span>

* <span data-ttu-id="05c7c-187">除非是巢狀置於泛型型別中，否則不能是泛型。</span><span class="sxs-lookup"><span data-stu-id="05c7c-187">They cannot be generic, unless they are generic only because they are nested within a generic type.</span></span> <span data-ttu-id="05c7c-188">換句話說，列舉型別不能有自己的型別參數。</span><span class="sxs-lookup"><span data-stu-id="05c7c-188">That is, an enumeration cannot have type parameters of its own.</span></span> 

> [!NOTE]
> <span data-ttu-id="05c7c-189">使用 C# 建立的巢狀型別 (包括列舉) 包含所有封入泛型型別的型別參數，因此即使沒有自己的型別參數，仍舊是泛型型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-189">Nested types (including enumerations) created with C# include the type parameters of all enclosing generic types, and are therefore generic even if they do not have type parameters of their own.</span></span> <span data-ttu-id="05c7c-190">如需詳細資訊，請參閱 [Type.MakeGenericType](xref:System.Type.MakeGenericType(System.Type[])) 參考主題。</span><span class="sxs-lookup"><span data-stu-id="05c7c-190">For more information, see the [Type.MakeGenericType](xref:System.Type.MakeGenericType(System.Type[])) reference topic.</span></span> 

<span data-ttu-id="05c7c-191">[FlagsAttribute](xref:System.FlagsAttribute) 屬性代表一種特殊的列舉，稱為位元欄位。</span><span class="sxs-lookup"><span data-stu-id="05c7c-191">The [FlagsAttribute](xref:System.FlagsAttribute) attribute denotes a special kind of enumeration called a bit field.</span></span> <span data-ttu-id="05c7c-192">Runtime 本身無法區別傳統列舉型別和位元欄位，但是您所使用的語言或許可以區分出來。</span><span class="sxs-lookup"><span data-stu-id="05c7c-192">The runtime itself does not distinguish between traditional enumerations and bit fields, but your language might do so.</span></span> <span data-ttu-id="05c7c-193">在區分時，可在位元欄位上使用位元 (Bitwise) 運算子來產生未命名的數值，但是不能用於列舉型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-193">When this distinction is made, bitwise operators can be used on bit fields, but not on enumerations, to generate unnamed values.</span></span> <span data-ttu-id="05c7c-194">列舉型別通常用於唯一的項目 (Element) 清單，例如該星期的天數、國別或區域名稱等。</span><span class="sxs-lookup"><span data-stu-id="05c7c-194">Enumerations are generally used for lists of unique elements, such as days of the week, country or region names, and so on.</span></span> <span data-ttu-id="05c7c-195">位元欄位通常用於可能以組合形式出現的特性或數量清單，例如 `Red And Big And Fast`。</span><span class="sxs-lookup"><span data-stu-id="05c7c-195">Bit fields are generally used for lists of qualities or quantities that might occur in combination, such as `Red And Big And Fast`.</span></span>

<span data-ttu-id="05c7c-196">下列範例顯示如何使用位元欄位和傳統列舉型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-196">The following example shows how to use both bit fields and traditional enumerations.</span></span>

```csharp
using System;
using System.Collections.Generic;

// A traditional enumeration of some root vegetables.
public enum SomeRootVegetables
{
    HorseRadish,
    Radish,
    Turnip
}

// A bit field or flag enumeration of harvesting seasons.
[Flags]
public enum Seasons
{
    None = 0,
    Summer = 1,
    Autumn = 2,
    Winter = 4,
    Spring = 8,
    All = Summer | Autumn | Winter | Spring
}

public class Example
{
   public static void Main()
   {
       // Hash table of when vegetables are available.
       Dictionary<SomeRootVegetables, Seasons> AvailableIn = new Dictionary<SomeRootVegetables, Seasons>();

       AvailableIn[SomeRootVegetables.HorseRadish] = Seasons.All;
       AvailableIn[SomeRootVegetables.Radish] = Seasons.Spring;
       AvailableIn[SomeRootVegetables.Turnip] = Seasons.Spring | 
            Seasons.Autumn;

       // Array of the seasons, using the enumeration.
       Seasons[] theSeasons = new Seasons[] { Seasons.Summer, Seasons.Autumn, 
            Seasons.Winter, Seasons.Spring };

       // Print information of what vegetables are available each season.
       foreach (Seasons season in theSeasons)
       {
          Console.Write(String.Format(
              "The following root vegetables are harvested in {0}:\n", 
              season.ToString("G")));
          foreach (KeyValuePair<SomeRootVegetables, Seasons> item in AvailableIn)
          {
             // A bitwise comparison.
             if (((Seasons)item.Value & season) > 0)
                 Console.Write(String.Format("  {0:G}\n", 
                      (SomeRootVegetables)item.Key));
          }
       }
   }
}
// The example displays the following output:
//    The following root vegetables are harvested in Summer:
//      HorseRadish
//    The following root vegetables are harvested in Autumn:
//      Turnip
//      HorseRadish
//    The following root vegetables are harvested in Winter:
//      HorseRadish
//    The following root vegetables are harvested in Spring:
//      Turnip
//      Radish
//      HorseRadish
```

```vb
Imports System.Collections.Generic

' A traditional enumeration of some root vegetables.
Public Enum SomeRootVegetables
   HorseRadish
   Radish
   Turnip
End Enum 

' A bit field or flag enumeration of harvesting seasons.
<Flags()> Public Enum Seasons
   None = 0
   Summer = 1
   Autumn = 2
   Winter = 4
   Spring = 8
   All = Summer Or Autumn Or Winter Or Spring
End Enum 

' Entry point.
Public Class Example
   Public Shared Sub Main()
      ' Hash table of when vegetables are available.
      Dim AvailableIn As New Dictionary(Of SomeRootVegetables, Seasons)()

      AvailableIn(SomeRootVegetables.HorseRadish) = Seasons.All
      AvailableIn(SomeRootVegetables.Radish) = Seasons.Spring
      AvailableIn(SomeRootVegetables.Turnip) = Seasons.Spring Or _
                                               Seasons.Autumn

      ' Array of the seasons, using the enumeration.
      Dim theSeasons() As Seasons = {Seasons.Summer, Seasons.Autumn, _
                                     Seasons.Winter, Seasons.Spring}

      ' Print information of what vegetables are available each season.
      For Each season As Seasons In theSeasons
         Console.WriteLine(String.Format( _
              "The following root vegetables are harvested in {0}:", _
              season.ToString("G")))
         For Each item As KeyValuePair(Of SomeRootVegetables, Seasons) In AvailableIn
            ' A bitwise comparison.
            If(CType(item.Value, Seasons) And season) > 0 Then
               Console.WriteLine("  " + _
                     CType(item.Key, SomeRootVegetables).ToString("G"))
            End If
         Next
      Next
   End Sub 
End Class 
' The example displays the following output:
'    The following root vegetables are harvested in Summer:
'      HorseRadish
'    The following root vegetables are harvested in Autumn:
'      Turnip
'      HorseRadish
'    The following root vegetables are harvested in Winter:
'      HorseRadish
'    The following root vegetables are harvested in Spring:
'      Turnip
'      Radish
'      HorseRadish
```

### <a name="interfaces"></a><span data-ttu-id="05c7c-197">介面</span><span class="sxs-lookup"><span data-stu-id="05c7c-197">Interfaces</span></span>

<span data-ttu-id="05c7c-198">介面會定義指定「可以執行」關聯性 (Relationship) 或「擁有」關聯性的合約。</span><span class="sxs-lookup"><span data-stu-id="05c7c-198">An interface defines a contract that specifies a "can do" relationship or a "has a" relationship.</span></span> <span data-ttu-id="05c7c-199">介面常用來實作功能，例如比較和排序 ([IComparable](xref:System.IComparable) 和 [IComparable&lt;T&gt;](xref:System.IComparable%601) 介面)、測試是否相等 ([IEquatable&lt;T&gt;](xref:System.IEquatable%601) 介面)，或列舉集合中的項目 ([IEnumerable](xref:System.Collections.IEnumerable) 和 [IEnumerable&lt;T&gt;](xref:System.Collections.Generic.IEnumerable%601) 介面)。</span><span class="sxs-lookup"><span data-stu-id="05c7c-199">Interfaces are often used to implement functionality, such as comparing and sorting (the [IComparable](xref:System.IComparable) and [IComparable&lt;T&gt;](xref:System.IComparable%601) interfaces), testing for equality (the [IEquatable&lt;T&gt;](xref:System.IEquatable%601) interface), or enumerating items in a collection (the [IEnumerable](xref:System.Collections.IEnumerable) and [IEnumerable&lt;T&gt;](xref:System.Collections.Generic.IEnumerable%601) interfaces).</span></span> <span data-ttu-id="05c7c-200">介面可以擁有屬性、方法和事件，這些都是抽象成員，也就是說，雖然介面會定義成員及其簽章，但每個介面成員的功能則是由實作介面的型別所定義。</span><span class="sxs-lookup"><span data-stu-id="05c7c-200">Interfaces can have properties, methods, and events, all of which are abstract members; that is, although the interface defines the members and their signatures, it leaves it to the type that implements the interface to define the functionality of each interface member.</span></span> <span data-ttu-id="05c7c-201">這表示，實作介面的任何類別或結構都必須為介面中宣告的抽象成員提供定義。</span><span class="sxs-lookup"><span data-stu-id="05c7c-201">This means that any class or structure that implements an interface must supply definitions for the abstract members declared in the interface.</span></span> <span data-ttu-id="05c7c-202">介面可能會要求任何實作類別或結構也必須實作一個或多個其他介面。</span><span class="sxs-lookup"><span data-stu-id="05c7c-202">An interface can require any implementing class or structure to also implement one or more other interfaces.</span></span>

<span data-ttu-id="05c7c-203">下列限制適用於介面：</span><span class="sxs-lookup"><span data-stu-id="05c7c-203">The following restrictions apply to interfaces:</span></span> 

* <span data-ttu-id="05c7c-204">介面可宣告為任何存取範圍，但是介面成員必須全部具有公用存取範圍。</span><span class="sxs-lookup"><span data-stu-id="05c7c-204">An interface can be declared with any accessibility, but interface members must all have public accessibility.</span></span>

* <span data-ttu-id="05c7c-205">介面無法定義建構函式。</span><span class="sxs-lookup"><span data-stu-id="05c7c-205">Interfaces cannot define constructors.</span></span>

* <span data-ttu-id="05c7c-206">介面不能定義欄位。</span><span class="sxs-lookup"><span data-stu-id="05c7c-206">Interfaces cannot define fields.</span></span>

* <span data-ttu-id="05c7c-207">介面可以只定義執行個體成員，</span><span class="sxs-lookup"><span data-stu-id="05c7c-207">Interfaces can define only instance members.</span></span> <span data-ttu-id="05c7c-208">不能定義靜態成員。</span><span class="sxs-lookup"><span data-stu-id="05c7c-208">They cannot define static members.</span></span>

<span data-ttu-id="05c7c-209">由於可以使用相同簽章宣告成員的介面不只一個，而且這些成員可以具有分開的實作，因此每一種語言都必須提供規則，將實作對應到需要成員的介面。</span><span class="sxs-lookup"><span data-stu-id="05c7c-209">Each language must provide rules for mapping an implementation to the interface that requires the member, because more than one interface can declare a member with the same signature, and these members can have separate implementations.</span></span>

### <a name="delegates"></a><span data-ttu-id="05c7c-210">委派</span><span class="sxs-lookup"><span data-stu-id="05c7c-210">Delegates</span></span>

<span data-ttu-id="05c7c-211">委派是參考型別，用途與 C++ 中的函式指標類似。</span><span class="sxs-lookup"><span data-stu-id="05c7c-211">Delegates are reference types that serve a purpose similar to that of function pointers in C++.</span></span> <span data-ttu-id="05c7c-212">委派是用於 .NET 中的事件處理常式和回呼函式。</span><span class="sxs-lookup"><span data-stu-id="05c7c-212">They are used for event handlers and callback functions in .NET.</span></span> <span data-ttu-id="05c7c-213">不同於函式指標，委派更具安全性、可以驗證，而且是型別安全 (Type Safe) 的。</span><span class="sxs-lookup"><span data-stu-id="05c7c-213">Unlike function pointers, delegates are secure, verifiable, and type safe.</span></span> <span data-ttu-id="05c7c-214">委派型別可以代表具有相容簽章的執行個體方法或靜態方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-214">A delegate type can represent any instance method or static method that has a compatible signature.</span></span> 

<span data-ttu-id="05c7c-215">如果委派參數的型別比方法參數的型別更嚴格，則委派的參數與對應的方法參數相容，因為這樣可保證傳遞給委派的引數能夠安全地傳遞給方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-215">A parameter of a delegate is compatible with the corresponding parameter of a method if the type of the delegate parameter is more restrictive than the type of the method parameter, because this guarantees that an argument passed to the delegate can be passed safely to the method.</span></span>

<span data-ttu-id="05c7c-216">同樣的，如果方法的傳回型別比委派的傳回型別更具限制性，由於此保證方法傳回的值會安全地轉換為委派的傳回型別，委派的傳回型別就會相容於方法的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-216">Similarly, the return type of a delegate is compatible with the return type of a method if the return type of the method is more restrictive than the return type of the delegate, because this guarantees that the return value of the method can be cast safely to the return type of the delegate.</span></span>

<span data-ttu-id="05c7c-217">例如，具有 [IEnumerable](xref:System.Collections.IEnumerable) 型別參數和 [Object](xref:System.Object) 傳回型別的委派，即可代表具有 [Object](xref:System.Object) 型別參數和 [IEnumerable](xref:System.Collections.IEnumerable) 型別傳回值的方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-217">For example, a delegate that has a parameter of type [IEnumerable](xref:System.Collections.IEnumerable) and a return type of [Object](xref:System.Object) can represent a method that has a parameter of type [Object](xref:System.Object) and a return value of type [IEnumerable](xref:System.Collections.IEnumerable).</span></span> 

 <span data-ttu-id="05c7c-218">委派會繫結到其所代表的方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-218">A delegate is said to be bound to the method it represents.</span></span> <span data-ttu-id="05c7c-219">除了繫結到方法以外，委派還可以繫結到物件。</span><span class="sxs-lookup"><span data-stu-id="05c7c-219">In addition to being bound to the method, a delegate can be bound to an object.</span></span> <span data-ttu-id="05c7c-220">物件表示方法的第一個參數，而且每一次叫用委派時，都會傳遞給方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-220">The object represents the first parameter of the method, and is passed to the method every time the delegate is invoked.</span></span> <span data-ttu-id="05c7c-221">如果方法是執行個體方法，那麼繫結物件會傳遞做為隱含的 `this` 參數 (Visual Basic 中則為 `Me`)；如果是靜態方法，物件會傳遞做為方法的第一個正式參數，而且委派簽章必須符合其餘參數。</span><span class="sxs-lookup"><span data-stu-id="05c7c-221">If the method is an instance method, the bound object is passed as the implicit `this` parameter (`Me` in Visual Basic); if the method is static, the object is passed as the first formal parameter of the method, and the delegate signature must match the remaining parameters.</span></span> 
 
 <span data-ttu-id="05c7c-222">所有的委派都繼承自 [System.MulticastDelegate](xref:System.MulticastDelegate)，該項則繼承自 [System.Delegate](xref:System.Delegate)。</span><span class="sxs-lookup"><span data-stu-id="05c7c-222">All delegates inherit from [System.MulticastDelegate](xref:System.MulticastDelegate), which inherits from [System.Delegate](xref:System.Delegate).</span></span> <span data-ttu-id="05c7c-223">C# 和 Visual Basic 語言並不允許從這些型別繼承，</span><span class="sxs-lookup"><span data-stu-id="05c7c-223">The C# and Visual Basic languages don't allow inheritance from these types.</span></span> <span data-ttu-id="05c7c-224">而是提供關鍵字以宣告委派。</span><span class="sxs-lookup"><span data-stu-id="05c7c-224">Instead, they provide keywords for declaring delegates.</span></span>
 
 <span data-ttu-id="05c7c-225">由於委派繼承自 [MulticastDelegate](xref:System.MulticastDelegate)，所以委派會具有引動過程清單，這是委派所代表方法的清單，在叫用委派時就會執行這些方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-225">Because delegates inherit from [MulticastDelegate](xref:System.MulticastDelegate), a delegate has an invocation list, which is a list of methods that the delegate represents and that are executed when the delegate is invoked.</span></span> <span data-ttu-id="05c7c-226">清單中的所有方法都會接收到叫用委派時所提供的引數。</span><span class="sxs-lookup"><span data-stu-id="05c7c-226">All methods in the list receive the arguments supplied when the delegate is invoked.</span></span>

> [!NOTE]
> <span data-ttu-id="05c7c-227">在引動過程清單中具有一個以上方法的委派，即使擁有傳回型別，其傳回值也不會具有定義。</span><span class="sxs-lookup"><span data-stu-id="05c7c-227">The return value is not defined for a delegate that has more than one method in its invocation list, even if the delegate has a return type.</span></span>

<span data-ttu-id="05c7c-228">在許多情況下，例如回呼方法中，委派只代表一個方法，而且您所需要採取的動作，就是建立委派然後再叫用委派。</span><span class="sxs-lookup"><span data-stu-id="05c7c-228">In many cases, such as with callback methods, a delegate represents only one method, and the only actions you have to take are creating the delegate and invoking it.</span></span> 

<span data-ttu-id="05c7c-229">對於代表多個方法的委派，.NET 提供 [Delegate](xref:System.Delegate) 和 [MulticastDelegate](xref:System.MulticastDelegate) 委派類別的方法，來支援對委派的引動過程清單加入方法 ([Delegate.Combine](xref:System.Delegate.Combine(System.Delegate,System.Delegate)) 方法)、移除方法 ([Delegate.Remove](xref:System.Delegate.Remove(System.Delegate,System.Delegate)) 方法)，以及取得引動過程清單 ([Delegate.GetInvocationList](xref:System.Delegate.GetInvocationList) 方法) 的諸如此類作業。</span><span class="sxs-lookup"><span data-stu-id="05c7c-229">For delegates that represent multiple methods, .NET provides methods of the [Delegate](xref:System.Delegate) and [MulticastDelegate](xref:System.MulticastDelegate) delegate classes to support operations such as adding a method to a delegate's invocation list (the [Delegate.Combine](xref:System.Delegate.Combine(System.Delegate,System.Delegate)) method), removing a method (the [Delegate.Remove](xref:System.Delegate.Remove(System.Delegate,System.Delegate)) method), and getting the invocation list (the [Delegate.GetInvocationList](xref:System.Delegate.GetInvocationList) method).</span></span>

> [!NOTE]
> <span data-ttu-id="05c7c-230">在 C# 或 Visual Basic 中，並不需要對事件處理常式委派使用這些方法，因為這些語言都提供加入和移除事件處理常式的語法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-230">It is not necessary to use these methods for event-handler delegates in C# or Visual Basic, because these languages provide syntax for adding and removing event handlers.</span></span>

## <a name="type-definitions"></a><span data-ttu-id="05c7c-231">型別定義</span><span class="sxs-lookup"><span data-stu-id="05c7c-231">Type definitions</span></span>

<span data-ttu-id="05c7c-232">型別定義包括下列：</span><span class="sxs-lookup"><span data-stu-id="05c7c-232">A type definition includes the following:</span></span> 

* <span data-ttu-id="05c7c-233">在型別上定義的任何屬性 (Attribute)</span><span class="sxs-lookup"><span data-stu-id="05c7c-233">Any attributes defined on the type.</span></span>

* <span data-ttu-id="05c7c-234">型別的存取範圍 (可視性)</span><span class="sxs-lookup"><span data-stu-id="05c7c-234">The type's accessibility (visibility).</span></span>

* <span data-ttu-id="05c7c-235">型別的名稱</span><span class="sxs-lookup"><span data-stu-id="05c7c-235">The type's name.</span></span>

* <span data-ttu-id="05c7c-236">型別的基底型別</span><span class="sxs-lookup"><span data-stu-id="05c7c-236">The type's base type.</span></span>

* <span data-ttu-id="05c7c-237">由型別實作的任何介面</span><span class="sxs-lookup"><span data-stu-id="05c7c-237">Any interfaces implemented by the type.</span></span>

* <span data-ttu-id="05c7c-238">型別中每一個成員的定義</span><span class="sxs-lookup"><span data-stu-id="05c7c-238">Definitions for each of the type's members.</span></span>

### <a name="attributes"></a><span data-ttu-id="05c7c-239">屬性</span><span class="sxs-lookup"><span data-stu-id="05c7c-239">Attributes</span></span>

<span data-ttu-id="05c7c-240">屬性提供了其他的使用者定義中繼資料。</span><span class="sxs-lookup"><span data-stu-id="05c7c-240">Attributes provide additional user-defined metadata.</span></span> <span data-ttu-id="05c7c-241">最常見的屬性用法是，用來將關於型別的其他資訊儲存在組件中，或者在設計階段或執行階段環境中修改型別成員的行為。</span><span class="sxs-lookup"><span data-stu-id="05c7c-241">Most commonly, they are used to store additional information about a type in its assembly, or to modify the behavior of a type member in either the design-time or run-time environment.</span></span> 

<span data-ttu-id="05c7c-242">屬性本身都是繼承自 [System.Attribute](xref:System.Attribute) 的類別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-242">Attributes are themselves classes that inherit from [System.Attribute](xref:System.Attribute).</span></span> <span data-ttu-id="05c7c-243">每一種支援使用屬性的語言都有自己的語法，用於將屬性套用至語言項目。</span><span class="sxs-lookup"><span data-stu-id="05c7c-243">Languages that support the use of attributes each have their own syntax for applying attributes to a language element.</span></span> <span data-ttu-id="05c7c-244">屬性可以幾乎套用至所有語言項目，而可以套用屬性的特定項目是由套用到該屬性類別的 [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) 定義。</span><span class="sxs-lookup"><span data-stu-id="05c7c-244">Attributes can be applied to almost any language element; the specific elements to which an attribute can be applied are defined by the [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) that is applied to that attribute class.</span></span>

### <a name="type-accessibility"></a><span data-ttu-id="05c7c-245">類型存取範圍</span><span class="sxs-lookup"><span data-stu-id="05c7c-245">Type accessibility</span></span>

<span data-ttu-id="05c7c-246">所有型別都具有修飾詞 (Modifier)，負責控制其他型別的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="05c7c-246">All types have a modifier that governs their accessibility from other types.</span></span> <span data-ttu-id="05c7c-247">下表說明執行階段所支援的型別存取範圍。</span><span class="sxs-lookup"><span data-stu-id="05c7c-247">The following table describes the type accessibilities supported by the runtime.</span></span>

<span data-ttu-id="05c7c-248">協助工具選項</span><span class="sxs-lookup"><span data-stu-id="05c7c-248">Accessibility</span></span> | <span data-ttu-id="05c7c-249">描述</span><span class="sxs-lookup"><span data-stu-id="05c7c-249">Description</span></span>
------------- | -----------
<span data-ttu-id="05c7c-250">public</span><span class="sxs-lookup"><span data-stu-id="05c7c-250">public</span></span> | <span data-ttu-id="05c7c-251">型別可供所有組件存取</span><span class="sxs-lookup"><span data-stu-id="05c7c-251">The type is accessible by all assemblies.</span></span>
<span data-ttu-id="05c7c-252">組件</span><span class="sxs-lookup"><span data-stu-id="05c7c-252">assembly</span></span> | <span data-ttu-id="05c7c-253">型別只能在本身的組件中存取</span><span class="sxs-lookup"><span data-stu-id="05c7c-253">The type is accessible only from within its assembly.</span></span>

<span data-ttu-id="05c7c-254">巢狀型別的存取範圍是依據其存取範圍定義域，由成員的宣告存取範圍和立即包含型別的存取範圍定義域來決定。</span><span class="sxs-lookup"><span data-stu-id="05c7c-254">The accessibility of a nested type depends on its accessibility domain, which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="05c7c-255">但是，巢狀型別的存取範圍領域不能超過包含型別 (Containing Type) 的存取範圍領域。</span><span class="sxs-lookup"><span data-stu-id="05c7c-255">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>

<span data-ttu-id="05c7c-256">在程式 `P` 的型別 `T` 中宣告的巢狀成員 `M`，它的存取範圍領域定義如下 (請注意，`M` 本身也可能是型別)：</span><span class="sxs-lookup"><span data-stu-id="05c7c-256">The accessibility domain of a nested member `M` declared in a type `T`within a program `P` is defined as follows (noting that `M` might itself be a type):</span></span> 

* <span data-ttu-id="05c7c-257">如果 `M` 的宣告存取範圍是 `public`，`M` 的存取範圍領域就是 `T` 的存取範圍領域。</span><span class="sxs-lookup"><span data-stu-id="05c7c-257">If the declared accessibility of `M` is `public`, the accessibility domain of `M` is the accessibility domain of `T`.</span></span>

* <span data-ttu-id="05c7c-258">如果 `M` 的宣告存取範圍是 `protected internal`，`M` 的存取範圍領域是 `T` 的存取範圍領域與 `P` 的程式文字和從 `T` 以外宣告的 `P` 所衍生任何型別的程式文字的交集。</span><span class="sxs-lookup"><span data-stu-id="05c7c-258">If the declared accessibility of `M` is `protected internal`, the accessibility domain of `M` is the intersection of the accessibility domain of `T` with the program text of `P` and the program text of any type derived from `T` declared outside `P`.</span></span>

* <span data-ttu-id="05c7c-259">如果 `M` 的宣告存取範圍是 `protected`，`M` 的存取範圍領域是 `T` 的存取範圍領域與 `T` 的程式文字和 `T` 所衍生之任一型別的交集。</span><span class="sxs-lookup"><span data-stu-id="05c7c-259">If the declared accessibility of `M` is `protected`, the accessibility domain of `M` is the intersection of the accessibility domain of `T` with the program text of `T` and any type derived from `T`.</span></span>

* <span data-ttu-id="05c7c-260">如果 `M` 的宣告存取範圍是 `internal`，`M` 的存取範圍領域是 `T` 的存取範圍領域與 `P` 的程式文字的交集。</span><span class="sxs-lookup"><span data-stu-id="05c7c-260">If the declared accessibility of `M` is `internal`, the accessibility domain of `M` is the intersection of the accessibility domain of `T` with the program text of`P`.</span></span>

* <span data-ttu-id="05c7c-261">如果 `M` 的宣告存取範圍是 `private`，`M` 的存取範圍領域就是 `T` 的程式文字。</span><span class="sxs-lookup"><span data-stu-id="05c7c-261">If the declared accessibility of `M` is `private`, the accessibility domain of `M` is the program text of `T`.</span></span>

### <a name="type-names"></a><span data-ttu-id="05c7c-262">型別名稱</span><span class="sxs-lookup"><span data-stu-id="05c7c-262">Type names</span></span>

<span data-ttu-id="05c7c-263">一般型別系統對於名稱只有兩項限制：</span><span class="sxs-lookup"><span data-stu-id="05c7c-263">The common type system imposes only two restrictions on names:</span></span> 

* <span data-ttu-id="05c7c-264">所有名稱都是以 Unicode (16 位元) 字元字串的方式編碼。</span><span class="sxs-lookup"><span data-stu-id="05c7c-264">All names are encoded as strings of Unicode (16-bit) characters.</span></span>

* <span data-ttu-id="05c7c-265">名稱的內嵌 (16 位元) 值不允許為 0x0000。</span><span class="sxs-lookup"><span data-stu-id="05c7c-265">Names are not permitted to have an embedded (16-bit) value of 0x0000.</span></span>

<span data-ttu-id="05c7c-266">然而，大部分語言會對型別名稱強制執行其他限制。</span><span class="sxs-lookup"><span data-stu-id="05c7c-266">However, most languages impose additional restrictions on type names.</span></span> <span data-ttu-id="05c7c-267">所有比較都是以位元組為基礎，因此會區分大小寫，而且與地區設定無關 (Locale-Independent)。</span><span class="sxs-lookup"><span data-stu-id="05c7c-267">All comparisons are done on a byte-by-byte basis, and are therefore case-sensitive and locale-independent.</span></span>

<span data-ttu-id="05c7c-268">雖然型別可能會參考其他模組和組件中的型別，但是型別必須在一個 .NET 模組中完整定義</span><span class="sxs-lookup"><span data-stu-id="05c7c-268">Although a type might reference types from other modules and assemblies, a type must be fully defined within one .NET module.</span></span> <span data-ttu-id="05c7c-269">(不過根據編譯器的支援，它可以分割成多個原始程式碼檔)。只有在命名空間中的型別名稱才必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="05c7c-269">(Depending on compiler support, however, it can be divided into multiple source code files.) Type names need be unique only within a namespace.</span></span> <span data-ttu-id="05c7c-270">若要能完整辨認型別，必須以包含型別實作的命名空間來限定型別名稱。</span><span class="sxs-lookup"><span data-stu-id="05c7c-270">To fully identify a type, the type name must be qualified by the namespace that contains the implementation of the type.</span></span>

### <a name="base-types-and-interfaces"></a><span data-ttu-id="05c7c-271">基底類型及介面</span><span class="sxs-lookup"><span data-stu-id="05c7c-271">Base types and interfaces</span></span>

<span data-ttu-id="05c7c-272">型別可繼承其他型別的數值和行為。</span><span class="sxs-lookup"><span data-stu-id="05c7c-272">A type can inherit values and behaviors from another type.</span></span> <span data-ttu-id="05c7c-273">一般型別系統不允許型別繼承一個以上的基底型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-273">The common type system does not allow types to inherit from more than one base type.</span></span>

<span data-ttu-id="05c7c-274">型別可實作任意數目的介面。</span><span class="sxs-lookup"><span data-stu-id="05c7c-274">A type can implement any number of interfaces.</span></span> <span data-ttu-id="05c7c-275">若要實作介面，型別必須實作該介面的所有虛擬成員。</span><span class="sxs-lookup"><span data-stu-id="05c7c-275">To implement an interface, a type must implement all the virtual members of that interface.</span></span> <span data-ttu-id="05c7c-276">虛擬方法可由衍生型別 (Derived Type) 實作，並且可以用靜態或動態方式叫用 (Invoke)。</span><span class="sxs-lookup"><span data-stu-id="05c7c-276">A virtual method can be implemented by a derived type and can be invoked either statically or dynamically.</span></span>

## <a name="type-members"></a><span data-ttu-id="05c7c-277">類型成員</span><span class="sxs-lookup"><span data-stu-id="05c7c-277">Type members</span></span>

<span data-ttu-id="05c7c-278">執行階段允許您定義能夠指定型別行為與狀態的型別成員。</span><span class="sxs-lookup"><span data-stu-id="05c7c-278">The runtime enables you to define members of your type, which specifies the behavior and state of a type.</span></span> <span data-ttu-id="05c7c-279">型別成員包含下列：</span><span class="sxs-lookup"><span data-stu-id="05c7c-279">Type members include the following:</span></span>

* [<span data-ttu-id="05c7c-280">欄位</span><span class="sxs-lookup"><span data-stu-id="05c7c-280">Fields</span></span>](#fields)

* [<span data-ttu-id="05c7c-281">屬性</span><span class="sxs-lookup"><span data-stu-id="05c7c-281">Properties</span></span>](#properties)

* [<span data-ttu-id="05c7c-282">方法</span><span class="sxs-lookup"><span data-stu-id="05c7c-282">Methods</span></span>](#methods)

* [<span data-ttu-id="05c7c-283">建構函式</span><span class="sxs-lookup"><span data-stu-id="05c7c-283">Constructors</span></span>](#constructors)

* [<span data-ttu-id="05c7c-284">事件</span><span class="sxs-lookup"><span data-stu-id="05c7c-284">Events</span></span>](#events)

* [<span data-ttu-id="05c7c-285">巢狀類型</span><span class="sxs-lookup"><span data-stu-id="05c7c-285">Nested types</span></span>](#nested-types)

### <a name="fields"></a><span data-ttu-id="05c7c-286">欄位</span><span class="sxs-lookup"><span data-stu-id="05c7c-286">Fields</span></span>

<span data-ttu-id="05c7c-287">欄位會描述並包含型別狀態組件。</span><span class="sxs-lookup"><span data-stu-id="05c7c-287">A field describes and contains part of the type's state.</span></span> <span data-ttu-id="05c7c-288">欄位可為執行階段支援的任何型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-288">Fields can be of any type supported by the runtime.</span></span> <span data-ttu-id="05c7c-289">最常見的情形是，欄位為 `private` 或 `protected`，如此才能夠只在類別內部或從衍生類別存取這些欄位。</span><span class="sxs-lookup"><span data-stu-id="05c7c-289">Most commonly, fields are either `private` or `protected`, so that they are accessible only from within the class or from a derived class.</span></span> <span data-ttu-id="05c7c-290">如果欄位的值可以本身型別以外進行修改，則通常會使用屬性集存取子。</span><span class="sxs-lookup"><span data-stu-id="05c7c-290">If the value of a field can be modified from outside its type, a property set accessor is typically used.</span></span> <span data-ttu-id="05c7c-291">公開欄位通常是唯讀的，而且可以是下兩種型別：</span><span class="sxs-lookup"><span data-stu-id="05c7c-291">Publicly exposed fields are usually read-only and can be of two types:</span></span> 

* <span data-ttu-id="05c7c-292">常數，它的值是在設計階段指派。</span><span class="sxs-lookup"><span data-stu-id="05c7c-292">Constants, whose value is assigned at design time.</span></span> <span data-ttu-id="05c7c-293">雖然並不會使用 `static` (Visual Basic 中則為 `Shared`) 關鍵字定義，但是這些常數都是類別的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="05c7c-293">These are static members of a class, although they are not defined using the `static` (`Shared` in Visual Basic) keyword.</span></span>

* <span data-ttu-id="05c7c-294">唯讀變數，其值可以在類別建構函式中進行指派。</span><span class="sxs-lookup"><span data-stu-id="05c7c-294">Read-only variables, whose values can be assigned in the class constructor.</span></span>

<span data-ttu-id="05c7c-295">下列範例說明兩種唯讀欄位的使用方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-295">The following example illustrates these two usages of read-only fields.</span></span>

```csharp
using System;

public class Constants
{
   public const double Pi = 3.1416;
   public readonly DateTime BirthDate;

   public Constants(DateTime birthDate)
   {
      this.BirthDate = birthDate;
   }
}

public class Example
{
   public static void Main()
   {
      Constants con = new Constants(new DateTime(1974, 8, 18));
      Console.Write(Constants.Pi + "\n");
      Console.Write(con.BirthDate.ToString("d") + "\n");
   }
}
// The example displays the following output if run on a system whose current
// culture is en-US:
//    3.1417
//    8/18/1974
```

```vb
Public Class Constants
   Public Const Pi As Double = 3.1416
   Public ReadOnly BirthDate As Date

   Public Sub New(birthDate As Date)
      Me.BirthDate = birthDate
   End Sub
End Class

Public Module Example
   Public Sub Main()
      Dim con As New Constants(#8/18/1974#)
      Console.WriteLine(Constants.Pi.ToString())
      Console.WriteLine(con.BirthDate.ToString("d"))
   End Sub
End Module
' The example displays the following output if run on a system whose current
' culture is en-US:
'    3.1417
'    8/18/1974
```

### <a name="properties"></a><span data-ttu-id="05c7c-296">屬性</span><span class="sxs-lookup"><span data-stu-id="05c7c-296">Properties</span></span>

<span data-ttu-id="05c7c-297">屬性會為型別的值或狀態命名，並且定義用來取得或設定屬性值的方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-297">A property names a value or state of the type and defines methods for getting or setting the property's value.</span></span> <span data-ttu-id="05c7c-298">屬性可以是基本型別、基本型別的集合、使用者定義型別或使用者定義型別的集合。</span><span class="sxs-lookup"><span data-stu-id="05c7c-298">Properties can be primitive types, collections of primitive types, user-defined types, or collections of user-defined types.</span></span> <span data-ttu-id="05c7c-299">屬性通常是用來保持型別的公用 (Public) 介面與型別的實際表示相互獨立。</span><span class="sxs-lookup"><span data-stu-id="05c7c-299">Properties are often used to keep the public interface of a type independent from the type's actual representation.</span></span> <span data-ttu-id="05c7c-300">這可以讓屬性反映並不直接儲存於類別中的值 (例如，屬性傳回已計算的值時)，或者在值指派給私用欄位之前先執行驗證。</span><span class="sxs-lookup"><span data-stu-id="05c7c-300">This enables properties to reflect values that are not directly stored in the class (for example, when a property returns a computed value) or to perform validation before values are assigned to private fields.</span></span> <span data-ttu-id="05c7c-301">下列範例說明第二種模式。</span><span class="sxs-lookup"><span data-stu-id="05c7c-301">The following example illustrates the latter pattern.</span></span>

```csharp
using System;

public class Person
{
   private int m_Age;

   public int Age
   { 
      get { return m_Age; }
      set {
         if (value < 0 || value > 125)
         {
            throw new ArgumentOutOfRangeException("The value of the Age property must be between 0 and 125.");
         }
         else
         {
            m_Age = value;
         }         
      }
   }
}
```

```vb
Public Class Person
   Private m_Age As Integer

   Public Property Age As Integer
      Get
         Return m_Age
      End Get
      Set
         If value < 0 Or value > 125 Then
            Throw New ArgumentOutOfRangeException("The value of the Age property must be between 0 and 125.")
         Else
            m_Age = value
         End If
      End Set
   End Property
End Class
```

<span data-ttu-id="05c7c-302">除了含有屬性本身之外，包含可讀取屬性之類型的 Microsoft Intermediate Language (MSIL) 也含有 `get`*_propertyname* 方法，而包含可寫入屬性之型別的 MSIL 則含有 `set`*_propertyname* 方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-302">In addition to including the property itself, the Microsoft intermediate language (MSIL) for a type that contains a readable property includes a `get`*_propertyname* method, and the MSIL for a type that contains a writable property includes a `set`*_propertyname* method.</span></span>

### <a name="methods"></a><span data-ttu-id="05c7c-303">方法</span><span class="sxs-lookup"><span data-stu-id="05c7c-303">Methods</span></span>

<span data-ttu-id="05c7c-304">方法會描述可以在類型上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="05c7c-304">A method describes operations that are available on the type.</span></span> <span data-ttu-id="05c7c-305">方法的簽章會指定所有參數和傳回值可使用的型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-305">A method's signature specifies the allowable types of all its parameters and of its return value.</span></span>

<span data-ttu-id="05c7c-306">雖然大部分方法都會針對方法呼叫定義所需的精確參數數目，但有些方法可支援數目不定的參數。</span><span class="sxs-lookup"><span data-stu-id="05c7c-306">Although most methods define the precise number of parameters required for method calls, some methods support a variable number of parameters.</span></span> <span data-ttu-id="05c7c-307">這些方法最後一個宣告的參數是以 [ParamArrayAttribute](xref:System.ParamArrayAttribute) 屬性標記。</span><span class="sxs-lookup"><span data-stu-id="05c7c-307">The final declared parameter of these methods is marked with the [ParamArrayAttribute](xref:System.ParamArrayAttribute) attribute.</span></span> <span data-ttu-id="05c7c-308">語言編譯器通常會提供關鍵字，例如 C# 中的 `params` 和 Visual Basic 中的 `ParamArray`，如此便不需要明確使用 [ParamArrayAttribute](xref:System.ParamArrayAttribute)。</span><span class="sxs-lookup"><span data-stu-id="05c7c-308">Language compilers typically provide a keyword, such as `params` in C# and `ParamArray` in Visual Basic, that makes explicit use of [ParamArrayAttribute](xref:System.ParamArrayAttribute) unnecessary.</span></span>

### <a name="constructors"></a><span data-ttu-id="05c7c-309">建構函式</span><span class="sxs-lookup"><span data-stu-id="05c7c-309">Constructors</span></span>

<span data-ttu-id="05c7c-310">建構函式是一種特殊方法，它會建立類別或結構的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="05c7c-310">A constructor is a special kind of method that creates new instances of a class or structure.</span></span> <span data-ttu-id="05c7c-311">與其他任何方法一樣，建構函式可以包含參數，不過建構函式沒有傳回值，換言之，它們傳回 `void`。</span><span class="sxs-lookup"><span data-stu-id="05c7c-311">Like any other method, a constructor can include parameters; however, constructors have no return value (that is, they return `void`).</span></span> 

<span data-ttu-id="05c7c-312">如果類別的原始程式碼沒有明確定義建構函式，則編譯器會包含預設 (無參數) 建構函式。</span><span class="sxs-lookup"><span data-stu-id="05c7c-312">If the source code for a class does not explicitly define a constructor, the compiler includes a default (parameterless) constructor.</span></span> <span data-ttu-id="05c7c-313">不過，如果類別的原始程式碼只定義參數化建構函式，C# 編譯器並不會產生無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="05c7c-313">However, if the source code for a class defines only parameterized constructors, the C# compiler doesn't generate a parameterless constructor.</span></span>

<span data-ttu-id="05c7c-314">如果結構的原始程式碼定義建構函式，它們必須是參數化建構函式；結構無法定義預設 (無參數) 建構函式，而且編譯器不會產生結構或其他實值型別的無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="05c7c-314">If the source code for a structure defines constructors, they must be parameterized; a structure cannot define a default (parameterless) constructor, and compilers do not generate parameterless constructors for structures or other value types.</span></span> <span data-ttu-id="05c7c-315">所有實值型別都有隱含的預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="05c7c-315">All value types do have an implicit default constructor.</span></span> <span data-ttu-id="05c7c-316">這個建構函式是由 Common Language Runtime 實作，會將結構的所有欄位初始化為其預設值。</span><span class="sxs-lookup"><span data-stu-id="05c7c-316">This constructor is implemented by the common language runtime and initializes all fields of the structure to their default values.</span></span> 

### <a name="events"></a><span data-ttu-id="05c7c-317">事件</span><span class="sxs-lookup"><span data-stu-id="05c7c-317">Events</span></span>

<span data-ttu-id="05c7c-318">事件 (Event) 會定義可以回應的事件 (Incident)，並且定義用於訂閱、取消訂閱和產生事件 (Event) 的方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-318">An event defines an incident that can be responded to, and defines methods for subscribing to, unsubscribing from, and raising the event.</span></span> <span data-ttu-id="05c7c-319">事件通常是用來通知其他型別有狀態變更。</span><span class="sxs-lookup"><span data-stu-id="05c7c-319">Events are often used to inform other types of state changes.</span></span>

### <a name="nested-types"></a><span data-ttu-id="05c7c-320">巢狀型別</span><span class="sxs-lookup"><span data-stu-id="05c7c-320">Nested types</span></span>

<span data-ttu-id="05c7c-321">巢狀型別是一種型別，它是某個其他型別的成員。</span><span class="sxs-lookup"><span data-stu-id="05c7c-321">A nested type is a type that is a member of some other type.</span></span> <span data-ttu-id="05c7c-322">巢狀型別應該緊密地與其包含型別結合，且不能與一般用途的型別一樣實用。</span><span class="sxs-lookup"><span data-stu-id="05c7c-322">Nested types should be tightly coupled to their containing type and must not be useful as a general-purpose type.</span></span> <span data-ttu-id="05c7c-323">當宣告的型別使用及建立巢狀型別的執行個體時，巢狀型別會很有用處，且不會在公用成員中公開此巢狀型別的使用。</span><span class="sxs-lookup"><span data-stu-id="05c7c-323">Nested types are useful when the declaring type uses and creates instances of the nested type, and use of the nested type is not exposed in public members.</span></span>

<span data-ttu-id="05c7c-324">巢狀型別對於一些開發人員來說可能會覺得混淆，所以除非有強制性的理由，否則不應該讓巢狀型別公開可見。</span><span class="sxs-lookup"><span data-stu-id="05c7c-324">Nested types are confusing to some developers and should not be publicly visible unless there is a compelling reason for visibility.</span></span> <span data-ttu-id="05c7c-325">在設計完善的程式庫中，開發人員應極少使用巢狀型別來將物件執行個體化或宣告變數。</span><span class="sxs-lookup"><span data-stu-id="05c7c-325">In a well-designed library, developers should rarely have to use nested types to instantiate objects or declare variables.</span></span>

## <a name="characteristics-of-type-members"></a><span data-ttu-id="05c7c-326">類型成員的特性</span><span class="sxs-lookup"><span data-stu-id="05c7c-326">Characteristics of type members</span></span>

<span data-ttu-id="05c7c-327">一般型別系統允許型別成員具有各種特性，但是所使用的語言並不需要支援所有特性。</span><span class="sxs-lookup"><span data-stu-id="05c7c-327">The common type system allows type members to have a variety of characteristics; however, languages are not required to support all these characteristics.</span></span> <span data-ttu-id="05c7c-328">下表將描述成員特性。</span><span class="sxs-lookup"><span data-stu-id="05c7c-328">The following table describes member characteristics.</span></span>

<span data-ttu-id="05c7c-329">特性</span><span class="sxs-lookup"><span data-stu-id="05c7c-329">Characteristic</span></span> | <span data-ttu-id="05c7c-330">適用於</span><span class="sxs-lookup"><span data-stu-id="05c7c-330">Can apply to</span></span> | <span data-ttu-id="05c7c-331">描述</span><span class="sxs-lookup"><span data-stu-id="05c7c-331">Description</span></span>
-------------- | ------------ | -----------
<span data-ttu-id="05c7c-332">abstract</span><span class="sxs-lookup"><span data-stu-id="05c7c-332">abstract</span></span> | <span data-ttu-id="05c7c-333">方法、屬性和事件</span><span class="sxs-lookup"><span data-stu-id="05c7c-333">Methods, properties, and events</span></span> | <span data-ttu-id="05c7c-334">型別不提供方法的實作。</span><span class="sxs-lookup"><span data-stu-id="05c7c-334">The type does not supply the method's implementation.</span></span> <span data-ttu-id="05c7c-335">繼承或實作抽象方法的型別必須提供方法的實作。</span><span class="sxs-lookup"><span data-stu-id="05c7c-335">Types that inherit or implement abstract methods must supply an implementation for the method.</span></span> <span data-ttu-id="05c7c-336">唯一的例外狀況 (Exception) 是當衍生型別本身也是抽象型別時。</span><span class="sxs-lookup"><span data-stu-id="05c7c-336">The only exception is when the derived type is itself an abstract type.</span></span> <span data-ttu-id="05c7c-337">所有抽象方法都是虛擬的。</span><span class="sxs-lookup"><span data-stu-id="05c7c-337">All abstract methods are virtual.</span></span>
<span data-ttu-id="05c7c-338">private</span><span class="sxs-lookup"><span data-stu-id="05c7c-338">private</span></span> | <span data-ttu-id="05c7c-339">全部</span><span class="sxs-lookup"><span data-stu-id="05c7c-339">All</span></span> | <span data-ttu-id="05c7c-340">只能在與成員相同的型別或巢狀型別中存取。</span><span class="sxs-lookup"><span data-stu-id="05c7c-340">Accessible only from within the same type as the member, or within a nested type.</span></span>
<span data-ttu-id="05c7c-341">family</span><span class="sxs-lookup"><span data-stu-id="05c7c-341">family</span></span> | <span data-ttu-id="05c7c-342">全部</span><span class="sxs-lookup"><span data-stu-id="05c7c-342">All</span></span> | <span data-ttu-id="05c7c-343">可在與成員相同的型別和從它繼承而來的衍生型別中存取。</span><span class="sxs-lookup"><span data-stu-id="05c7c-343">Accessible from within the same type as the member, and from derived types that inherit from it.</span></span>
<span data-ttu-id="05c7c-344">assemby</span><span class="sxs-lookup"><span data-stu-id="05c7c-344">assemby</span></span> | <span data-ttu-id="05c7c-345">全部</span><span class="sxs-lookup"><span data-stu-id="05c7c-345">All</span></span> | <span data-ttu-id="05c7c-346">只能在已定義型別的組件中存取。</span><span class="sxs-lookup"><span data-stu-id="05c7c-346">Accessible only in the assembly in which the type is defined.</span></span>
<span data-ttu-id="05c7c-347">family 和 assembly</span><span class="sxs-lookup"><span data-stu-id="05c7c-347">family and assembly</span></span> | <span data-ttu-id="05c7c-348">全部</span><span class="sxs-lookup"><span data-stu-id="05c7c-348">All</span></span> | <span data-ttu-id="05c7c-349">只能從同時限定家族和組件存取的型別中存取。</span><span class="sxs-lookup"><span data-stu-id="05c7c-349">Accessible only from types that qualify for both family and assembly access.</span></span>
<span data-ttu-id="05c7c-350">family 或 assembly</span><span class="sxs-lookup"><span data-stu-id="05c7c-350">family or assemby</span></span> | <span data-ttu-id="05c7c-351">全部</span><span class="sxs-lookup"><span data-stu-id="05c7c-351">All</span></span> | <span data-ttu-id="05c7c-352">只能從限定家族或組件之一存取的型別中存取。</span><span class="sxs-lookup"><span data-stu-id="05c7c-352">Accessible only from types that qualify for either family or assembly access.</span></span>
<span data-ttu-id="05c7c-353">public</span><span class="sxs-lookup"><span data-stu-id="05c7c-353">public</span></span> | <span data-ttu-id="05c7c-354">全部</span><span class="sxs-lookup"><span data-stu-id="05c7c-354">All</span></span> | <span data-ttu-id="05c7c-355">可從任何型別中存取。</span><span class="sxs-lookup"><span data-stu-id="05c7c-355">Accessible from any type.</span></span>
<span data-ttu-id="05c7c-356">final</span><span class="sxs-lookup"><span data-stu-id="05c7c-356">final</span></span> | <span data-ttu-id="05c7c-357">方法、屬性和事件</span><span class="sxs-lookup"><span data-stu-id="05c7c-357">Methods, properties, and events</span></span> | <span data-ttu-id="05c7c-358">在衍生型別中無法覆寫虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-358">The virtual method cannot be overridden in a derived type.</span></span>
<span data-ttu-id="05c7c-359">initialize-only</span><span class="sxs-lookup"><span data-stu-id="05c7c-359">initialize-only</span></span> | <span data-ttu-id="05c7c-360">欄位</span><span class="sxs-lookup"><span data-stu-id="05c7c-360">Fields</span></span> | <span data-ttu-id="05c7c-361">只能初始化數值，在初始化之後即無法寫入。</span><span class="sxs-lookup"><span data-stu-id="05c7c-361">The value can only be initialized, and cannot be written after initialization.</span></span>
<span data-ttu-id="05c7c-362">執行個體</span><span class="sxs-lookup"><span data-stu-id="05c7c-362">instance</span></span> | <span data-ttu-id="05c7c-363">欄位、方法、屬性和事件</span><span class="sxs-lookup"><span data-stu-id="05c7c-363">Fields, methods, properties, and events</span></span> | <span data-ttu-id="05c7c-364">如果成員未標記為 `static` (C#)、`Shared` (Visual Basic)、`virtual` (C#) 或 `Overridable` (Visual Basic)，則為執行個體成員 (沒有 instance 關鍵字)。</span><span class="sxs-lookup"><span data-stu-id="05c7c-364">If a member is not marked as `static` (C#), `Shared` (Visual Basic), `virtual` (C#), or `Overridable` (Visual Basic),  it is an instance member (there is no instance keyword).</span></span> <span data-ttu-id="05c7c-365">在記憶體中，這類成員的複本數與使用它的物件數一樣。</span><span class="sxs-lookup"><span data-stu-id="05c7c-365">There will be as many copies of such members in memory as there are objects that use it.</span></span>
<span data-ttu-id="05c7c-366">常值</span><span class="sxs-lookup"><span data-stu-id="05c7c-366">literal</span></span> | <span data-ttu-id="05c7c-367">欄位</span><span class="sxs-lookup"><span data-stu-id="05c7c-367">Fields</span></span> | <span data-ttu-id="05c7c-368">指定給欄位的數值是在編譯時間得知的內建實值型別的固定值。</span><span class="sxs-lookup"><span data-stu-id="05c7c-368">The value assigned to the field is a fixed value, known at compile time, of a built-in value type.</span></span> <span data-ttu-id="05c7c-369">常值 (Literal) 欄位有時候也稱為常數。</span><span class="sxs-lookup"><span data-stu-id="05c7c-369">Literal fields are sometimes referred to as constants.</span></span>
<span data-ttu-id="05c7c-370">newslot 或 override</span><span class="sxs-lookup"><span data-stu-id="05c7c-370">newslot or override</span></span> | <span data-ttu-id="05c7c-371">全部</span><span class="sxs-lookup"><span data-stu-id="05c7c-371">All</span></span> | <span data-ttu-id="05c7c-372">定義成員與具有相同簽章的繼承成員之間的互動方式：`newslot` 可隱藏具有相同簽章的繼承成員；`override` 可取代繼承虛擬方法的定義。</span><span class="sxs-lookup"><span data-stu-id="05c7c-372">Defines how the member interacts with inherited members that have the same signature: `newslot` hides inherited members that have the same signature; `override` replaces the definition of an inherited virtual method.</span></span> <span data-ttu-id="05c7c-373">預設值為 newslot。</span><span class="sxs-lookup"><span data-stu-id="05c7c-373">The default is newslot.</span></span>
<span data-ttu-id="05c7c-374">靜態</span><span class="sxs-lookup"><span data-stu-id="05c7c-374">static</span></span> | <span data-ttu-id="05c7c-375">欄位、方法、屬性和事件</span><span class="sxs-lookup"><span data-stu-id="05c7c-375">Fields, methods, properties, and events</span></span> | <span data-ttu-id="05c7c-376">成員屬於定義於其上的型別，而非屬於特定的型別執行個體；即使沒有建立型別執行個體，成員仍然存在，而且供型別的所有執行個體共用。</span><span class="sxs-lookup"><span data-stu-id="05c7c-376">The member belongs to the type it is defined on, not to a particular instance of the type; the member exists even if an instance of the type is not created, and it is shared among all instances of the type.</span></span>
<span data-ttu-id="05c7c-377">虛擬</span><span class="sxs-lookup"><span data-stu-id="05c7c-377">virtual</span></span> | <span data-ttu-id="05c7c-378">方法、屬性和事件</span><span class="sxs-lookup"><span data-stu-id="05c7c-378">Methods, properties, and events</span></span> | <span data-ttu-id="05c7c-379">方法可由衍生型別實作，而且可以用靜態或動態方式叫用。</span><span class="sxs-lookup"><span data-stu-id="05c7c-379">The method can be implemented by a derived type and can be invoked either statically or dynamically.</span></span> <span data-ttu-id="05c7c-380">如果使用動態引動，在執行時期進行呼叫的執行個體型別會決定呼叫哪一個方法實作，而不是由編譯時間得知的型別決定。</span><span class="sxs-lookup"><span data-stu-id="05c7c-380">If dynamic invocation is used, the type of the instance that makes the call at run time (rather than the type known at compile time) determines which implementation of the method is called.</span></span> <span data-ttu-id="05c7c-381">若要用靜態方式叫用虛擬方法，可能必須將變數轉型為使用方法所需版本的型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-381">To invoke a virtual method statically, the variable might have to be cast to a type that uses the desired version of the method.</span></span>

### <a name="overloading"></a><span data-ttu-id="05c7c-382">多載化</span><span class="sxs-lookup"><span data-stu-id="05c7c-382">Overloading</span></span>

<span data-ttu-id="05c7c-383">每一個型別成員都具有唯一 (Unique) 的簽章。</span><span class="sxs-lookup"><span data-stu-id="05c7c-383">Each type member has a unique signature.</span></span> <span data-ttu-id="05c7c-384">方法簽章包含方法名稱和參數清單 (方法引數的順序和型別)。</span><span class="sxs-lookup"><span data-stu-id="05c7c-384">Method signatures consist of the method name and a parameter list (the order and types of the method's arguments).</span></span> <span data-ttu-id="05c7c-385">只要簽章不相同，就可以在型別中定義具有相同名稱的多個方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-385">Multiple methods with the same name can be defined within a type as long as their signatures differ.</span></span> <span data-ttu-id="05c7c-386">定義兩個或多個具有相同名稱的方法時，就說這個方法是多載。</span><span class="sxs-lookup"><span data-stu-id="05c7c-386">When two or more methods with the same name are defined, the method is said to be overloaded.</span></span> <span data-ttu-id="05c7c-387">例如在 [System.Char](xref:System.Char) 中，會多載 `IsDigit` 方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-387">For example, in [System.Char](xref:System.Char), the `IsDigit` method is overloaded.</span></span> <span data-ttu-id="05c7c-388">其中一個方法採用 [Char](xref:System.Char)，</span><span class="sxs-lookup"><span data-stu-id="05c7c-388">One method takes a [Char](xref:System.Char).</span></span> <span data-ttu-id="05c7c-389">另一個方法則採用 [String](xref:System.String) 與 [Int32](xref:System.Int32)。</span><span class="sxs-lookup"><span data-stu-id="05c7c-389">The other method takes a [String](xref:System.String) and an [Int32](xref:System.Int32).</span></span> 

> [!NOTE]
> <span data-ttu-id="05c7c-390">傳回型別並不會視為方法簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="05c7c-390">The return type is not considered part of a method's signature.</span></span> <span data-ttu-id="05c7c-391">換言之，如果這些方法的差異只在於傳回型別，就不能多載這些方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-391">That is, methods cannot be overloaded if they differ only by return type.</span></span>

### <a name="inheriting-overriding-and-hiding-members"></a><span data-ttu-id="05c7c-392">繼承、覆寫及隱藏成員</span><span class="sxs-lookup"><span data-stu-id="05c7c-392">Inheriting, overriding, and hiding members</span></span>

<span data-ttu-id="05c7c-393">衍生型別會繼承其基底型別的所有成員；也就是說，在衍生型別上會定義這些成員，並供衍生型別使用。</span><span class="sxs-lookup"><span data-stu-id="05c7c-393">A derived type inherits all members of its base type; that is, these members are defined on, and available to, the derived type.</span></span> <span data-ttu-id="05c7c-394">繼承成員的行為或品質可用下列兩種方式來修改：</span><span class="sxs-lookup"><span data-stu-id="05c7c-394">The behavior or qualities of inherited members can be modified in two ways:</span></span> 

* <span data-ttu-id="05c7c-395">衍生型別可用相同的簽章定義新的成員，如此便可隱藏繼承的成員。</span><span class="sxs-lookup"><span data-stu-id="05c7c-395">A derived type can hide an inherited member by defining a new member with the same signature.</span></span> <span data-ttu-id="05c7c-396">您可以將原先為 public 的成員設為 private 成員，或是為標記為 `final` 的繼承方法定義新的行為。</span><span class="sxs-lookup"><span data-stu-id="05c7c-396">This might be done to make a previously public member private or to define new behavior for an inherited method that is marked as `final`.</span></span>

* <span data-ttu-id="05c7c-397">衍生型別可覆寫繼承的虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-397">A derived type can override an inherited virtual method.</span></span> <span data-ttu-id="05c7c-398">覆寫方法會提供新的方法定義，叫用方法時將根據執行時期的實值型別，而非根據編譯時間得知的變數型別。</span><span class="sxs-lookup"><span data-stu-id="05c7c-398">The overriding method provides a new definition of the method that will be invoked based on the type of the value at run time rather than the type of the variable known at compile time.</span></span> <span data-ttu-id="05c7c-399">只有當虛擬方法未標記為 `final`，而且新的方法至少可像虛擬方法一樣存取時，方法才可覆寫虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="05c7c-399">A method can override a virtual method only if the virtual method is not marked as `final` and the new method is at least as accessible as the virtual method.</span></span>

## <a name="see-also"></a><span data-ttu-id="05c7c-400">請參閱</span><span class="sxs-lookup"><span data-stu-id="05c7c-400">See also</span></span>

[<span data-ttu-id="05c7c-401">.NET Framework 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="05c7c-401">Type conversion in the .NET Framework</span></span>](type-conversion.md)
