---
title: "結構 | C# 手冊"
description: "了解結構類型和其建立方式"
keywords: .NET, .NET Core, C#
author: BillWagner
ms.author: wiwagn
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.translationtype: Human Translation
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: ff7e67add731324e01b8f2cc323a66e3a8683ec9
ms.contentlocale: zh-tw
ms.lasthandoff: 05/15/2017

---

# <a name="structs"></a><span data-ttu-id="42ddd-104">結構</span><span class="sxs-lookup"><span data-stu-id="42ddd-104">Structs</span></span>
<span data-ttu-id="42ddd-105">*struct* 是實值型別。</span><span class="sxs-lookup"><span data-stu-id="42ddd-105">A *struct* is a value type.</span></span> <span data-ttu-id="42ddd-106">建立結構時，指派結構的變數會保留結構的實際資料。</span><span class="sxs-lookup"><span data-stu-id="42ddd-106">When a struct is created, the variable to which the struct is assigned holds the struct's actual data.</span></span> <span data-ttu-id="42ddd-107">將結構指派至新的變數時，將會複製結構。</span><span class="sxs-lookup"><span data-stu-id="42ddd-107">When the struct is assigned to a new variable, it is copied.</span></span> <span data-ttu-id="42ddd-108">因此，新的變數和原始變數會各自包含一份相同的資料。</span><span class="sxs-lookup"><span data-stu-id="42ddd-108">The new variable and the original variable therefore contain two separate copies of the same data.</span></span> <span data-ttu-id="42ddd-109">針對其中一個複本所做的變更，並不會影響到另一個複本。</span><span class="sxs-lookup"><span data-stu-id="42ddd-109">Changes made to one copy do not affect the other copy.</span></span>

<span data-ttu-id="42ddd-110">實值型別變數會直接包含其值，這表示配置的記憶體內嵌在宣告該變數的內容中。</span><span class="sxs-lookup"><span data-stu-id="42ddd-110">Value type variables directly contain their values, which means that the memory is allocated inline in whatever context the variable is declared.</span></span> <span data-ttu-id="42ddd-111">實值型別變數不會有任何個別的堆積配置或記憶體回收額外負荷。</span><span class="sxs-lookup"><span data-stu-id="42ddd-111">There is no separate heap allocation or garbage collection overhead for value-type variables.</span></span>  
  
<span data-ttu-id="42ddd-112">實值型別有兩種類別︰[struct](./language-reference/keywords/struct.md) 和 [enum](./language-reference/keywords/enum.md)。</span><span class="sxs-lookup"><span data-stu-id="42ddd-112">There are two categories of value types: [struct](./language-reference/keywords/struct.md) and [enum](./language-reference/keywords/enum.md).</span></span>  
  
<span data-ttu-id="42ddd-113">內建的數字類型為結構，而您可以存取其屬性和方法︰</span><span class="sxs-lookup"><span data-stu-id="42ddd-113">The built-in numeric types are structs, and they have properties and methods that you can access:</span></span>  
  
<span data-ttu-id="42ddd-114">[!code-csharp[靜態方法](../../samples/snippets/csharp/concepts/structs/static-method.cs)]</span><span class="sxs-lookup"><span data-stu-id="42ddd-114">[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]</span></span>
  
<span data-ttu-id="42ddd-115">但您會將它們當作簡單的非彙總類型來宣告並將值指派給它們︰</span><span class="sxs-lookup"><span data-stu-id="42ddd-115">But you declare and assign values to them as if they were simple non-aggregate types:</span></span>  
  
<span data-ttu-id="42ddd-116">[!code-csharp[指派值](../../samples/snippets/csharp/concepts/structs/assign-value.cs)]</span><span class="sxs-lookup"><span data-stu-id="42ddd-116">[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)]</span></span> 
  
<span data-ttu-id="42ddd-117">實值型別為 *sealed*，其表示您無法從 @System.Int32 衍生類型，也無法定義從任何使用者定義的類別或結構繼承的結構，因為結構只能從 @System.ValueType 繼承。</span><span class="sxs-lookup"><span data-stu-id="42ddd-117">Value types are *sealed*, which means, for example, that you cannot derive a type from @System.Int32, and you cannot define a struct to inherit from any user-defined class or struct because a struct can only inherit from @System.ValueType.</span></span> <span data-ttu-id="42ddd-118">不過，結構可以實作一或多個介面。</span><span class="sxs-lookup"><span data-stu-id="42ddd-118">However, a struct can implement one or more interfaces.</span></span> <span data-ttu-id="42ddd-119">您可以將結構類型轉型為介面類型；這會導致 *boxing* 作業將結構包裝在 Managed 堆積上的參考型別物件內。</span><span class="sxs-lookup"><span data-stu-id="42ddd-119">You can cast a struct type to an interface type; this causes a *boxing* operation to wrap the struct inside a reference type object on the managed heap.</span></span> <span data-ttu-id="42ddd-120">當您將實值型別傳遞至會將 @System.Object 作為輸入參數的方法時，就會進行 Boxing 作業。</span><span class="sxs-lookup"><span data-stu-id="42ddd-120">Boxing operations occur when you pass a value type to a method that takes an @System.Object as an input parameter.</span></span> <span data-ttu-id="42ddd-121">如需詳細資訊，請參閱 [Boxing 和 Unboxing](./programming-guide/types/boxing-and-unboxing.md )。</span><span class="sxs-lookup"><span data-stu-id="42ddd-121">For more information, see [Boxing and Unboxing](./programming-guide/types/boxing-and-unboxing.md ).</span></span>  
  
