---
title: 在 Visual Basic 中的 Tuple
ms.date: 04/23/2017
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
ms.openlocfilehash: 16934232e1e202f1b100680a5101332aa622f2cc
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348494"
---
# <a name="tuples-visual-basic"></a><span data-ttu-id="24ec9-102">Tuple (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24ec9-102">Tuples (Visual Basic)</span></span>

<span data-ttu-id="24ec9-103">從 Visual Basic 2017 開始，Visual Basic 語言提供內建支援，讓 tuple 建立 tuple 和存取的更容易的 tuple 項目。</span><span class="sxs-lookup"><span data-stu-id="24ec9-103">Starting with Visual Basic 2017, the Visual Basic language offers built-in support for tuples that makes creating tuples and accessing the elements of tuples easier.</span></span> <span data-ttu-id="24ec9-104">Tuple 是輕量的資料結構，具有特定的數字和值的序列。</span><span class="sxs-lookup"><span data-stu-id="24ec9-104">A tuple is a lightweight data structure that has a specific number and sequence of values.</span></span> <span data-ttu-id="24ec9-105">當您具現化的元組時，您可以定義數目和每個值 （或元素） 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="24ec9-105">When you instantiate the tuple, you define the number and the data type of each value (or element).</span></span> <span data-ttu-id="24ec9-106">例如，2 tuple （或組） 有兩個項目。</span><span class="sxs-lookup"><span data-stu-id="24ec9-106">For example, a 2-tuple (or pair) has two elements.</span></span> <span data-ttu-id="24ec9-107">第一個可能`Boolean`值，而第二個是`String`。</span><span class="sxs-lookup"><span data-stu-id="24ec9-107">The first might be a `Boolean` value, while the second is a `String`.</span></span> <span data-ttu-id="24ec9-108">Tuple 可以方便將多個值儲存在單一物件，通常是當做從方法傳回多個值的輕量方式使用。</span><span class="sxs-lookup"><span data-stu-id="24ec9-108">Because tuples make it easy to store multiple values in a single object, they are often used as a lightweight way to return multiple values from a method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24ec9-109">Tuple 支援需要<xref:System.ValueTuple>型別。</span><span class="sxs-lookup"><span data-stu-id="24ec9-109">Tuple support requires the <xref:System.ValueTuple> type.</span></span> <span data-ttu-id="24ec9-110">如果未安裝.NET Framework 4.7 中，您必須新增 NuGet 套件`System.ValueTuple`，它位在 NuGet 資源庫。</span><span class="sxs-lookup"><span data-stu-id="24ec9-110">If the .NET Framework 4.7 is not installed, you must add the NuGet package `System.ValueTuple`, which is available on the NuGet Gallery.</span></span> <span data-ttu-id="24ec9-111">沒有這個套件中，您可能會收到編譯錯誤類似於 「 預先定義類型 'ValueTuple(Of,,,)' 未定義或匯入 」。</span><span class="sxs-lookup"><span data-stu-id="24ec9-111">Without this package, you may get a compilation error similar to, "Predefined type 'ValueTuple(Of,,,)' is not defined or imported."</span></span>

## <a name="instantiating-and-using-a-tuple"></a><span data-ttu-id="24ec9-112">具現化，並使用 tuple</span><span class="sxs-lookup"><span data-stu-id="24ec9-112">Instantiating and using a tuple</span></span>

<span data-ttu-id="24ec9-113">方法及其逗點分隔值 im 括號括住，您可以初始化 tuple。</span><span class="sxs-lookup"><span data-stu-id="24ec9-113">You instantiate a tuple by enclosing its comma-delimited values im parentheses.</span></span> <span data-ttu-id="24ec9-114">每個這些值就會變成 tuple 的欄位。</span><span class="sxs-lookup"><span data-stu-id="24ec9-114">Each of those values then becomes a field of the tuple.</span></span> <span data-ttu-id="24ec9-115">比方說，下列程式碼會定義三重 （或 3-tuple） 與`Date`做為其第一個值，`String`做為第二個，和`Boolean`為其第三個。</span><span class="sxs-lookup"><span data-stu-id="24ec9-115">For example, the following code defines a triple (or 3-tuple) with a `Date` as its first value, a `String` as its second, and a `Boolean` as its third.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

