---
title: 解構元組和其他類型
description: 了解如何解構 Tuple 和其他類型。
author: rpetrusha
ms.author: ronpet
ms.date: 07/18/2016
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: 48724c65de4fe71294eb5c61c1891d9d56c9b5a4
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "45746818"
---
# <a name="deconstructing-tuples-and-other-types"></a><span data-ttu-id="fa123-103">解構元組和其他類型</span><span class="sxs-lookup"><span data-stu-id="fa123-103">Deconstructing tuples and other types</span></span>

<span data-ttu-id="fa123-104">元組可讓您輕鬆地從方法呼叫擷取多個值。</span><span class="sxs-lookup"><span data-stu-id="fa123-104">A tuple provides a light-weight way to retrieve multiple values from a method call.</span></span> <span data-ttu-id="fa123-105">但擷取元組之後，您必須處理其個別項目。</span><span class="sxs-lookup"><span data-stu-id="fa123-105">But once you retrieve the tuple, you have to handle its individual elements.</span></span> <span data-ttu-id="fa123-106">逐項目執行這項作業很麻煩，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="fa123-106">Doing this on an element-by-element basis is cumbersome, as the following example shows.</span></span> <span data-ttu-id="fa123-107">`QueryCityData` 方法會傳回 3 元組，並以不同作業將其每個項目指派給個別變數。</span><span class="sxs-lookup"><span data-stu-id="fa123-107">The `QueryCityData` method returns a 3-tuple, and each of its elements is assigned to a variable in a separate operation.</span></span>

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

<span data-ttu-id="fa123-108">從一個物件擷取多個欄位和屬性值可能一樣麻煩：您必須逐成員將欄位或屬性值指派給個別變數。</span><span class="sxs-lookup"><span data-stu-id="fa123-108">Retrieving multiple field and property values from an object can be equally cumbersome: you have to assign a field or property value to a variable on a member-by-member basis.</span></span>

<span data-ttu-id="fa123-109">從 C# 7.0 開始，您可以透過單一 *deconstruct* 作業，從一個 Tuple 擷取多個項目，或從一個物件擷取多個欄位、屬性和計算值。</span><span class="sxs-lookup"><span data-stu-id="fa123-109">Starting with C# 7.0, you can retrieve multiple elements from a tuple or retrieve multiple field, property, and computed values from an object in a single *deconstruct* operation.</span></span> <span data-ttu-id="fa123-110">當您解構元組時，您會將其項目指派給個別變數。</span><span class="sxs-lookup"><span data-stu-id="fa123-110">When you deconstruct a tuple, you assign its elements to individual variables.</span></span> <span data-ttu-id="fa123-111">當您解構物件時，您會將選取的值指派給個別變數。</span><span class="sxs-lookup"><span data-stu-id="fa123-111">When you deconstruct an object, you assign selected values to individual variables.</span></span>

## <a name="deconstructing-a-tuple"></a><span data-ttu-id="fa123-112">解構元組</span><span class="sxs-lookup"><span data-stu-id="fa123-112">Deconstructing a tuple</span></span>

<span data-ttu-id="fa123-113">C# 提供解構元組的內建支援，讓您以單一作業將元組中的所有項目解除封裝。</span><span class="sxs-lookup"><span data-stu-id="fa123-113">C# features built-in support for deconstructing tuples, which lets you unpackage all the items in a tuple in a single operation.</span></span> <span data-ttu-id="fa123-114">解構元組的一般語法類似定義元組的語法：您會在指派陳述式的左側，以括弧括住要指派每個項目的變數。</span><span class="sxs-lookup"><span data-stu-id="fa123-114">The general syntax for deconstructing a tuple is similar to the syntax for defining one: you enclose the variables to which each element is to be assigned in parentheses in the left side of an assignment statement.</span></span> <span data-ttu-id="fa123-115">例如，下列陳述式會將 4 元組的項目指派給四個不同的變數：</span><span class="sxs-lookup"><span data-stu-id="fa123-115">For example, the following statement assigns the elements of a 4-tuple to four separate variables:</span></span>

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

