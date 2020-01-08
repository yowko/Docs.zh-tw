---
title: 結構 - C# 手冊
description: 了解結構類型和其建立方式
ms.date: 10/12/2016
ms.technology: csharp-fundamentals
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: cdfe2a763058b8f568ede2ff93c918c2dae874f7
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346894"
---
# <a name="structs"></a><span data-ttu-id="a6de5-103">結構</span><span class="sxs-lookup"><span data-stu-id="a6de5-103">Structs</span></span>

<span data-ttu-id="a6de5-104">*struct* 是實值型別。</span><span class="sxs-lookup"><span data-stu-id="a6de5-104">A *struct* is a value type.</span></span> <span data-ttu-id="a6de5-105">當建立結構時，結構指派至的變數會保留結構的實際資料。</span><span class="sxs-lookup"><span data-stu-id="a6de5-105">When a struct is created, the variable to which the struct is assigned holds the struct's actual data.</span></span> <span data-ttu-id="a6de5-106">將結構指派至新的變數時，將會複製結構。</span><span class="sxs-lookup"><span data-stu-id="a6de5-106">When the struct is assigned to a new variable, it is copied.</span></span> <span data-ttu-id="a6de5-107">因此，新的變數和原始變數會各自包含一份相同的資料。</span><span class="sxs-lookup"><span data-stu-id="a6de5-107">The new variable and the original variable therefore contain two separate copies of the same data.</span></span> <span data-ttu-id="a6de5-108">針對其中一個複本所做的變更，並不會影響到另一個複本。</span><span class="sxs-lookup"><span data-stu-id="a6de5-108">Changes made to one copy do not affect the other copy.</span></span>

<span data-ttu-id="a6de5-109">實值型別變數會直接包含其值，這表示配置的記憶體內嵌在宣告該變數的內容中。</span><span class="sxs-lookup"><span data-stu-id="a6de5-109">Value type variables directly contain their values, which means that the memory is allocated inline in whatever context the variable is declared.</span></span> <span data-ttu-id="a6de5-110">實值型別變數不會有任何個別的堆積配置或記憶體回收額外負荷。</span><span class="sxs-lookup"><span data-stu-id="a6de5-110">There is no separate heap allocation or garbage collection overhead for value-type variables.</span></span>

<span data-ttu-id="a6de5-111">實值型別有兩種類別︰[struct](language-reference/keywords/struct.md) 和 [enum](language-reference/builtin-types/enum.md)。</span><span class="sxs-lookup"><span data-stu-id="a6de5-111">There are two categories of value types: [struct](language-reference/keywords/struct.md) and [enum](language-reference/builtin-types/enum.md).</span></span>

<span data-ttu-id="a6de5-112">內建的數字型別為結構，而您可以存取其屬性和方法︰</span><span class="sxs-lookup"><span data-stu-id="a6de5-112">The built-in numeric types are structs, and they have properties and methods that you can access:</span></span>

[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]

<span data-ttu-id="a6de5-113">但您會將它們當做簡單的非彙總型別來宣告並將值指派給它們︰</span><span class="sxs-lookup"><span data-stu-id="a6de5-113">But you declare and assign values to them as if they were simple non-aggregate types:</span></span>

[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)]

