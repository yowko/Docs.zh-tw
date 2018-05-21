---
title: 結構 - C# 手冊
description: 了解結構類型和其建立方式
ms.date: 10/12/2016
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 9fe4e0278ecf46f762a93aa489030c0a9e5563b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="structs"></a><span data-ttu-id="1d276-103">結構</span><span class="sxs-lookup"><span data-stu-id="1d276-103">Structs</span></span>
<span data-ttu-id="1d276-104">*struct* 是實值型別。</span><span class="sxs-lookup"><span data-stu-id="1d276-104">A *struct* is a value type.</span></span> <span data-ttu-id="1d276-105">建立結構時，指派結構的變數會保留結構的實際資料。</span><span class="sxs-lookup"><span data-stu-id="1d276-105">When a struct is created, the variable to which the struct is assigned holds the struct's actual data.</span></span> <span data-ttu-id="1d276-106">將結構指派至新的變數時，將會複製結構。</span><span class="sxs-lookup"><span data-stu-id="1d276-106">When the struct is assigned to a new variable, it is copied.</span></span> <span data-ttu-id="1d276-107">因此，新的變數和原始變數會各自包含一份相同的資料。</span><span class="sxs-lookup"><span data-stu-id="1d276-107">The new variable and the original variable therefore contain two separate copies of the same data.</span></span> <span data-ttu-id="1d276-108">針對其中一個複本所做的變更，並不會影響到另一個複本。</span><span class="sxs-lookup"><span data-stu-id="1d276-108">Changes made to one copy do not affect the other copy.</span></span>

<span data-ttu-id="1d276-109">實值型別變數會直接包含其值，這表示配置的記憶體內嵌在宣告該變數的內容中。</span><span class="sxs-lookup"><span data-stu-id="1d276-109">Value type variables directly contain their values, which means that the memory is allocated inline in whatever context the variable is declared.</span></span> <span data-ttu-id="1d276-110">實值型別變數不會有任何個別的堆積配置或記憶體回收額外負荷。</span><span class="sxs-lookup"><span data-stu-id="1d276-110">There is no separate heap allocation or garbage collection overhead for value-type variables.</span></span>  
  
<span data-ttu-id="1d276-111">實值型別有兩種類別︰[struct](./language-reference/keywords/struct.md) 和 [enum](./language-reference/keywords/enum.md)。</span><span class="sxs-lookup"><span data-stu-id="1d276-111">There are two categories of value types: [struct](./language-reference/keywords/struct.md) and [enum](./language-reference/keywords/enum.md).</span></span>  
  
<span data-ttu-id="1d276-112">內建的數字型別為結構，而您可以存取其屬性和方法︰</span><span class="sxs-lookup"><span data-stu-id="1d276-112">The built-in numeric types are structs, and they have properties and methods that you can access:</span></span>  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
<span data-ttu-id="1d276-113">但您會將它們當做簡單的非彙總型別來宣告並將值指派給它們︰</span><span class="sxs-lookup"><span data-stu-id="1d276-113">But you declare and assign values to them as if they were simple non-aggregate types:</span></span>  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
<span data-ttu-id="1d276-114">實值型別為 *sealed*，其表示您無法從 <xref:System.Int32> 衍生類型，也無法定義從任何使用者定義的類別或結構繼承的結構，因為結構只能從 <xref:System.ValueType> 繼承。</span><span class="sxs-lookup"><span data-stu-id="1d276-114">Value types are *sealed*, which means, for example, that you cannot derive a type from <xref:System.Int32>, and you cannot define a struct to inherit from any user-defined class or struct because a struct can only inherit from <xref:System.ValueType>.</span></span> <span data-ttu-id="1d276-115">不過，結構可以實作一或多個介面。</span><span class="sxs-lookup"><span data-stu-id="1d276-115">However, a struct can implement one or more interfaces.</span></span> <span data-ttu-id="1d276-116">您可以將結構類型轉型為介面類型；這會導致 *boxing* 作業將結構包裝在 Managed 堆積上的參考型別物件內。</span><span class="sxs-lookup"><span data-stu-id="1d276-116">You can cast a struct type to an interface type; this causes a *boxing* operation to wrap the struct inside a reference type object on the managed heap.</span></span> <span data-ttu-id="1d276-117">當您將實值型別傳遞至會將 <xref:System.Object> 作為輸入參數的方法時，就會進行 Boxing 作業。</span><span class="sxs-lookup"><span data-stu-id="1d276-117">Boxing operations occur when you pass a value type to a method that takes an <xref:System.Object> as an input parameter.</span></span> <span data-ttu-id="1d276-118">如需詳細資訊，請參閱 [Boxing 和 Unboxing](./programming-guide/types/boxing-and-unboxing.md )。</span><span class="sxs-lookup"><span data-stu-id="1d276-118">For more information, see [Boxing and Unboxing](./programming-guide/types/boxing-and-unboxing.md ).</span></span>  
  