<span data-ttu-id="fa123-116">解構 Tuple 的方式有三種：</span><span class="sxs-lookup"><span data-stu-id="fa123-116">There are three ways to deconstruct a tuple:</span></span>

- <span data-ttu-id="fa123-117">您可以明確地宣告括弧內每個欄位的類型。</span><span class="sxs-lookup"><span data-stu-id="fa123-117">You can explicitly declare the type of each field inside parentheses.</span></span> <span data-ttu-id="fa123-118">下列範例會使用此方法來解構 `QueryCityData` 方法傳回的 3 元組。</span><span class="sxs-lookup"><span data-stu-id="fa123-118">The following example uses this approach to deconstruct the 3-tuple returned by the `QueryCityData` method.</span></span>

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- <span data-ttu-id="fa123-119">您可以使用 `var` 關鍵字，讓 C# 推斷每個變數的類型。</span><span class="sxs-lookup"><span data-stu-id="fa123-119">You can use the `var` keyword so that C# infers the type of each variable.</span></span> <span data-ttu-id="fa123-120">請將 `var` 關鍵字放在括弧外。</span><span class="sxs-lookup"><span data-stu-id="fa123-120">You place the `var` keyword outside of the parentheses.</span></span> <span data-ttu-id="fa123-121">下列範例會在解構 `QueryCityData` 方法傳回的 3 元組時，使用型別推斷。</span><span class="sxs-lookup"><span data-stu-id="fa123-121">The following example uses type inference when deconstructing the 3-tuple returned by the `QueryCityData` method.</span></span>

    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    <span data-ttu-id="fa123-122">您也可以個別使用 `var` 關鍵字搭配括弧內的任何或所有變數宣告。</span><span class="sxs-lookup"><span data-stu-id="fa123-122">You can also use the `var` keyword individually with any or all of the variable declarations inside the parentheses.</span></span>

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    <span data-ttu-id="fa123-123">這樣做很麻煩，因此不建議使用。</span><span class="sxs-lookup"><span data-stu-id="fa123-123">This is cumbersome and is not recommended.</span></span>

- <span data-ttu-id="fa123-124">最後，您可能會將 Tuple 解構成已宣告的變數。</span><span class="sxs-lookup"><span data-stu-id="fa123-124">Lastly, you may deconstruct the tuple into variables that have already been declared.</span></span>

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

<span data-ttu-id="fa123-125">請注意，您無法在括弧外指定特定類型，即使元組中的每個欄位都有相同的類型也是一樣。</span><span class="sxs-lookup"><span data-stu-id="fa123-125">Note that you cannot specify a specific type outside the parentheses even if every field in the tuple has the same type.</span></span> <span data-ttu-id="fa123-126">這會產生編譯器錯誤 CS8136：「解構 'var (...)' 表單不允許特定的 'var' 類型」。</span><span class="sxs-lookup"><span data-stu-id="fa123-126">This generates compiler error CS8136, "Deconstruction 'var (...)' form disallows a specific type for 'var'.".</span></span>

<span data-ttu-id="fa123-127">請注意，您也必須將元組的每個項目指派給個別變數。</span><span class="sxs-lookup"><span data-stu-id="fa123-127">Note that you must also assign each element of the tuple to a variable.</span></span> <span data-ttu-id="fa123-128">如果您省略任何項目，編譯器會產生錯誤 CS8132：「無法將 'x' 項目的元組解構為 'y' 變數」。</span><span class="sxs-lookup"><span data-stu-id="fa123-128">If you omit any elements, the compiler generates error CS8132, "Cannot deconstruct a tuple of 'x' elements into 'y' variables."</span></span>

<span data-ttu-id="fa123-129">請注意，您不能在解構左側混用現有變數的宣告和指派。</span><span class="sxs-lookup"><span data-stu-id="fa123-129">Note that you cannot mix declarations and assignments to existing variables on the left-hand side of a deconstruction.</span></span> <span data-ttu-id="fa123-130">編譯器會產生錯誤 CS8184：「解構不得混合左側的宣告與運算式。」</span><span class="sxs-lookup"><span data-stu-id="fa123-130">The compiler generates error CS8184, "a deconstruction cannot mix declarations and expressions on the left-hand-side."</span></span> <span data-ttu-id="fa123-131">此情形發生在成員包含新宣告和現有的變數時。</span><span class="sxs-lookup"><span data-stu-id="fa123-131">when the members include newly declared and existing variables.</span></span>

