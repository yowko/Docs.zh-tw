---
title: 在 Visual Basic 中的 Tuple
ms.custom: ''
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68c82e75ce4a438381bc9c60ce8c992565eb31cb
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="tuples-visual-basic"></a><span data-ttu-id="fdbee-102">Tuple (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fdbee-102">Tuples (Visual Basic)</span></span>

<span data-ttu-id="fdbee-103">從 Visual Basic 2017 開始，Visual Basic 語言提供了內建的 tuple，可支援建立 tuple 及存取更容易 tuple 的項目。</span><span class="sxs-lookup"><span data-stu-id="fdbee-103">Starting with Visual Basic 2017, the Visual Basic language offers built-in support for tuples that makes creating tuples and accessing the elements of tuples easier.</span></span> <span data-ttu-id="fdbee-104">Tuple 是輕量的資料結構有特定數目和值的序列。</span><span class="sxs-lookup"><span data-stu-id="fdbee-104">A tuple is a light-weight data structure that has a specific number and sequence of values.</span></span> <span data-ttu-id="fdbee-105">當您具現化 tuple 時，您可以定義數目和每個值 （或元素） 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="fdbee-105">When you instantiate the tuple, you define the number and the data type of each value (or element).</span></span> <span data-ttu-id="fdbee-106">例如，2-tuple （或組） 有兩個項目。</span><span class="sxs-lookup"><span data-stu-id="fdbee-106">For example, a 2-tuple (or pair) has two elements.</span></span> <span data-ttu-id="fdbee-107">第一個可能`Boolean`值，而第二個是`String`。</span><span class="sxs-lookup"><span data-stu-id="fdbee-107">The first might be a `Boolean` value, while the second is a `String`.</span></span> <span data-ttu-id="fdbee-108">Tuple 可以輕鬆將多個值儲存在單一物件，因為通常用做為從方法傳回多個值的輕量方式。</span><span class="sxs-lookup"><span data-stu-id="fdbee-108">Because tuples make it easy to store multiple values in a single object, they are often used as a lightweight way to return multiple values from a method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fdbee-109">Tuple 支援需要<xref:System.ValueTuple>型別。</span><span class="sxs-lookup"><span data-stu-id="fdbee-109">Tuple support requires the <xref:System.ValueTuple> type.</span></span> <span data-ttu-id="fdbee-110">如果未安裝.NET Framework 4.7，您必須先將 NuGet 封裝`System.ValueTuple`，它位在 NuGet Gallery 上。</span><span class="sxs-lookup"><span data-stu-id="fdbee-110">If the .NET Framework 4.7 is not installed, you must add the NuGet package `System.ValueTuple`, which is available on the NuGet Gallery.</span></span> <span data-ttu-id="fdbee-111">沒有這個套件，您可能會收到編譯錯誤類似於 「 預先定義型別 'ValueTuple(Of,,,)' 未定義或匯入 」。</span><span class="sxs-lookup"><span data-stu-id="fdbee-111">Without this package, you may get a compilation error similar to, "Predefined type 'ValueTuple(Of,,,)' is not defined or imported."</span></span>

## <a name="instantiating-and-using-a-tuple"></a><span data-ttu-id="fdbee-112">具現化及使用 tuple</span><span class="sxs-lookup"><span data-stu-id="fdbee-112">Instantiating and using a tuple</span></span>

<span data-ttu-id="fdbee-113">您只要將它以逗號分隔值的 im 括號初始化 tuple。</span><span class="sxs-lookup"><span data-stu-id="fdbee-113">You instantiate a tuple by enclosing its comma-delimited values im parentheses.</span></span> <span data-ttu-id="fdbee-114">每個這些值就會變成 tuple 的欄位。</span><span class="sxs-lookup"><span data-stu-id="fdbee-114">Each of those values then becomes a field of the tuple.</span></span> <span data-ttu-id="fdbee-115">比方說，下列程式碼會定義三重 （或 3 tuple） 與`Date`做為其第一個值，`String`做為第二個，而`Boolean`做為其第三個。</span><span class="sxs-lookup"><span data-stu-id="fdbee-115">For example, the following code defines a triple (or 3-tuple) with a `Date` as its first value, a `String` as its second, and a `Boolean` as its third.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

<span data-ttu-id="fdbee-116">根據預設，tuple 中每個欄位的名稱包含字串的`Item`以及 tuple 中的欄位 1 為基底位置。</span><span class="sxs-lookup"><span data-stu-id="fdbee-116">By default, the name of each field in a tuple consists of the string `Item` along with the field's one-based position in the tuple.</span></span> <span data-ttu-id="fdbee-117">針對此 3-tuple`Date`欄位是`Item1`、`String`欄位是`Item2`，而`Boolean`欄位是`Item3`。</span><span class="sxs-lookup"><span data-stu-id="fdbee-117">For this 3-tuple, the `Date` field is `Item1`, the `String` field is `Item2`, and the `Boolean` field is `Item3`.</span></span> <span data-ttu-id="fdbee-118">下列範例顯示的 tuple 上一行的程式碼中具現化欄位的值</span><span class="sxs-lookup"><span data-stu-id="fdbee-118">The following example displays the values of fields of the tuple instantiated in the previous line of code</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

<span data-ttu-id="fdbee-119">Visual Basic tuple 的欄位會讀取寫入;tuple 已具現化之後，您可以修改它的值。</span><span class="sxs-lookup"><span data-stu-id="fdbee-119">The fields of a Visual Basic tuple are read-write; after you've instantiated a tuple, you can modify its values.</span></span> <span data-ttu-id="fdbee-120">下列範例會修改兩個 tuple 上一個範例中所建立的三個欄位，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="fdbee-120">The following example modifies two of the three fields of the tuple created in the previous example and displays the result.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a><span data-ttu-id="fdbee-121">具現化及使用具名的 tuple</span><span class="sxs-lookup"><span data-stu-id="fdbee-121">Instantiating and using a named tuple</span></span>

<span data-ttu-id="fdbee-122">而不是使用 tuple 欄位的預設名稱，您可以具現化*名為 tuple*藉由 tuple 的項目來指定您自己的名稱。</span><span class="sxs-lookup"><span data-stu-id="fdbee-122">Rather than using default names for a tuple's fields, you can instantiate a *named tuple* by assigning your own names to the tuple's elements.</span></span> <span data-ttu-id="fdbee-123">然後可以指派的名稱來存取的 tuple 欄位*或*藉由其預設名稱。</span><span class="sxs-lookup"><span data-stu-id="fdbee-123">The tuple's fields can then be accessed by their assigned names *or* by their default names.</span></span> <span data-ttu-id="fdbee-124">下列範例在不同之處在於它明確命名的第一個欄位，具現化相同以前，做為 3 個 tuple `EventDate`，第二個`Name`，第三個`IsHoliday`。</span><span class="sxs-lookup"><span data-stu-id="fdbee-124">The following example instantiates the same 3-tuple as previously, except that it explicitly names the first field `EventDate`, the second `Name`, and the third `IsHoliday`.</span></span> <span data-ttu-id="fdbee-125">然後顯示欄位值，修改它們，並再次顯示欄位值。</span><span class="sxs-lookup"><span data-stu-id="fdbee-125">It then displays the field values, modifies them, and displays the field values again.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="fdbee-126">推斷的 tuple 項目名稱</span><span class="sxs-lookup"><span data-stu-id="fdbee-126">Inferred tuple element names</span></span>

<span data-ttu-id="fdbee-127">從 Visual Basic 15.3 開始，Visual Basic 可推斷 tuple 項目; 的名稱您沒有明確指派給它們。</span><span class="sxs-lookup"><span data-stu-id="fdbee-127">Starting with Visual Basic 15.3, Visual Basic can infer the names of tuple elements; you do not have to assign them explicitly.</span></span> <span data-ttu-id="fdbee-128">初始化變數，一組 tuple，而且您想要做為變數的名稱相同的 tuple 項目名稱時，推斷的 tuple 名稱很有用。</span><span class="sxs-lookup"><span data-stu-id="fdbee-128">Inferred tuple names are useful when you initialize a tuple from a set of variables, and you want the tuple element name to be the same as the variable name.</span></span> 

<span data-ttu-id="fdbee-129">下列範例會建立`stateInfo`tuple，其中包含三個明確的具名項目， `state`， `stateName`，和`capital`。</span><span class="sxs-lookup"><span data-stu-id="fdbee-129">The following example creates a `stateInfo` tuple that contains three explicitly named elements, `state`, `stateName`, and `capital`.</span></span> <span data-ttu-id="fdbee-130">請注意，在中命名項目，tuple 的初始化陳述式只會指派具名項目同名的變數的值。</span><span class="sxs-lookup"><span data-stu-id="fdbee-130">Note that, in naming the elements, the tuple initialization statement simply assigns the named elements the values of the identically named variables.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
<span data-ttu-id="fdbee-131">項目和變數具有相同的名稱，因為 Visual Basic 編譯器可以推斷出欄位的名稱，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="fdbee-131">Because elements and variables have the same name, the Visual Basic compiler can infer the names of the fields, as the following example shows.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

<span data-ttu-id="fdbee-132">若要啟用 interred 的 tuple 項目名稱，您必須定義要在 Visual Basic 專案中使用 Visual Basic 編譯器的版本 (\*.vbproj) 檔案：</span><span class="sxs-lookup"><span data-stu-id="fdbee-132">To enable interred tuple element names, you must define the version of the Visual Basic compiler to use in your Visual Basic project (\*.vbproj) file:</span></span> 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 
```

<span data-ttu-id="fdbee-133">版本號碼可以是任何版本的 Visual Basic 編譯器 15.3 開始。</span><span class="sxs-lookup"><span data-stu-id="fdbee-133">The version number can be any version of the Visual Basic compiler starting with 15.3.</span></span> <span data-ttu-id="fdbee-134">而不是硬式編碼特定編譯器版本，您也可以指定 「 最新 」 做為值`LangVersion`使用 Visual Basic 編譯器在系統上安裝最新版本進行編譯。</span><span class="sxs-lookup"><span data-stu-id="fdbee-134">Rather than hard-coding a specific compiler version, you can also specify "Latest" as the value of `LangVersion` to compile with the most recent version of the Visual Basic compiler installed on your system.</span></span>

<span data-ttu-id="fdbee-135">在某些情況下，Visual Basic 編譯器無法推斷從候選項目名稱的 tuple 項目名稱和 tuple 欄位只可參考使用其預設名稱，例如`Item1`，`Item2`等等。它們包括：</span><span class="sxs-lookup"><span data-stu-id="fdbee-135">In some cases, the Visual Basic compiler cannot infer the tuple element name from the candidate name, and the tuple field can only be referenced using its default name, such as `Item1`, `Item2`, etc. These include:</span></span>

- <span data-ttu-id="fdbee-136">候選項目名稱等同於 tuple 成員名稱，例如`Item3`， `Rest`，或`ToString`。</span><span class="sxs-lookup"><span data-stu-id="fdbee-136">The candidate name is the same as the name of a tuple member, such as `Item3`, `Rest`, or `ToString`.</span></span>

- <span data-ttu-id="fdbee-137">Tuple 中重複的候選項目名稱。</span><span class="sxs-lookup"><span data-stu-id="fdbee-137">The candidate name is duplicated in the tuple.</span></span>
 
<span data-ttu-id="fdbee-138">欄位名稱推斷失敗時，Visual Basic 不會產生編譯器錯誤，也不是在執行階段擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fdbee-138">When field name inference fails, Visual Basic does not generate a compiler error, nor is an exception thrown at runtime.</span></span> <span data-ttu-id="fdbee-139">相反地，tuple 欄位必須參考預先定義的名稱，例如`Item1`和`Item2`。</span><span class="sxs-lookup"><span data-stu-id="fdbee-139">Instead, tuple fields must be referenced by their predefined names, such as `Item1` and `Item2`.</span></span> 
  
## <a name="tuples-versus-structures"></a><span data-ttu-id="fdbee-140">Tuple 與結構</span><span class="sxs-lookup"><span data-stu-id="fdbee-140">Tuples versus structures</span></span>

<span data-ttu-id="fdbee-141">Visual Basic tuple 都是實值類型的其中一個執行個體**System.ValueTuple**泛型型別。</span><span class="sxs-lookup"><span data-stu-id="fdbee-141">A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types.</span></span> <span data-ttu-id="fdbee-142">例如，`holiday`前一個範例中所定義的 tuple 都是執行個體<xref:System.ValueTuple%603>結構。</span><span class="sxs-lookup"><span data-stu-id="fdbee-142">For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure.</span></span> <span data-ttu-id="fdbee-143">它被設計為資料的輕量型容器。</span><span class="sxs-lookup"><span data-stu-id="fdbee-143">It is designed to be a lightweight container for data.</span></span> <span data-ttu-id="fdbee-144">Tuple 旨在讓您輕鬆建立具有多個資料項目的物件，因為其欠缺的一些功能可能會有自訂的結構。</span><span class="sxs-lookup"><span data-stu-id="fdbee-144">Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have.</span></span> <span data-ttu-id="fdbee-145">它們包括：</span><span class="sxs-lookup"><span data-stu-id="fdbee-145">These include:</span></span>

- <span data-ttu-id="fdbee-146">自訂成員。</span><span class="sxs-lookup"><span data-stu-id="fdbee-146">Custom members.</span></span> <span data-ttu-id="fdbee-147">您無法定義自己的屬性、 方法或事件的 tuple。</span><span class="sxs-lookup"><span data-stu-id="fdbee-147">You cannot define your own properties, methods, or events for a tuple.</span></span>

- <span data-ttu-id="fdbee-148">驗證。</span><span class="sxs-lookup"><span data-stu-id="fdbee-148">Validation.</span></span> <span data-ttu-id="fdbee-149">您無法驗證指派給欄位的資料。</span><span class="sxs-lookup"><span data-stu-id="fdbee-149">You cannot validate the data assigned to fields.</span></span>

- <span data-ttu-id="fdbee-150">不變性。</span><span class="sxs-lookup"><span data-stu-id="fdbee-150">Immutability.</span></span> <span data-ttu-id="fdbee-151">Visual Basic tuple 是可變動的。</span><span class="sxs-lookup"><span data-stu-id="fdbee-151">Visual Basic tuples are mutable.</span></span> <span data-ttu-id="fdbee-152">相反地，自訂結構可讓您控制執行個體是否處於可變動或不變。</span><span class="sxs-lookup"><span data-stu-id="fdbee-152">In contrast, a custom structure allows you to control whether an instance is mutable or immutable.</span></span>

<span data-ttu-id="fdbee-153">自訂成員、 屬性和欄位驗證或不變性來說很重要，您應該使用 Visual Basic[結構](../../../language-reference/statements/structure-statement.md)陳述式來定義自訂值型別。</span><span class="sxs-lookup"><span data-stu-id="fdbee-153">If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.</span></span>

<span data-ttu-id="fdbee-154">Visual Basic tuple 沒有繼承的成員及其**ValueTuple**型別。</span><span class="sxs-lookup"><span data-stu-id="fdbee-154">A Visual Basic tuple does inherit the members of its **ValueTuple** type.</span></span> <span data-ttu-id="fdbee-155">除了其欄位，這些需求包括下列方法：</span><span class="sxs-lookup"><span data-stu-id="fdbee-155">In addition to its fields, these include the following methods:</span></span>

| <span data-ttu-id="fdbee-156">成員</span><span class="sxs-lookup"><span data-stu-id="fdbee-156">Member</span></span> | <span data-ttu-id="fdbee-157">描述</span><span class="sxs-lookup"><span data-stu-id="fdbee-157">Description</span></span> |
| ---|---|
| <span data-ttu-id="fdbee-158">CompareTo</span><span class="sxs-lookup"><span data-stu-id="fdbee-158">CompareTo</span></span> | <span data-ttu-id="fdbee-159">比較目前的 tuple，至另一個 tuple 有相同數目的項目。</span><span class="sxs-lookup"><span data-stu-id="fdbee-159">Compares the current tuple to another tuple with the same number of elements.</span></span> |
| <span data-ttu-id="fdbee-160">等於</span><span class="sxs-lookup"><span data-stu-id="fdbee-160">Equals</span></span> | <span data-ttu-id="fdbee-161">判斷目前的 tuple 是否等於另一個 tuple 或物件。</span><span class="sxs-lookup"><span data-stu-id="fdbee-161">Determines whether the current tuple is equal to another tuple or object.</span></span> |
| <span data-ttu-id="fdbee-162">GetHashCode</span><span class="sxs-lookup"><span data-stu-id="fdbee-162">GetHashCode</span></span> | <span data-ttu-id="fdbee-163">計算目前的執行個體的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="fdbee-163">Calculates the hash code for the current instance.</span></span> |
| <span data-ttu-id="fdbee-164">ToString</span><span class="sxs-lookup"><span data-stu-id="fdbee-164">ToString</span></span> | <span data-ttu-id="fdbee-165">傳回 tuple，其格式的字串表示`(Item1, Item2...)`，其中`Item1`和`Item2`代表 tuple 的欄位的值。</span><span class="sxs-lookup"><span data-stu-id="fdbee-165">Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields.</span></span> |

<span data-ttu-id="fdbee-166">此外， **ValueTuple**型別會實作<xref:System.Collections.IStructuralComparable>和<xref:System.Collections.IStructuralEquatable>介面，讓您定義客戶比較子。</span><span class="sxs-lookup"><span data-stu-id="fdbee-166">In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define customer comparers.</span></span>

## <a name="assignment-and-tuples"></a><span data-ttu-id="fdbee-167">指派和 Tuple</span><span class="sxs-lookup"><span data-stu-id="fdbee-167">Assignment and tuples</span></span>

<span data-ttu-id="fdbee-168">Visual Basic 支援 tuple 類型有相同數目的欄位之間的指派。</span><span class="sxs-lookup"><span data-stu-id="fdbee-168">Visual Basic supports assignment between tuple types that have the same number of fields.</span></span> <span data-ttu-id="fdbee-169">如果下列其中一項為 true，則可以轉換的欄位型別：</span><span class="sxs-lookup"><span data-stu-id="fdbee-169">The field types can be converted if one of the following is true:</span></span>

- <span data-ttu-id="fdbee-170">來源和目標欄位屬於相同類型。</span><span class="sxs-lookup"><span data-stu-id="fdbee-170">The source and target field are of the same type.</span></span>

- <span data-ttu-id="fdbee-171">擴展 （或隱含） 的來源類型轉換成目標類型被定義。</span><span class="sxs-lookup"><span data-stu-id="fdbee-171">A widening (or implicit) conversion of the source type to the target type is defined.</span></span> 

- <span data-ttu-id="fdbee-172">`Option Strict` 是`On`，和縮小 （或明確） 的來源類型轉換成目標類型定義。</span><span class="sxs-lookup"><span data-stu-id="fdbee-172">`Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined.</span></span> <span data-ttu-id="fdbee-173">如果來源值是目標類型的範圍之外，這項轉換可以擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fdbee-173">This conversion can throw an exception if the source value is outside the range of the target type.</span></span>

<span data-ttu-id="fdbee-174">不會考慮對指派進行其他轉換。</span><span class="sxs-lookup"><span data-stu-id="fdbee-174">Other conversions are not considered for assignments.</span></span> <span data-ttu-id="fdbee-175">讓我們看看 Tuple 類型之間允許的指派類型。</span><span class="sxs-lookup"><span data-stu-id="fdbee-175">Let's look at the kinds of assignments that are allowed between tuple types.</span></span>

<span data-ttu-id="fdbee-176">請考慮在下列範例中使用的這些參數：</span><span class="sxs-lookup"><span data-stu-id="fdbee-176">Consider these variables used in the following examples:</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

<span data-ttu-id="fdbee-177">前兩個變數，`unnamed`和`anonymous`，不會有語意提供欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="fdbee-177">The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields.</span></span> <span data-ttu-id="fdbee-178">欄位名稱都是預設值`Item1`和`Item2`。</span><span class="sxs-lookup"><span data-stu-id="fdbee-178">Their field names are the default `Item1` and `Item2`.</span></span> <span data-ttu-id="fdbee-179">最後兩個變數，`named`和`differentName`語意的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="fdbee-179">The last two variables, `named` and `differentName` have semantic field names.</span></span> <span data-ttu-id="fdbee-180">請注意，這兩個 Tuple 有不同的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="fdbee-180">Note that these two tuples have different names for the fields.</span></span>

<span data-ttu-id="fdbee-181">所有的這些 tuple 的四個有相同數目的欄位 （稱為 'arity'），與這些欄位類型完全相同。</span><span class="sxs-lookup"><span data-stu-id="fdbee-181">All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical.</span></span> <span data-ttu-id="fdbee-182">因此，所有這些指派都會運作︰</span><span class="sxs-lookup"><span data-stu-id="fdbee-182">Therefore, all of these assignments work:</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

<span data-ttu-id="fdbee-183">請注意，不會指派 Tuple 的名稱。</span><span class="sxs-lookup"><span data-stu-id="fdbee-183">Notice that the names of the tuples are not assigned.</span></span> <span data-ttu-id="fdbee-184">依欄位在 Tuple 中的順序，指派欄位的值。</span><span class="sxs-lookup"><span data-stu-id="fdbee-184">The values of the fields are assigned following the order of the fields in the tuple.</span></span>

<span data-ttu-id="fdbee-185">最後，請注意，我們可以將指派`named`tuple `conversion` tuple，即使的第一個欄位`named`是`Integer`，並將第一個欄位的`conversion`是`Long`。</span><span class="sxs-lookup"><span data-stu-id="fdbee-185">Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`.</span></span> <span data-ttu-id="fdbee-186">此指派會成功，因為轉換`Integer`至`Long`擴展轉換。</span><span class="sxs-lookup"><span data-stu-id="fdbee-186">This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

<span data-ttu-id="fdbee-187">Tuple 不同數目的欄位不可以指派：</span><span class="sxs-lookup"><span data-stu-id="fdbee-187">Tuples with different numbers of fields are not assignable:</span></span>

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a><span data-ttu-id="fdbee-188">Tuple 作為方法傳回值</span><span class="sxs-lookup"><span data-stu-id="fdbee-188">Tuples as method return values</span></span>

<span data-ttu-id="fdbee-189">方法可以傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="fdbee-189">A method can return only a single value.</span></span> <span data-ttu-id="fdbee-190">通常，不過，您會希望方法呼叫傳回多個值。</span><span class="sxs-lookup"><span data-stu-id="fdbee-190">Frequently, though, you'd like a method call to return multiple values.</span></span> <span data-ttu-id="fdbee-191">有數種方式來解決這項限制：</span><span class="sxs-lookup"><span data-stu-id="fdbee-191">There are several ways to work around this limitation:</span></span>

- <span data-ttu-id="fdbee-192">您可以建立自訂類別或結構的屬性或欄位代表的方法所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="fdbee-192">You can create a custom class or structure whose properties or fields represent values returned by the method.</span></span> <span data-ttu-id="fdbee-193">因此是重量型的解決方案。它會要求您定義自訂類型，其唯一目的是要從方法呼叫中擷取值。</span><span class="sxs-lookup"><span data-stu-id="fdbee-193">Thus is a heavyweight solution; it requires that you define a custom type whose only purpose is to retrieve values from a method call.</span></span>

- <span data-ttu-id="fdbee-194">您可以從方法傳回單一值，並將其餘的值傳回的參考，這個方法以傳送它們。</span><span class="sxs-lookup"><span data-stu-id="fdbee-194">You can return a single value from the method, and return the remaining values by passing them by reference to the method.</span></span> <span data-ttu-id="fdbee-195">這牽涉到變數和不小心覆寫的傳址方式傳遞的變數值的風險，具現化的額外的負荷。</span><span class="sxs-lookup"><span data-stu-id="fdbee-195">This involves the overhead of instantiating a variable and risks inadvertently overwriting the value of the variable that you pass by reference.</span></span>

- <span data-ttu-id="fdbee-196">您可以使用 tuple，提供要擷取多個傳回值的輕量型方案。</span><span class="sxs-lookup"><span data-stu-id="fdbee-196">You can use a tuple, which provides a lightweight solution to retrieving multiple return values.</span></span>

<span data-ttu-id="fdbee-197">例如， **TryParse**方法在.NET 傳回`Boolean`值，指出是否在剖析作業成功。</span><span class="sxs-lookup"><span data-stu-id="fdbee-197">For example, the **TryParse** methods in .NET return a `Boolean` value that indicates whether the parsing operation succeeded.</span></span> <span data-ttu-id="fdbee-198">在剖析作業的結果會傳回給方法的參考所傳遞的變數中。</span><span class="sxs-lookup"><span data-stu-id="fdbee-198">The result of the parsing operation is returned in a variable passed by reference to the method.</span></span> <span data-ttu-id="fdbee-199">一般來說，呼叫剖析方法時，例如<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>看起來像下面這樣：</span><span class="sxs-lookup"><span data-stu-id="fdbee-199">Normally, a call to the a parsing method such as <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> looks like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

<span data-ttu-id="fdbee-200">我們可以從在剖析作業傳回 tuple，如果我們將呼叫包裝至<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>我們自己的方法中的方法。</span><span class="sxs-lookup"><span data-stu-id="fdbee-200">We can return a tuple from the parsing operation if we wrap the call to the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method in our own method.</span></span> <span data-ttu-id="fdbee-201">在下列範例中，`NumericLibrary.ParseInteger`呼叫<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>方法，並傳回具有兩個元素的具名的 tuple。</span><span class="sxs-lookup"><span data-stu-id="fdbee-201">In the following example, `NumericLibrary.ParseInteger` calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method and returns a named tuple with two elements.</span></span> 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

<span data-ttu-id="fdbee-202">然後，您可以呼叫具有類似下列的程式碼的方法：</span><span class="sxs-lookup"><span data-stu-id="fdbee-202">You can then call the method with code like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a><span data-ttu-id="fdbee-203">Visual Basic 的 tuple 與.NET Framework 中</span><span class="sxs-lookup"><span data-stu-id="fdbee-203">Visual Basic tuples and tuples in the .NET Framework</span></span>

<span data-ttu-id="fdbee-204">Visual Basic tuple 是其中一個的執行個體**System.ValueTuple** .NET Framework 4.7 中導入的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="fdbee-204">A Visual Basic tuple is an instance of one of the **System.ValueTuple** generic types, which were introduced in the .NET Framework 4.7.</span></span> <span data-ttu-id="fdbee-205">.NET Framework 也會包含一組的泛型**System.Tuple**類別。</span><span class="sxs-lookup"><span data-stu-id="fdbee-205">The .NET Framework also includes a set of generic **System.Tuple** classes.</span></span> <span data-ttu-id="fdbee-206">這些類別，不過，與 Visual Basic tuple 不同而**System.ValueTuple**數種方式中的泛型類型：</span><span class="sxs-lookup"><span data-stu-id="fdbee-206">These classes, however, differ from Visual Basic tuples and the **System.ValueTuple** generic types in a number of ways:</span></span>

- <span data-ttu-id="fdbee-207">項目**Tuple**類別是名為屬性`Item1`， `Item2`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="fdbee-207">The elements of the **Tuple** classes are properties named `Item1`, `Item2`, and so on.</span></span> <span data-ttu-id="fdbee-208">在 Visual Basic tuple 和**ValueTuple**型別，tuple 項目是欄位。</span><span class="sxs-lookup"><span data-stu-id="fdbee-208">In Visual Basic tuples and the **ValueTuple** types, tuple elements are fields.</span></span>

- <span data-ttu-id="fdbee-209">您無法指派有意義的名稱的項目**Tuple**執行個體或**ValueTuple**執行個體。</span><span class="sxs-lookup"><span data-stu-id="fdbee-209">You cannot assign meaningful names to the elements of a **Tuple** instance or of a **ValueTuple** instance.</span></span> <span data-ttu-id="fdbee-210">Visual Basic 可讓您指定的通訊之欄位的意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="fdbee-210">Visual Basic allows you to assign names that communicate the meaning of the fields.</span></span>

- <span data-ttu-id="fdbee-211">內容**Tuple**執行個體是唯讀，則是不變的 tuple。</span><span class="sxs-lookup"><span data-stu-id="fdbee-211">The properties of a **Tuple** instance are read-only; the tuples are immutable.</span></span> <span data-ttu-id="fdbee-212">在 Visual Basic tuple 和**ValueTuple**型別，tuple 欄位是讀寫，則是可變動的 tuple。</span><span class="sxs-lookup"><span data-stu-id="fdbee-212">In Visual Basic tuples and the **ValueTuple** types, tuple fields are read-write; the tuples are mutable.</span></span>

- <span data-ttu-id="fdbee-213">泛型**Tuple**類型是參考型別。</span><span class="sxs-lookup"><span data-stu-id="fdbee-213">The generic **Tuple** types are reference types.</span></span> <span data-ttu-id="fdbee-214">使用這些**Tuple**類型配置物件的方法。</span><span class="sxs-lookup"><span data-stu-id="fdbee-214">Using these **Tuple** types means allocating objects.</span></span> <span data-ttu-id="fdbee-215">在最忙碌路徑上，這可能會對您應用程式的效能造成可觀的衝擊。</span><span class="sxs-lookup"><span data-stu-id="fdbee-215">On hot paths, this can have a measurable impact on your application's performance.</span></span> <span data-ttu-id="fdbee-216">Visual Basic tuple 和**ValueTuple**類型為實值類型。</span><span class="sxs-lookup"><span data-stu-id="fdbee-216">Visual Basic tuples and the **ValueTuple** types are value types.</span></span>

<span data-ttu-id="fdbee-217">中的擴充方法<xref:System.TupleExtensions>類別讓您輕鬆 tuple Visual Basic 和.NET 之間進行轉換**Tuple**物件。</span><span class="sxs-lookup"><span data-stu-id="fdbee-217">Extension methods in the <xref:System.TupleExtensions> class make it easy to convert between Visual Basic tuples and .NET **Tuple** objects.</span></span> <span data-ttu-id="fdbee-218">**ToTuple**方法會將 Visual Basic tuple 轉換至.NET **Tuple**物件，而**ToValueTuple**方法會將轉換.NET **Tuple**Visual Basic tuple 物件。</span><span class="sxs-lookup"><span data-stu-id="fdbee-218">The **ToTuple** method converts a Visual Basic tuple to a .NET **Tuple** object, and the **ToValueTuple** method converts a .NET **Tuple** object to a Visual Basic tuple.</span></span>

<span data-ttu-id="fdbee-219">下列範例會建立 tuple、 將它轉換成.NET **Tuple**物件，並將它回到 Visual Basic tuple。</span><span class="sxs-lookup"><span data-stu-id="fdbee-219">The following example creates a tuple, converts it to a .NET **Tuple** object, and converts it back to a Visual Basic tuple.</span></span> <span data-ttu-id="fdbee-220">然後這個範例會比較此 tuple 與原始以確保它們相等。</span><span class="sxs-lookup"><span data-stu-id="fdbee-220">The example then compares this tuple with the original one to ensure that they are equal.</span></span>

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a><span data-ttu-id="fdbee-221">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fdbee-221">See also</span></span>

[<span data-ttu-id="fdbee-222">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="fdbee-222">Visual Basic Language Reference</span></span>](index.md)  