<span data-ttu-id="a6de5-114">實值型別為 *sealed*，其表示您無法從 <xref:System.Int32> 衍生類型，也無法定義從任何使用者定義的類別或結構繼承的結構，因為結構只能從 <xref:System.ValueType> 繼承。</span><span class="sxs-lookup"><span data-stu-id="a6de5-114">Value types are *sealed*, which means, for example, that you cannot derive a type from <xref:System.Int32>, and you cannot define a struct to inherit from any user-defined class or struct because a struct can only inherit from <xref:System.ValueType>.</span></span> <span data-ttu-id="a6de5-115">不過，結構可以實作一個或多個介面。</span><span class="sxs-lookup"><span data-stu-id="a6de5-115">However, a struct can implement one or more interfaces.</span></span> <span data-ttu-id="a6de5-116">您可以將 struct 型別轉換為 interface 型別；原因是包裝結構的 *boxing* 作業在 Managed 堆積上的參考型別物件內。</span><span class="sxs-lookup"><span data-stu-id="a6de5-116">You can cast a struct type to an interface type; this causes a *boxing* operation to wrap the struct inside a reference type object on the managed heap.</span></span> <span data-ttu-id="a6de5-117">當您將實值型別傳遞至會將 <xref:System.Object> 作為輸入參數的方法時，就會進行 Boxing 作業。</span><span class="sxs-lookup"><span data-stu-id="a6de5-117">Boxing operations occur when you pass a value type to a method that takes an <xref:System.Object> as an input parameter.</span></span> <span data-ttu-id="a6de5-118">如需詳細資訊，請參閱 [Boxing 和 Unboxing](./programming-guide/types/boxing-and-unboxing.md )。</span><span class="sxs-lookup"><span data-stu-id="a6de5-118">For more information, see [Boxing and Unboxing](./programming-guide/types/boxing-and-unboxing.md ).</span></span>

<span data-ttu-id="a6de5-119">您使用 [struct](./language-reference/keywords/struct.md) 關鍵字來建立您自己自訂的實值型別。</span><span class="sxs-lookup"><span data-stu-id="a6de5-119">You use the [struct](./language-reference/keywords/struct.md) keyword to create your own custom value types.</span></span> <span data-ttu-id="a6de5-120">一般來說，會使用結構做為一小組相關變數的容器，如下列範例所示︰</span><span class="sxs-lookup"><span data-stu-id="a6de5-120">Typically, a struct is used as a container for a small set of related variables, as shown in the following example:</span></span>

[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]

<span data-ttu-id="a6de5-121">如需 .NET Framework 中實值型別的詳細資訊，請參閱[一般型別系統](../standard/common-type-system.md)。</span><span class="sxs-lookup"><span data-stu-id="a6de5-121">For more information about value types in the .NET Framework, see [Common Type System](../standard/common-type-system.md).</span></span>

<span data-ttu-id="a6de5-122">結構與類別共用大部分相同的語法，不過結構的限制高於類別︰</span><span class="sxs-lookup"><span data-stu-id="a6de5-122">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>

- <span data-ttu-id="a6de5-123">在結構宣告內，除非欄位宣告為 `const` 或 `static`，否則無法初始化欄位。</span><span class="sxs-lookup"><span data-stu-id="a6de5-123">Within a struct declaration, fields cannot be initialized unless they are declared as `const` or `static`.</span></span>

- <span data-ttu-id="a6de5-124">結構無法宣告無參數建構函式 (不含參數的建構函式) 或完成項。</span><span class="sxs-lookup"><span data-stu-id="a6de5-124">A struct cannot declare a parameterless constructor (a constructor without parameters) or a finalizer.</span></span>

- <span data-ttu-id="a6de5-125">指派時會複製結構。</span><span class="sxs-lookup"><span data-stu-id="a6de5-125">Structs are copied on assignment.</span></span> <span data-ttu-id="a6de5-126">將結構指派給新的變數時，會複製所有資料，而且對新複本進行的任何修改都不會變更原始複本的資料。</span><span class="sxs-lookup"><span data-stu-id="a6de5-126">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="a6de5-127">使用實值型別集合 (例如 Dictionary<string, myStruct>) 時，請一定要記住這一點。</span><span class="sxs-lookup"><span data-stu-id="a6de5-127">This is important to remember when working with collections of value types such as Dictionary<string, myStruct>.</span></span>

- <span data-ttu-id="a6de5-128">結構是實值型別，而類別是參考型別。</span><span class="sxs-lookup"><span data-stu-id="a6de5-128">Structs are value types and classes are reference types.</span></span>