## <a name="deconstructing-tuple-elements-with-discards"></a><span data-ttu-id="fa123-132">使用 Discard 解構元組項目</span><span class="sxs-lookup"><span data-stu-id="fa123-132">Deconstructing tuple elements with discards</span></span>

<span data-ttu-id="fa123-133">解構元組時，您通常只對部分項目的值感興趣。</span><span class="sxs-lookup"><span data-stu-id="fa123-133">Often when deconstructing a tuple, you're interested in the values of only some elements.</span></span> <span data-ttu-id="fa123-134">從 C# 7.0 開始，您可以使 C# 的 *discard* 支援，這是您已選擇忽略其值的唯寫變數。</span><span class="sxs-lookup"><span data-stu-id="fa123-134">Starting with C# 7.0, you can take advantage of C#'s support for *discards*, which are write-only variables whose values you've chosen to ignore.</span></span> <span data-ttu-id="fa123-135">Discard 是由指派中的底線字元 ("\_") 指定。</span><span class="sxs-lookup"><span data-stu-id="fa123-135">A discard is designated by an underscore character ("\_") in an assignment.</span></span> <span data-ttu-id="fa123-136">您可以視需要捨棄許多值，每個值都會以單一 discard `_` 表示。</span><span class="sxs-lookup"><span data-stu-id="fa123-136">You can discard as many values as you like; all are represented by the single discard, `_`.</span></span>

<span data-ttu-id="fa123-137">下列範例說明如何搭配使用元組與 discard。</span><span class="sxs-lookup"><span data-stu-id="fa123-137">The following example illustrates the use of tuples with discards.</span></span> <span data-ttu-id="fa123-138">`QueryCityDataForYears` 方法會傳回 6 元組，其中包含城市名稱、其區碼、年份、該年的城市人口、次年的年份、次年的城市人口。</span><span class="sxs-lookup"><span data-stu-id="fa123-138">The `QueryCityDataForYears` method returns a 6-tuple with the name of a city, its area, a year, the city's population for that year, a second year, and the city's population for that second year.</span></span> <span data-ttu-id="fa123-139">此範例會顯示這兩年之間的人口變化。</span><span class="sxs-lookup"><span data-stu-id="fa123-139">The example shows the change in population between those two years.</span></span> <span data-ttu-id="fa123-140">在元組可用的資料中，我們對城市區碼不感興趣，並在設計階段得知城市名稱及兩個日期。</span><span class="sxs-lookup"><span data-stu-id="fa123-140">Of the data available from the tuple, we're unconcerned with the city area, and we know the city name and the two dates at design-time.</span></span> <span data-ttu-id="fa123-141">因此，我們只對元組中所儲存的兩個人口值感興趣，而可以將其餘值視為 discard。</span><span class="sxs-lookup"><span data-stu-id="fa123-141">As a result, we're only interested in the two population values stored in the tuple, and can handle its remaining values as discards.</span></span>  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

### <a name="deconstructing-user-defined-types"></a><span data-ttu-id="fa123-142">解構使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="fa123-142">Deconstructing user-defined types</span></span>

<span data-ttu-id="fa123-143">非元組類型不會提供 discard 的內建支援。</span><span class="sxs-lookup"><span data-stu-id="fa123-143">Non-tuple types do not offer built-in support for discards.</span></span> <span data-ttu-id="fa123-144">不過，身為類別、結構或介面的作者，您可以藉由實作一或多個 `Deconstruct` 方法來解構類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fa123-144">However, as the author of a class, a struct, or an interface, you can allow instances of the type to be deconstructed by implementing one or more `Deconstruct` methods.</span></span> <span data-ttu-id="fa123-145">此方法會傳回 void，而且所要解構的每個值會以方法簽章中的 [out](language-reference/keywords/out-parameter-modifier.md) 參數表示。</span><span class="sxs-lookup"><span data-stu-id="fa123-145">The method returns void, and each value to be deconstructed is indicated by an [out](language-reference/keywords/out-parameter-modifier.md) parameter in the method signature.</span></span> <span data-ttu-id="fa123-146">例如，`Person` 類別的下列 `Deconstruct` 方法會傳回名字、中間名和姓氏：</span><span class="sxs-lookup"><span data-stu-id="fa123-146">For example, the following `Deconstruct` method of a `Person` class returns the first, middle, and last name:</span></span>

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