<span data-ttu-id="42ddd-122">您使用 [struct](./language-reference/keywords/struct.md) 關鍵字來建立您自己自訂的實值型別。</span><span class="sxs-lookup"><span data-stu-id="42ddd-122">You use the [struct](./language-reference/keywords/struct.md) keyword to create your own custom value types.</span></span> <span data-ttu-id="42ddd-123">一般來說，會使用結構作為一小組相關變數的容器，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="42ddd-123">Typically, a struct is used as a container for a small set of related variables, as shown in the following example:</span></span>  
  
<span data-ttu-id="42ddd-124">[!code-csharp[Struct 關鍵字](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]</span><span class="sxs-lookup"><span data-stu-id="42ddd-124">[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]</span></span>  
  
<span data-ttu-id="42ddd-125">如需 .NET Framework 中實值型別的詳細資訊，請參閱[一般型別系統](../standard/common-type-system.md)。</span><span class="sxs-lookup"><span data-stu-id="42ddd-125">For more information about value types in the .NET Framework, see [Common Type System](../standard/common-type-system.md).</span></span>  
    
<span data-ttu-id="42ddd-126">結構與類別共用大部分相同的語法，不過結構的限制高於類別︰</span><span class="sxs-lookup"><span data-stu-id="42ddd-126">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
-   <span data-ttu-id="42ddd-127">在結構宣告內，除非欄位宣告為 `const` 或 `static`，否則無法初始化欄位。</span><span class="sxs-lookup"><span data-stu-id="42ddd-127">Within a struct declaration, fields cannot be initialized unless they are declared as `const` or `static`.</span></span>  
  
-   <span data-ttu-id="42ddd-128">結構無法宣告預設建構函式 (不含參數的建構函式) 或完成項。</span><span class="sxs-lookup"><span data-stu-id="42ddd-128">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
  
-   <span data-ttu-id="42ddd-129">指派時會複製結構。</span><span class="sxs-lookup"><span data-stu-id="42ddd-129">Structs are copied on assignment.</span></span> <span data-ttu-id="42ddd-130">將結構指派給新的變數時，會複製所有資料，而且對新複本進行的任何修改都不會變更原始複本的資料。</span><span class="sxs-lookup"><span data-stu-id="42ddd-130">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="42ddd-131">使用實值型別集合 (例如 Dictionary<string, myStruct>) 時，請一定要記住這一點。</span><span class="sxs-lookup"><span data-stu-id="42ddd-131">This is important to remember when working with collections of value types such as Dictionary<string, myStruct>.</span></span>  
  
-   <span data-ttu-id="42ddd-132">結構是實值型別，而類別是參考型別。</span><span class="sxs-lookup"><span data-stu-id="42ddd-132">Structs are value types and classes are reference types.</span></span>  
  
-   <span data-ttu-id="42ddd-133">不同於類別，結構不需要使用 `new` 運算子就能具現化。</span><span class="sxs-lookup"><span data-stu-id="42ddd-133">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
-   <span data-ttu-id="42ddd-134">結構可以宣告具有參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="42ddd-134">Structs can declare constructors that have parameters.</span></span>  
  
-   <span data-ttu-id="42ddd-135">結構無法繼承自另一個結構或類別，而且不能作為類別的基底。</span><span class="sxs-lookup"><span data-stu-id="42ddd-135">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="42ddd-136">所有結構都直接繼承自 @System.ValueType，該項則繼承自 @System.Object。</span><span class="sxs-lookup"><span data-stu-id="42ddd-136">All structs inherit directly from @System.ValueType, which inherits from @System.Object.</span></span>  
  
-   <span data-ttu-id="42ddd-137">結構可以實作介面。</span><span class="sxs-lookup"><span data-stu-id="42ddd-137">A struct can implement interfaces.</span></span>

## <a name="literal-values"></a><span data-ttu-id="42ddd-138">常值</span><span class="sxs-lookup"><span data-stu-id="42ddd-138">Literal values</span></span>  
<span data-ttu-id="42ddd-139">在 C# 中，常值會接收來自編譯器的類型。</span><span class="sxs-lookup"><span data-stu-id="42ddd-139">In C#, literal values receive a type from the compiler.</span></span> <span data-ttu-id="42ddd-140">您可以在數字後面附加一個字母，指定應如何輸入數值常值。</span><span class="sxs-lookup"><span data-stu-id="42ddd-140">You can specify how a numeric literal should be typed by appending a letter to the end of the number.</span></span> <span data-ttu-id="42ddd-141">例如，若要指定應該將值 4.56 視為浮點數時，請在數字之後附加 "f" 或 "F"︰`4.56f`。</span><span class="sxs-lookup"><span data-stu-id="42ddd-141">For example, to specify that the value 4.56 should be treated as a float, append an "f" or "F" after the number: `4.56f`.</span></span> <span data-ttu-id="42ddd-142">如果未附加任何字母，則編譯器會推斷 `double` 類型的常值。</span><span class="sxs-lookup"><span data-stu-id="42ddd-142">If no letter is appended, the compiler will infer the `double` type for the literal.</span></span> <span data-ttu-id="42ddd-143">如需您可以使用字母後置字元指定哪些類型的詳細資訊，請參閱參考頁面中個別類型的[實值型別](./language-reference/keywords/value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="42ddd-143">For more information about which types can be specified with letter suffixes, see the reference pages for individual types in [Value Types](./language-reference/keywords/value-types.md).</span></span>  
  
<span data-ttu-id="42ddd-144">因為輸入的是常值且所有類型最終都衍生自 @System.Object，所以您可以如下所示來撰寫和編譯程式碼：</span><span class="sxs-lookup"><span data-stu-id="42ddd-144">Because literals are typed, and all types derive ultimately from @System.Object, you can write and compile code such as the following:</span></span>  
  
<span data-ttu-id="42ddd-145">[!code-csharp[常值](../../samples/snippets/csharp/concepts/structs/literals.cs)]</span><span class="sxs-lookup"><span data-stu-id="42ddd-145">[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]</span></span>

<span data-ttu-id="42ddd-146">最後兩個範例示範 C# 7.0 引進的語言功能。</span><span class="sxs-lookup"><span data-stu-id="42ddd-146">The last two examples demonstrate language features introduced in C# 7.0.</span></span> <span data-ttu-id="42ddd-147">第一個可讓您使用底線字元作為數值常值內的「數字分隔符號」。</span><span class="sxs-lookup"><span data-stu-id="42ddd-147">The first allows you to use an underscore character as a *digit separator* inside numeric literals.</span></span> <span data-ttu-id="42ddd-148">您可以將它們放在數字之間的任何位置，以提高可讀性。</span><span class="sxs-lookup"><span data-stu-id="42ddd-148">You can put them wherever you want between digits to improve readability.</span></span> <span data-ttu-id="42ddd-149">它們不會影響值。</span><span class="sxs-lookup"><span data-stu-id="42ddd-149">They have no effect on the value.</span></span>

<span data-ttu-id="42ddd-150">第二個示範「二進位常值」，可讓您直接指定位元模式，而不是使用十六進位標記法。</span><span class="sxs-lookup"><span data-stu-id="42ddd-150">The second demonstrates *binary literals*, which allow you to specify bit patterns directly instead of using hexadecimal notation.</span></span>

## <a name="nullable-types"></a><span data-ttu-id="42ddd-151">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="42ddd-151">Nullable types</span></span>  
<span data-ttu-id="42ddd-152">一般實值型別的值不能為 [null](./language-reference/keywords/null.md)。</span><span class="sxs-lookup"><span data-stu-id="42ddd-152">Ordinary value types cannot have a value of [null](./language-reference/keywords/null.md).</span></span> <span data-ttu-id="42ddd-153">不過，您可以在該類型後面添加 **?**，建立可為 Null 的實值型別</span><span class="sxs-lookup"><span data-stu-id="42ddd-153">However, you can create nullable value types by affixing a **?**</span></span> <span data-ttu-id="42ddd-154">。</span><span class="sxs-lookup"><span data-stu-id="42ddd-154">after the type.</span></span> <span data-ttu-id="42ddd-155">例如，**int?** 是也能具有 [null](./language-reference/keywords/null.md) 值的 **int** 類型。</span><span class="sxs-lookup"><span data-stu-id="42ddd-155">For example, **int?** is an **int** type that can also have the value [null](./language-reference/keywords/null.md).</span></span> <span data-ttu-id="42ddd-156">在 CTS 中，可為 Null 的型別是泛型結構類型 @System.Nullable%601 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="42ddd-156">In the CTS, nullable types are instances of the generic struct type @System.Nullable%601.</span></span> <span data-ttu-id="42ddd-157">當您要在資料庫之間來回傳遞的資料數值可能為 Null 時，可為 Null 的型別會特別有用。</span><span class="sxs-lookup"><span data-stu-id="42ddd-157">Nullable types are especially useful when you are passing data to and from databases in which numeric values might be null.</span></span> <span data-ttu-id="42ddd-158">如需詳細資訊，請參閱[可為 Null 的型別 (C# 程式設計手冊)](./programming-guide/nullable-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="42ddd-158">For more information, see [Nullable Types (C# Programming Guide)](./programming-guide/nullable-types/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="42ddd-159">請參閱</span><span class="sxs-lookup"><span data-stu-id="42ddd-159">See also</span></span>
[<span data-ttu-id="42ddd-160">類別</span><span class="sxs-lookup"><span data-stu-id="42ddd-160">Classes</span></span>](classes.md)

[<span data-ttu-id="42ddd-161">基本類型</span><span class="sxs-lookup"><span data-stu-id="42ddd-161">Basic Types</span></span>](basic-types.md)