<span data-ttu-id="1d276-119">您使用 [struct](./language-reference/keywords/struct.md) 關鍵字來建立您自己自訂的實值型別。</span><span class="sxs-lookup"><span data-stu-id="1d276-119">You use the [struct](./language-reference/keywords/struct.md) keyword to create your own custom value types.</span></span> <span data-ttu-id="1d276-120">一般來說，會使用結構做為一小組相關變數的容器，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="1d276-120">Typically, a struct is used as a container for a small set of related variables, as shown in the following example:</span></span>  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
<span data-ttu-id="1d276-121">如需 .NET Framework 中實值型別的詳細資訊，請參閱[一般型別系統](../standard/common-type-system.md)。</span><span class="sxs-lookup"><span data-stu-id="1d276-121">For more information about value types in the .NET Framework, see [Common Type System](../standard/common-type-system.md).</span></span>  
    
<span data-ttu-id="1d276-122">結構與類別共用大部分相同的語法，不過結構的限制高於類別︰</span><span class="sxs-lookup"><span data-stu-id="1d276-122">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
-   <span data-ttu-id="1d276-123">在結構宣告內，除非欄位宣告為 `const` 或 `static`，否則無法初始化欄位。</span><span class="sxs-lookup"><span data-stu-id="1d276-123">Within a struct declaration, fields cannot be initialized unless they are declared as `const` or `static`.</span></span>  
  
-   <span data-ttu-id="1d276-124">結構無法宣告預設建構函式 (不含參數的建構函式) 或完成項。</span><span class="sxs-lookup"><span data-stu-id="1d276-124">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
  
-   <span data-ttu-id="1d276-125">指派時會複製結構。</span><span class="sxs-lookup"><span data-stu-id="1d276-125">Structs are copied on assignment.</span></span> <span data-ttu-id="1d276-126">將結構指派給新的變數時，會複製所有資料，而且對新複本進行的任何修改都不會變更原始複本的資料。</span><span class="sxs-lookup"><span data-stu-id="1d276-126">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="1d276-127">使用實值型別集合 (例如 Dictionary<string, myStruct>) 時，請一定要記住這一點。</span><span class="sxs-lookup"><span data-stu-id="1d276-127">This is important to remember when working with collections of value types such as Dictionary<string, myStruct>.</span></span>  
  
-   <span data-ttu-id="1d276-128">結構是實值型別，而類別是參考型別。</span><span class="sxs-lookup"><span data-stu-id="1d276-128">Structs are value types and classes are reference types.</span></span>  
  
-   <span data-ttu-id="1d276-129">不同於類別，結構不需要使用 `new` 運算子就能具現化。</span><span class="sxs-lookup"><span data-stu-id="1d276-129">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
-   <span data-ttu-id="1d276-130">結構可以宣告具有參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="1d276-130">Structs can declare constructors that have parameters.</span></span>  
  
-   <span data-ttu-id="1d276-131">結構無法繼承自另一個結構或類別，而且不能作為類別的基底。</span><span class="sxs-lookup"><span data-stu-id="1d276-131">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="1d276-132">所有結構都直接繼承自 <xref:System.ValueType>，該項則繼承自 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="1d276-132">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
  
-   <span data-ttu-id="1d276-133">結構可以實作介面。</span><span class="sxs-lookup"><span data-stu-id="1d276-133">A struct can implement interfaces.</span></span>

## <a name="literal-values"></a><span data-ttu-id="1d276-134">常值</span><span class="sxs-lookup"><span data-stu-id="1d276-134">Literal values</span></span>  
<span data-ttu-id="1d276-135">在 C# 中，常值會接收來自編譯器的類型。</span><span class="sxs-lookup"><span data-stu-id="1d276-135">In C#, literal values receive a type from the compiler.</span></span> <span data-ttu-id="1d276-136">您可以在數字後面附加一個字母，指定應如何輸入數值常值。</span><span class="sxs-lookup"><span data-stu-id="1d276-136">You can specify how a numeric literal should be typed by appending a letter to the end of the number.</span></span> <span data-ttu-id="1d276-137">例如，若要指定應該將值 4.56 視為浮點數時，請在數字之後附加 "f" 或 "F"︰`4.56f`。</span><span class="sxs-lookup"><span data-stu-id="1d276-137">For example, to specify that the value 4.56 should be treated as a float, append an "f" or "F" after the number: `4.56f`.</span></span> <span data-ttu-id="1d276-138">如果未附加任何字母，則編譯器會推斷 `double` 類型的常值。</span><span class="sxs-lookup"><span data-stu-id="1d276-138">If no letter is appended, the compiler will infer the `double` type for the literal.</span></span> <span data-ttu-id="1d276-139">如需您可以使用字母後置字元指定哪些類型的詳細資訊，請參閱參考頁面中個別類型的[實值型別](./language-reference/keywords/value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="1d276-139">For more information about which types can be specified with letter suffixes, see the reference pages for individual types in [Value Types](./language-reference/keywords/value-types.md).</span></span>  
  