<span data-ttu-id="fa123-147">您可以接著使用如下所示的指派，來解構名為 `p` 的 `Person` 類別執行個體：</span><span class="sxs-lookup"><span data-stu-id="fa123-147">You can then deconstruct an instance of the `Person` class named `p` with an assignment like the following:</span></span>

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

<span data-ttu-id="fa123-148">下列範例會多載 `Deconstruct` 方法，以傳回 `Person` 物件屬性的各種組合。</span><span class="sxs-lookup"><span data-stu-id="fa123-148">The following example overloads the `Deconstruct` method to return various combinations of properties of a `Person` object.</span></span> <span data-ttu-id="fa123-149">每個多載會傳回：</span><span class="sxs-lookup"><span data-stu-id="fa123-149">Individual overloads return:</span></span>

- <span data-ttu-id="fa123-150">名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="fa123-150">A first and last name.</span></span>
- <span data-ttu-id="fa123-151">名字、姓氏和中間名。</span><span class="sxs-lookup"><span data-stu-id="fa123-151">A first, last, and middle name.</span></span>
- <span data-ttu-id="fa123-152">名字、姓氏、城市名稱和州/省名稱。</span><span class="sxs-lookup"><span data-stu-id="fa123-152">A first name, a last name, a city name, and a state name.</span></span>

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

<span data-ttu-id="fa123-153">因為您可以多載 `Deconstruct` 方法以反映多組經常從物件擷取的資料，所以應該使用獨特且明確的簽章來小心定義 `Deconstruct` 方法。</span><span class="sxs-lookup"><span data-stu-id="fa123-153">Because you can overload the `Deconstruct` method to reflect groups of data that are commonly extracted from an object, you should be careful to define `Deconstruct` methods with signatures that are distinctive and unambiguous.</span></span> <span data-ttu-id="fa123-154">多個 `Deconstruct` 方法如有相同數目但不同順序的 `out` 參數，或有相同數目和類型但不同順序的 `out` 參數，則會造成混淆。</span><span class="sxs-lookup"><span data-stu-id="fa123-154">Multiple `Deconstruct` methods that have the same number of `out` parameters or the same number and type of `out` parameters in a different order can cause confusion.</span></span>

<span data-ttu-id="fa123-155">下列範例中的多載方法 `Deconstruct` 說明造成混淆的其中一個可能來源。</span><span class="sxs-lookup"><span data-stu-id="fa123-155">The overloaded `Deconstruct` method in the following example illustrates one possible source of confusion.</span></span> <span data-ttu-id="fa123-156">第一個多載會依序傳回 `Person` 物件的名字、中間名、姓氏和年齡。</span><span class="sxs-lookup"><span data-stu-id="fa123-156">The first overload returns the first name, middle name, last name, and age of a `Person` object, in that order.</span></span> <span data-ttu-id="fa123-157">第二個多載會傳回名稱資訊和年收入，但名字、中間名和姓氏的順序不同。</span><span class="sxs-lookup"><span data-stu-id="fa123-157">The second overload returns name information only along with annual income, but the first, middle, and last name are in a different order.</span></span> <span data-ttu-id="fa123-158">解構 `Person` 執行個體時很容易混淆引數的順序。</span><span class="sxs-lookup"><span data-stu-id="fa123-158">This makes it easy to confuse the order of arguments when deconstructing a `Person` instance.</span></span>

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a><span data-ttu-id="fa123-159">使用 discard 解構使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="fa123-159">Deconstructing a user-defined type with discards</span></span>