<span data-ttu-id="24ec9-116">根據預設，tuple 中每個欄位的名稱含有字串`Item`以及欄位的 tuple 中以一為位置。</span><span class="sxs-lookup"><span data-stu-id="24ec9-116">By default, the name of each field in a tuple consists of the string `Item` along with the field's one-based position in the tuple.</span></span> <span data-ttu-id="24ec9-117">這個的 3 元組，如`Date`欄位是`Item1`，則`String`欄位`Item2`，和`Boolean`欄位是`Item3`。</span><span class="sxs-lookup"><span data-stu-id="24ec9-117">For this 3-tuple, the `Date` field is `Item1`, the `String` field is `Item2`, and the `Boolean` field is `Item3`.</span></span> <span data-ttu-id="24ec9-118">下列範例顯示的上一行程式碼中具現化的元組欄位的值</span><span class="sxs-lookup"><span data-stu-id="24ec9-118">The following example displays the values of fields of the tuple instantiated in the previous line of code</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

<span data-ttu-id="24ec9-119">Visual Basic tuple 的欄位會讀取-寫入;tuple 已具現化之後，您可以修改其值。</span><span class="sxs-lookup"><span data-stu-id="24ec9-119">The fields of a Visual Basic tuple are read-write; after you've instantiated a tuple, you can modify its values.</span></span> <span data-ttu-id="24ec9-120">下列範例會修改兩個 tuple 的前一個範例中所建立的三個欄位，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="24ec9-120">The following example modifies two of the three fields of the tuple created in the previous example and displays the result.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a><span data-ttu-id="24ec9-121">具現化，並使用具名的 tuple</span><span class="sxs-lookup"><span data-stu-id="24ec9-121">Instantiating and using a named tuple</span></span>

<span data-ttu-id="24ec9-122">而不是使用 tuple 欄位的預設名稱，您可以具現化*具名 tuple*藉由將您自己的名稱指派給 tuple 項目。</span><span class="sxs-lookup"><span data-stu-id="24ec9-122">Rather than using default names for a tuple's fields, you can instantiate a *named tuple* by assigning your own names to the tuple's elements.</span></span> <span data-ttu-id="24ec9-123">其指定名稱並可存取 tuple 欄位*或*由其預設名稱。</span><span class="sxs-lookup"><span data-stu-id="24ec9-123">The tuple's fields can then be accessed by their assigned names *or* by their default names.</span></span> <span data-ttu-id="24ec9-124">下列範例在不同之處在於它明確名稱的第一個欄位，具現化相同與之前，3 個 tuple `EventDate`，第二個`Name`，和第三個`IsHoliday`。</span><span class="sxs-lookup"><span data-stu-id="24ec9-124">The following example instantiates the same 3-tuple as previously, except that it explicitly names the first field `EventDate`, the second `Name`, and the third `IsHoliday`.</span></span> <span data-ttu-id="24ec9-125">然後會顯示欄位值，修改它們，並會再次顯示欄位值。</span><span class="sxs-lookup"><span data-stu-id="24ec9-125">It then displays the field values, modifies them, and displays the field values again.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="24ec9-126">Tuple 型別推導</span><span class="sxs-lookup"><span data-stu-id="24ec9-126">Inferred tuple element names</span></span>

<span data-ttu-id="24ec9-127">從 Visual Basic 15.3 開始，Visual Basic 可以推斷 tuple 項目的名稱;您不必明確指派給他們。</span><span class="sxs-lookup"><span data-stu-id="24ec9-127">Starting with Visual Basic 15.3, Visual Basic can infer the names of tuple elements; you do not have to assign them explicitly.</span></span> <span data-ttu-id="24ec9-128">當您初始化 tuple 的一組變數，和您想要的變數名稱相同的元組元素名稱，推斷的元組名稱很有用。</span><span class="sxs-lookup"><span data-stu-id="24ec9-128">Inferred tuple names are useful when you initialize a tuple from a set of variables, and you want the tuple element name to be the same as the variable name.</span></span> 