- <span data-ttu-id="a6de5-129">不同於類別，結構不需要使用 `new` 運算子就能具現化。</span><span class="sxs-lookup"><span data-stu-id="a6de5-129">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a6de5-130">在 .NET Core 2.1 和更新版本中，必須使用[新的運算子](language-reference/operators/new-operator.md)或[預設常值](language-reference/operators/default.md#default-literal)，或初始化其每一個私用欄位來具現化結構類型。</span><span class="sxs-lookup"><span data-stu-id="a6de5-130">In .NET Core 2.1 and later, a struct type must be instantiated by using the [new operator](language-reference/operators/new-operator.md) or [default literal](language-reference/operators/default.md#default-literal), or by initializing each of its private fields.</span></span> <span data-ttu-id="a6de5-131">如需詳細資訊，請參閱[從2.0 版遷移至2.1 的重大變更](../core/compatibility/2.0-2.1.md#corefx)。</span><span class="sxs-lookup"><span data-stu-id="a6de5-131">For more information, see [Breaking changes for migration from version 2.0 to 2.1](../core/compatibility/2.0-2.1.md#corefx).</span></span>

- <span data-ttu-id="a6de5-132">結構可以宣告具有參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="a6de5-132">Structs can declare constructors that have parameters.</span></span>

- <span data-ttu-id="a6de5-133">結構無法繼承自另一個結構或類別，而且不能作為類別的基底。</span><span class="sxs-lookup"><span data-stu-id="a6de5-133">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="a6de5-134">所有結構都直接繼承自 <xref:System.ValueType>，該項則繼承自 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="a6de5-134">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>

- <span data-ttu-id="a6de5-135">結構（例如類別）可以執行介面。</span><span class="sxs-lookup"><span data-stu-id="a6de5-135">A struct, like a class, can implement interfaces.</span></span>

## <a name="nullable-value-types"></a><span data-ttu-id="a6de5-136">可為 Null 的實值類型</span><span class="sxs-lookup"><span data-stu-id="a6de5-136">Nullable value types</span></span>

<span data-ttu-id="a6de5-137">一般的實值型別值不能為 [null](language-reference/keywords/null.md)。</span><span class="sxs-lookup"><span data-stu-id="a6de5-137">Ordinary value types cannot have a value of [null](language-reference/keywords/null.md).</span></span> <span data-ttu-id="a6de5-138">不過，您可以在該型別後面添加 `?`，建立可為 null 的實值型別。</span><span class="sxs-lookup"><span data-stu-id="a6de5-138">However, you can create nullable value types by affixing a `?` after the type.</span></span> <span data-ttu-id="a6de5-139">例如，`int?` 就是也能有 [null](./language-reference/keywords/null.md) 值的 `int` 型別。</span><span class="sxs-lookup"><span data-stu-id="a6de5-139">For example, `int?` is an `int` type that can also have the value [null](./language-reference/keywords/null.md).</span></span> <span data-ttu-id="a6de5-140">可為 null 的實數值型別是 <xref:System.Nullable%601>泛型結構類型的實例。</span><span class="sxs-lookup"><span data-stu-id="a6de5-140">Nullable value types are instances of the generic struct type <xref:System.Nullable%601>.</span></span> <span data-ttu-id="a6de5-141">可為 null 的實值型別在您將資料傳遞至資料庫，且其中的數值可能為 null 或未定義時，特別有用。</span><span class="sxs-lookup"><span data-stu-id="a6de5-141">Nullable value types are especially useful when you are passing data to and from databases in which numeric values might be null or undefined.</span></span> <span data-ttu-id="a6de5-142">如需詳細資訊，請參閱[可為 null 的實數值型別](language-reference/builtin-types/nullable-value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a6de5-142">For more information, see [Nullable value types](language-reference/builtin-types/nullable-value-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a6de5-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="a6de5-143">See also</span></span>

- [<span data-ttu-id="a6de5-144">類別</span><span class="sxs-lookup"><span data-stu-id="a6de5-144">Classes</span></span>](programming-guide/classes-and-structs/classes.md)
- [<span data-ttu-id="a6de5-145">基本類型</span><span class="sxs-lookup"><span data-stu-id="a6de5-145">Basic Types</span></span>](basic-types.md)