<span data-ttu-id="fa123-160">就像[元組](#deconstructing-tuple-elements-with-discards)一樣，您可以使用 discard 來忽略 `Deconstruct` 方法傳回的選取項目。</span><span class="sxs-lookup"><span data-stu-id="fa123-160">Just as you do with [tuples](#deconstructing-tuple-elements-with-discards), you can use discards to ignore selected items returned by a `Deconstruct` method.</span></span> <span data-ttu-id="fa123-161">每個 discard 是由名為 "\_" 的變數定義，而單一解構作業可包含多個 discard。</span><span class="sxs-lookup"><span data-stu-id="fa123-161">Each discard is defined by a variable named "\_", and a single deconstruction operation can include multiple discards.</span></span>

<span data-ttu-id="fa123-162">下列範例會將 `Person` 物件解構為四個字串 (名字、姓氏、城市和州/省)，但捨棄姓氏和州/省。</span><span class="sxs-lookup"><span data-stu-id="fa123-162">The following example deconstructs a `Person` object into four strings (the first and last names, the city, and the state) but discards the last name and the state.</span></span>

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a><span data-ttu-id="fa123-163">使用擴充方法解構使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="fa123-163">Deconstructing a user-defined type with an extension method</span></span>

<span data-ttu-id="fa123-164">如果您並未撰寫類別、結構或介面，仍然可以解構該類型的物件，方法是實作一或多個 `Deconstruct` [擴充方法](programming-guide/classes-and-structs/extension-methods.md)來傳回您想要的值。</span><span class="sxs-lookup"><span data-stu-id="fa123-164">If you didn't author a class, struct, or interface, you can still deconstruct objects of that type by implementing one or more `Deconstruct` [extension methods](programming-guide/classes-and-structs/extension-methods.md) to return the values in which you're interested.</span></span>

<span data-ttu-id="fa123-165">下列範例為 <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> 類別定義兩個 `Deconstruct` 擴充方法。</span><span class="sxs-lookup"><span data-stu-id="fa123-165">The following example defines two `Deconstruct` extension methods for the <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="fa123-166">第一個方法會傳回一組值，指出屬性的特性 (包括其類型)、這是靜態或執行個體、是否為唯讀，以及是否已建立索引。</span><span class="sxs-lookup"><span data-stu-id="fa123-166">The first returns a set of values that indicate the characteristics of the property, including its type, whether it's static or instance, whether it's read-only, and whether it's indexed.</span></span> <span data-ttu-id="fa123-167">第二個方法指出屬性的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="fa123-167">The second indicates the property's accessibility.</span></span> <span data-ttu-id="fa123-168">因為 get 和 set 存取子的存取範圍可能不同，所以布林值會指出屬性是否有不同的 get 和 set 存取子，並在不同時指出其是否具有相同的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="fa123-168">Because the accessibility of get and set accessors can differ, Boolean values indicate whether the property has separate get and set accessors and, if it does, whether they have the same accessibility.</span></span> <span data-ttu-id="fa123-169">如果只有一個存取子，或是 get 和 set 存取子具有相同的存取範圍，則 `access` 變數會指出屬性的整個存取範圍。</span><span class="sxs-lookup"><span data-stu-id="fa123-169">If there is only one accessor or both the get and the set accessor have the same accessibility, the `access` variable indicates the accessibility of the property as a whole.</span></span> <span data-ttu-id="fa123-170">否則，get 和 set 存取子的存取範圍是以 `getAccess` 和 `setAccess` 變數表示。</span><span class="sxs-lookup"><span data-stu-id="fa123-170">Otherwise, the accessibility of the get and set accessors are indicated by the accessaccessibility is indicated by the `getAccess` and `setAccess` variables.</span></span>

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]

## <a name="see-also"></a><span data-ttu-id="fa123-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa123-171">See also</span></span>

- [<span data-ttu-id="fa123-172">捨棄</span><span class="sxs-lookup"><span data-stu-id="fa123-172">Discards</span></span>](discards.md)
- [<span data-ttu-id="fa123-173">元組</span><span class="sxs-lookup"><span data-stu-id="fa123-173">Tuples</span></span>](tuples.md)  