<span data-ttu-id="24ec9-129">下列範例會建立`stateInfo`tuple，其中包含三個明確具名項目`state`， `stateName`，和`capital`。</span><span class="sxs-lookup"><span data-stu-id="24ec9-129">The following example creates a `stateInfo` tuple that contains three explicitly named elements, `state`, `stateName`, and `capital`.</span></span> <span data-ttu-id="24ec9-130">請注意，在命名項目，元組初始化陳述式只會指派具名項目同名的變數的值。</span><span class="sxs-lookup"><span data-stu-id="24ec9-130">Note that, in naming the elements, the tuple initialization statement simply assigns the named elements the values of the identically named variables.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
<span data-ttu-id="24ec9-131">項目和變數具有相同名稱，因為 Visual Basic 編譯器可以推斷欄位的名稱，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="24ec9-131">Because elements and variables have the same name, the Visual Basic compiler can infer the names of the fields, as the following example shows.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

<span data-ttu-id="24ec9-132">若要啟用推斷的元組元素名稱，您必須定義在 Visual Basic 專案中使用 Visual Basic 編譯器的版本 (\*.vbproj) 檔案：</span><span class="sxs-lookup"><span data-stu-id="24ec9-132">To enable inferred tuple element names, you must define the version of the Visual Basic compiler to use in your Visual Basic project (\*.vbproj) file:</span></span> 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 
```

<span data-ttu-id="24ec9-133">版本號碼可以是任何版本的 Visual Basic 編譯器從 15.3 開始。</span><span class="sxs-lookup"><span data-stu-id="24ec9-133">The version number can be any version of the Visual Basic compiler starting with 15.3.</span></span> <span data-ttu-id="24ec9-134">而不是硬式編碼特定編譯器版本，您也可以指定"Latest"作為值`LangVersion`使用最新版本的系統上安裝的 Visual Basic 編譯器進行編譯。</span><span class="sxs-lookup"><span data-stu-id="24ec9-134">Rather than hard-coding a specific compiler version, you can also specify "Latest" as the value of `LangVersion` to compile with the most recent version of the Visual Basic compiler installed on your system.</span></span>

<span data-ttu-id="24ec9-135">如需詳細資訊，請參閱 <<c0> [ 設定的 Visual Basic 語言版本](../../../language-reference/configure-language-version.md)。</span><span class="sxs-lookup"><span data-stu-id="24ec9-135">For more information, see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

<span data-ttu-id="24ec9-136">在某些情況下，Visual Basic 編譯器無法推斷元組元素名稱，從候選項目名稱和元組欄位只能參考使用預設名稱，例如`Item1`，`Item2`等等。它們包括：</span><span class="sxs-lookup"><span data-stu-id="24ec9-136">In some cases, the Visual Basic compiler cannot infer the tuple element name from the candidate name, and the tuple field can only be referenced using its default name, such as `Item1`, `Item2`, etc. These include:</span></span>

- <span data-ttu-id="24ec9-137">候選名稱是相同的元組成員名稱，例如`Item3`， `Rest`，或`ToString`。</span><span class="sxs-lookup"><span data-stu-id="24ec9-137">The candidate name is the same as the name of a tuple member, such as `Item3`, `Rest`, or `ToString`.</span></span>

- <span data-ttu-id="24ec9-138">候選名稱重複的 tuple 中。</span><span class="sxs-lookup"><span data-stu-id="24ec9-138">The candidate name is duplicated in the tuple.</span></span>
 
<span data-ttu-id="24ec9-139">當欄位名稱推斷失敗時，Visual Basic 不會產生編譯器錯誤，也是在執行階段擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="24ec9-139">When field name inference fails, Visual Basic does not generate a compiler error, nor is an exception thrown at runtime.</span></span> <span data-ttu-id="24ec9-140">相反地，元組欄位，必須以參考其預先定義的名稱，例如`Item1`和`Item2`。</span><span class="sxs-lookup"><span data-stu-id="24ec9-140">Instead, tuple fields must be referenced by their predefined names, such as `Item1` and `Item2`.</span></span> 
  
## <a name="tuples-versus-structures"></a><span data-ttu-id="24ec9-141">Tuple 與結構</span><span class="sxs-lookup"><span data-stu-id="24ec9-141">Tuples versus structures</span></span>

<span data-ttu-id="24ec9-142">Visual Basic tuple 是實值類型的其中一個執行個體**System.ValueTuple**泛型型別。</span><span class="sxs-lookup"><span data-stu-id="24ec9-142">A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types.</span></span> <span data-ttu-id="24ec9-143">例如，`holiday`先前的範例中所定義的 tuple 是的執行個體<xref:System.ValueTuple%603>結構。</span><span class="sxs-lookup"><span data-stu-id="24ec9-143">For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure.</span></span> <span data-ttu-id="24ec9-144">它被設計為輕量級容器以取得資料。</span><span class="sxs-lookup"><span data-stu-id="24ec9-144">It is designed to be a lightweight container for data.</span></span> <span data-ttu-id="24ec9-145">Tuple 的目標是要讓您輕鬆建立具有多個資料項目的物件，因為它缺少的一些功能可能會有一個自訂的結構。</span><span class="sxs-lookup"><span data-stu-id="24ec9-145">Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have.</span></span> <span data-ttu-id="24ec9-146">它們包括：</span><span class="sxs-lookup"><span data-stu-id="24ec9-146">These include:</span></span>

- <span data-ttu-id="24ec9-147">自訂的成員。</span><span class="sxs-lookup"><span data-stu-id="24ec9-147">Custom members.</span></span> <span data-ttu-id="24ec9-148">您無法定義自己的屬性、 方法或事件的 tuple。</span><span class="sxs-lookup"><span data-stu-id="24ec9-148">You cannot define your own properties, methods, or events for a tuple.</span></span>

- <span data-ttu-id="24ec9-149">驗證。</span><span class="sxs-lookup"><span data-stu-id="24ec9-149">Validation.</span></span> <span data-ttu-id="24ec9-150">您無法驗證指派給欄位的資料。</span><span class="sxs-lookup"><span data-stu-id="24ec9-150">You cannot validate the data assigned to fields.</span></span>

- <span data-ttu-id="24ec9-151">不是變性。</span><span class="sxs-lookup"><span data-stu-id="24ec9-151">Immutability.</span></span> <span data-ttu-id="24ec9-152">Visual Basic tuple 是可變動的。</span><span class="sxs-lookup"><span data-stu-id="24ec9-152">Visual Basic tuples are mutable.</span></span> <span data-ttu-id="24ec9-153">相反地，自訂的結構可讓您控制執行個體是否可變動或不可變。</span><span class="sxs-lookup"><span data-stu-id="24ec9-153">In contrast, a custom structure allows you to control whether an instance is mutable or immutable.</span></span>

<span data-ttu-id="24ec9-154">如果自訂成員、 屬性和欄位驗證或不變性是重要的您應該使用 Visual Basic[結構](../../../language-reference/statements/structure-statement.md)陳述式來定義自訂的實值型別。</span><span class="sxs-lookup"><span data-stu-id="24ec9-154">If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.</span></span>

<span data-ttu-id="24ec9-155">Visual Basic tuple 沒有繼承的成員及其**ValueTuple**型別。</span><span class="sxs-lookup"><span data-stu-id="24ec9-155">A Visual Basic tuple does inherit the members of its **ValueTuple** type.</span></span> <span data-ttu-id="24ec9-156">除了其欄位，包括下列方法：</span><span class="sxs-lookup"><span data-stu-id="24ec9-156">In addition to its fields, these include the following methods:</span></span>

| <span data-ttu-id="24ec9-157">成員</span><span class="sxs-lookup"><span data-stu-id="24ec9-157">Member</span></span> | <span data-ttu-id="24ec9-158">描述</span><span class="sxs-lookup"><span data-stu-id="24ec9-158">Description</span></span> |
| ---|---|
| <span data-ttu-id="24ec9-159">CompareTo</span><span class="sxs-lookup"><span data-stu-id="24ec9-159">CompareTo</span></span> | <span data-ttu-id="24ec9-160">比較目前的 tuple，另一個具有相同數目的元素的元組。</span><span class="sxs-lookup"><span data-stu-id="24ec9-160">Compares the current tuple to another tuple with the same number of elements.</span></span> |
| <span data-ttu-id="24ec9-161">等於</span><span class="sxs-lookup"><span data-stu-id="24ec9-161">Equals</span></span> | <span data-ttu-id="24ec9-162">判斷目前的 tuple 是否等於另一個 tuple 或物件。</span><span class="sxs-lookup"><span data-stu-id="24ec9-162">Determines whether the current tuple is equal to another tuple or object.</span></span> |
| <span data-ttu-id="24ec9-163">GetHashCode</span><span class="sxs-lookup"><span data-stu-id="24ec9-163">GetHashCode</span></span> | <span data-ttu-id="24ec9-164">計算目前的執行個體的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="24ec9-164">Calculates the hash code for the current instance.</span></span> |
| <span data-ttu-id="24ec9-165">ToString</span><span class="sxs-lookup"><span data-stu-id="24ec9-165">ToString</span></span> | <span data-ttu-id="24ec9-166">傳回此 tuple，採用下列格式的字串表示法`(Item1, Item2...)`，其中`Item1`和`Item2`代表 tuple 欄位的值。</span><span class="sxs-lookup"><span data-stu-id="24ec9-166">Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields.</span></span> |

<span data-ttu-id="24ec9-167">颾魤 ㄛ **ValueTuple**型別會實作<xref:System.Collections.IStructuralComparable>和<xref:System.Collections.IStructuralEquatable>介面，可讓您定義客戶的比較子。</span><span class="sxs-lookup"><span data-stu-id="24ec9-167">In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define customer comparers.</span></span>

## <a name="assignment-and-tuples"></a><span data-ttu-id="24ec9-168">指派和 Tuple</span><span class="sxs-lookup"><span data-stu-id="24ec9-168">Assignment and tuples</span></span>

<span data-ttu-id="24ec9-169">Visual Basic 支援欄位數目相同的元組類型間的指派。</span><span class="sxs-lookup"><span data-stu-id="24ec9-169">Visual Basic supports assignment between tuple types that have the same number of fields.</span></span> <span data-ttu-id="24ec9-170">如果下列其中一項為真，則可以轉換的欄位型別：</span><span class="sxs-lookup"><span data-stu-id="24ec9-170">The field types can be converted if one of the following is true:</span></span>

- <span data-ttu-id="24ec9-171">來源和目標的欄位都屬於相同的類型。</span><span class="sxs-lookup"><span data-stu-id="24ec9-171">The source and target field are of the same type.</span></span>

- <span data-ttu-id="24ec9-172">定義擴展 （或隱含） 轉換成來源型別的目標類型。</span><span class="sxs-lookup"><span data-stu-id="24ec9-172">A widening (or implicit) conversion of the source type to the target type is defined.</span></span> 

- <span data-ttu-id="24ec9-173">`Option Strict` 是`On`，並縮小 （或明確） 之來源型別的目標類型定義轉換。</span><span class="sxs-lookup"><span data-stu-id="24ec9-173">`Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined.</span></span> <span data-ttu-id="24ec9-174">如果來源值超出目標類型的範圍，則這項轉換會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="24ec9-174">This conversion can throw an exception if the source value is outside the range of the target type.</span></span>