<span data-ttu-id="1d276-140">因為輸入的是常值且所有類型最終都衍生自 <xref:System.Object>，所以您可以如下所示來撰寫和編譯程式碼：</span><span class="sxs-lookup"><span data-stu-id="1d276-140">Because literals are typed, and all types derive ultimately from <xref:System.Object>, you can write and compile code such as the following:</span></span>  
  
[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]

<span data-ttu-id="1d276-141">最後兩個範例示範 C# 7.0 引進的語言功能。</span><span class="sxs-lookup"><span data-stu-id="1d276-141">The last two examples demonstrate language features introduced in C# 7.0.</span></span> <span data-ttu-id="1d276-142">第一個可讓您使用底線字元作為數值常值內的「數字分隔符號」。</span><span class="sxs-lookup"><span data-stu-id="1d276-142">The first allows you to use an underscore character as a *digit separator* inside numeric literals.</span></span> <span data-ttu-id="1d276-143">您可以將它們放在數字之間的任何位置，以提高可讀性。</span><span class="sxs-lookup"><span data-stu-id="1d276-143">You can put them wherever you want between digits to improve readability.</span></span> <span data-ttu-id="1d276-144">它們不會影響值。</span><span class="sxs-lookup"><span data-stu-id="1d276-144">They have no effect on the value.</span></span>

<span data-ttu-id="1d276-145">第二個示範「二進位常值」，可讓您直接指定位元模式，而不是使用十六進位標記法。</span><span class="sxs-lookup"><span data-stu-id="1d276-145">The second demonstrates *binary literals*, which allow you to specify bit patterns directly instead of using hexadecimal notation.</span></span>

## <a name="nullable-types"></a><span data-ttu-id="1d276-146">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="1d276-146">Nullable types</span></span>  
<span data-ttu-id="1d276-147">一般實值型別的值不能為 [null](./language-reference/keywords/null.md)。</span><span class="sxs-lookup"><span data-stu-id="1d276-147">Ordinary value types cannot have a value of [null](./language-reference/keywords/null.md).</span></span> <span data-ttu-id="1d276-148">不過，您可以在該類型後面添加 **?**，建立可為 Null 的實值型別</span><span class="sxs-lookup"><span data-stu-id="1d276-148">However, you can create nullable value types by affixing a **?**</span></span> <span data-ttu-id="1d276-149">。</span><span class="sxs-lookup"><span data-stu-id="1d276-149">after the type.</span></span> <span data-ttu-id="1d276-150">例如，**int?** 是也能具有 [null](./language-reference/keywords/null.md) 值的 **int** 類型。</span><span class="sxs-lookup"><span data-stu-id="1d276-150">For example, **int?** is an **int** type that can also have the value [null](./language-reference/keywords/null.md).</span></span> <span data-ttu-id="1d276-151">在 CTS 中，可為 Null 的型別是泛型結構類型 <xref:System.Nullable%601> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1d276-151">In the CTS, nullable types are instances of the generic struct type <xref:System.Nullable%601>.</span></span> <span data-ttu-id="1d276-152">當您要在資料庫之間來回傳遞的資料數值可能為 Null 時，可為 Null 的型別會特別有用。</span><span class="sxs-lookup"><span data-stu-id="1d276-152">Nullable types are especially useful when you are passing data to and from databases in which numeric values might be null.</span></span> <span data-ttu-id="1d276-153">如需詳細資訊，請參閱[可為 Null 的型別 (C# 程式設計手冊)](./programming-guide/nullable-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1d276-153">For more information, see [Nullable Types (C# Programming Guide)](./programming-guide/nullable-types/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d276-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d276-154">See also</span></span>
[<span data-ttu-id="1d276-155">類別</span><span class="sxs-lookup"><span data-stu-id="1d276-155">Classes</span></span>](classes.md)

[<span data-ttu-id="1d276-156">基本類型</span><span class="sxs-lookup"><span data-stu-id="1d276-156">Basic Types</span></span>](basic-types.md)