<span data-ttu-id="24ec9-175">不會考慮對指派進行其他轉換。</span><span class="sxs-lookup"><span data-stu-id="24ec9-175">Other conversions are not considered for assignments.</span></span> <span data-ttu-id="24ec9-176">讓我們看看 Tuple 類型之間允許的指派類型。</span><span class="sxs-lookup"><span data-stu-id="24ec9-176">Let's look at the kinds of assignments that are allowed between tuple types.</span></span>

<span data-ttu-id="24ec9-177">請考慮在下列範例中使用的這些參數：</span><span class="sxs-lookup"><span data-stu-id="24ec9-177">Consider these variables used in the following examples:</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

<span data-ttu-id="24ec9-178">前兩個變數中，`unnamed`和`anonymous`，不會有提供欄位的語意名稱。</span><span class="sxs-lookup"><span data-stu-id="24ec9-178">The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields.</span></span> <span data-ttu-id="24ec9-179">欄位名稱都是預設`Item1`和`Item2`。</span><span class="sxs-lookup"><span data-stu-id="24ec9-179">Their field names are the default `Item1` and `Item2`.</span></span> <span data-ttu-id="24ec9-180">最後兩個變數中，`named`和`differentName`語意的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="24ec9-180">The last two variables, `named` and `differentName` have semantic field names.</span></span> <span data-ttu-id="24ec9-181">請注意，這兩個 Tuple 有不同的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="24ec9-181">Note that these two tuples have different names for the fields.</span></span>

<span data-ttu-id="24ec9-182">所有四個 tuple 都有相同數目的欄位 （稱為 'arity'），而且這些欄位的類型完全相同。</span><span class="sxs-lookup"><span data-stu-id="24ec9-182">All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical.</span></span> <span data-ttu-id="24ec9-183">因此，所有這些指派都會運作︰</span><span class="sxs-lookup"><span data-stu-id="24ec9-183">Therefore, all of these assignments work:</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

<span data-ttu-id="24ec9-184">請注意，不會指派 Tuple 的名稱。</span><span class="sxs-lookup"><span data-stu-id="24ec9-184">Notice that the names of the tuples are not assigned.</span></span> <span data-ttu-id="24ec9-185">依欄位在 Tuple 中的順序，指派欄位的值。</span><span class="sxs-lookup"><span data-stu-id="24ec9-185">The values of the fields are assigned following the order of the fields in the tuple.</span></span>

<span data-ttu-id="24ec9-186">最後，請注意，我們可以將指派`named`tuple `conversion` tuple，即使的第一個欄位`named`是`Integer`，和的第一個欄位`conversion`是`Long`。</span><span class="sxs-lookup"><span data-stu-id="24ec9-186">Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`.</span></span> <span data-ttu-id="24ec9-187">此指派會成功，因為轉換`Integer`至`Long`是擴展轉換。</span><span class="sxs-lookup"><span data-stu-id="24ec9-187">This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

<span data-ttu-id="24ec9-188">Tuple 的欄位數目不同則無法指派：</span><span class="sxs-lookup"><span data-stu-id="24ec9-188">Tuples with different numbers of fields are not assignable:</span></span>

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a><span data-ttu-id="24ec9-189">Tuple 作為方法傳回值</span><span class="sxs-lookup"><span data-stu-id="24ec9-189">Tuples as method return values</span></span>

<span data-ttu-id="24ec9-190">方法可傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="24ec9-190">A method can return only a single value.</span></span> <span data-ttu-id="24ec9-191">通常，不過，您想要傳回多個值的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="24ec9-191">Frequently, though, you'd like a method call to return multiple values.</span></span> <span data-ttu-id="24ec9-192">有數種方式可解決這項限制：</span><span class="sxs-lookup"><span data-stu-id="24ec9-192">There are several ways to work around this limitation:</span></span>

- <span data-ttu-id="24ec9-193">您可以建立自訂的類別或結構的屬性或欄位代表的方法所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="24ec9-193">You can create a custom class or structure whose properties or fields represent values returned by the method.</span></span> <span data-ttu-id="24ec9-194">因此是重量級解決方案;它會要求您定義自訂類型，其唯一目的是要擷取的方法呼叫中的值。</span><span class="sxs-lookup"><span data-stu-id="24ec9-194">Thus is a heavyweight solution; it requires that you define a custom type whose only purpose is to retrieve values from a method call.</span></span>

- <span data-ttu-id="24ec9-195">您可以從方法傳回單一值，並將它們傳遞的參考，這個方法會傳回其餘的值。</span><span class="sxs-lookup"><span data-stu-id="24ec9-195">You can return a single value from the method, and return the remaining values by passing them by reference to the method.</span></span> <span data-ttu-id="24ec9-196">這牽涉到變數，而不小心覆寫的傳址方式傳遞的變數值的風險，具現化額外的負荷。</span><span class="sxs-lookup"><span data-stu-id="24ec9-196">This involves the overhead of instantiating a variable and risks inadvertently overwriting the value of the variable that you pass by reference.</span></span>

- <span data-ttu-id="24ec9-197">您可以使用提供輕量型解決方案，以擷取多個傳回值的元組。</span><span class="sxs-lookup"><span data-stu-id="24ec9-197">You can use a tuple, which provides a lightweight solution to retrieving multiple return values.</span></span>

<span data-ttu-id="24ec9-198">例如， **TryParse**方法在.NET 傳回`Boolean`值，指出是否在剖析作業成功。</span><span class="sxs-lookup"><span data-stu-id="24ec9-198">For example, the **TryParse** methods in .NET return a `Boolean` value that indicates whether the parsing operation succeeded.</span></span> <span data-ttu-id="24ec9-199">在剖析作業的結果會傳回給方法的參考所傳遞的變數中。</span><span class="sxs-lookup"><span data-stu-id="24ec9-199">The result of the parsing operation is returned in a variable passed by reference to the method.</span></span> <span data-ttu-id="24ec9-200">一般來說，呼叫剖析方法，例如<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="24ec9-200">Normally, a call to the a parsing method such as <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> looks like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

<span data-ttu-id="24ec9-201">我們可以從剖析的作業傳回 tuple，如果我們將呼叫包裝至<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>我們自己的方法中的方法。</span><span class="sxs-lookup"><span data-stu-id="24ec9-201">We can return a tuple from the parsing operation if we wrap the call to the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method in our own method.</span></span> <span data-ttu-id="24ec9-202">在下列範例中，`NumericLibrary.ParseInteger`呼叫<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>方法，並傳回具有兩個元素的具名元組。</span><span class="sxs-lookup"><span data-stu-id="24ec9-202">In the following example, `NumericLibrary.ParseInteger` calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method and returns a named tuple with two elements.</span></span> 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

<span data-ttu-id="24ec9-203">然後，您可以呼叫的方法，如下所示的程式碼：</span><span class="sxs-lookup"><span data-stu-id="24ec9-203">You can then call the method with code like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a><span data-ttu-id="24ec9-204">Visual Basic 的 tuple 與.NET Framework 中的 tuple</span><span class="sxs-lookup"><span data-stu-id="24ec9-204">Visual Basic tuples and tuples in the .NET Framework</span></span>

<span data-ttu-id="24ec9-205">Visual Basic tuple 是其中一個的執行個體**System.ValueTuple**引進.NET Framework 4.7 中的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="24ec9-205">A Visual Basic tuple is an instance of one of the **System.ValueTuple** generic types, which were introduced in the .NET Framework 4.7.</span></span> <span data-ttu-id="24ec9-206">.NET Framework 也包含一組的泛型**System.Tuple**類別。</span><span class="sxs-lookup"><span data-stu-id="24ec9-206">The .NET Framework also includes a set of generic **System.Tuple** classes.</span></span> <span data-ttu-id="24ec9-207">這些類別，不過，與 Visual Basic tuple 不同， **System.ValueTuple**數種方式中的泛型類型：</span><span class="sxs-lookup"><span data-stu-id="24ec9-207">These classes, however, differ from Visual Basic tuples and the **System.ValueTuple** generic types in a number of ways:</span></span>

- <span data-ttu-id="24ec9-208">項目**Tuple**類別是名為屬性`Item1`， `Item2`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="24ec9-208">The elements of the **Tuple** classes are properties named `Item1`, `Item2`, and so on.</span></span> <span data-ttu-id="24ec9-209">在 Visual Basic 的 tuple 與**ValueTuple**型別，tuple 項目是欄位。</span><span class="sxs-lookup"><span data-stu-id="24ec9-209">In Visual Basic tuples and the **ValueTuple** types, tuple elements are fields.</span></span>

- <span data-ttu-id="24ec9-210">您無法將有意義的名稱指派至的項目**Tuple**執行個體或是**ValueTuple**執行個體。</span><span class="sxs-lookup"><span data-stu-id="24ec9-210">You cannot assign meaningful names to the elements of a **Tuple** instance or of a **ValueTuple** instance.</span></span> <span data-ttu-id="24ec9-211">Visual Basic 可讓您指派通訊之欄位的意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="24ec9-211">Visual Basic allows you to assign names that communicate the meaning of the fields.</span></span>

- <span data-ttu-id="24ec9-212">屬性**Tuple**執行個體是唯讀，是不可變的 tuple。</span><span class="sxs-lookup"><span data-stu-id="24ec9-212">The properties of a **Tuple** instance are read-only; the tuples are immutable.</span></span> <span data-ttu-id="24ec9-213">在 Visual Basic 的 tuple 與**ValueTuple**類型、 元組欄位會讀取寫入; 是可變動的 tuple。</span><span class="sxs-lookup"><span data-stu-id="24ec9-213">In Visual Basic tuples and the **ValueTuple** types, tuple fields are read-write; the tuples are mutable.</span></span>

- <span data-ttu-id="24ec9-214">泛型**Tuple**型別是參考型別。</span><span class="sxs-lookup"><span data-stu-id="24ec9-214">The generic **Tuple** types are reference types.</span></span> <span data-ttu-id="24ec9-215">使用這些**Tuple**類型表示配置物件。</span><span class="sxs-lookup"><span data-stu-id="24ec9-215">Using these **Tuple** types means allocating objects.</span></span> <span data-ttu-id="24ec9-216">在最忙碌路徑上，這可能會對您應用程式的效能造成可觀的衝擊。</span><span class="sxs-lookup"><span data-stu-id="24ec9-216">On hot paths, this can have a measurable impact on your application's performance.</span></span> <span data-ttu-id="24ec9-217">Visual Basic 的 tuple 與**ValueTuple**類型為實值型別。</span><span class="sxs-lookup"><span data-stu-id="24ec9-217">Visual Basic tuples and the **ValueTuple** types are value types.</span></span>

<span data-ttu-id="24ec9-218">中的擴充方法<xref:System.TupleExtensions>類別讓您輕鬆轉換 Visual Basic 的 tuple 與.NET 之間**Tuple**物件。</span><span class="sxs-lookup"><span data-stu-id="24ec9-218">Extension methods in the <xref:System.TupleExtensions> class make it easy to convert between Visual Basic tuples and .NET **Tuple** objects.</span></span> <span data-ttu-id="24ec9-219">**ToTuple**方法會將.NET 中的 Visual Basic tuple **Tuple**物件，而**ToValueTuple**方法會將轉換.NET **Tuple**Visual Basic tuple 物件。</span><span class="sxs-lookup"><span data-stu-id="24ec9-219">The **ToTuple** method converts a Visual Basic tuple to a .NET **Tuple** object, and the **ToValueTuple** method converts a .NET **Tuple** object to a Visual Basic tuple.</span></span>

<span data-ttu-id="24ec9-220">下列範例建立的元組，然後將它轉換成.NET **Tuple**物件，並將它回復為 Visual Basic 的元組。</span><span class="sxs-lookup"><span data-stu-id="24ec9-220">The following example creates a tuple, converts it to a .NET **Tuple** object, and converts it back to a Visual Basic tuple.</span></span> <span data-ttu-id="24ec9-221">然後這個範例會比較此 tuple 與原始以確保它們相等。</span><span class="sxs-lookup"><span data-stu-id="24ec9-221">The example then compares this tuple with the original one to ensure that they are equal.</span></span>

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a><span data-ttu-id="24ec9-222">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24ec9-222">See also</span></span>

- [<span data-ttu-id="24ec9-223">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="24ec9-223">Visual Basic Language Reference</span></span>](index.md)
