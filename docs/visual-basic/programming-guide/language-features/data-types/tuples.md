---
title: Tuple
ms.date: 04/23/2017
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
ms.openlocfilehash: b169a1c13b3f20d7b5e2a1386cfb28a9cc093dcd
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559085"
---
# <a name="tuples-visual-basic"></a><span data-ttu-id="b93b2-102">元組 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="b93b2-102">Tuples (Visual Basic)</span></span>

<span data-ttu-id="b93b2-103">從 Visual Basic 2017 開始，Visual Basic 語言為元組提供內建支援，可讓您更輕鬆地建立元組及存取元組的元素。</span><span class="sxs-lookup"><span data-stu-id="b93b2-103">Starting with Visual Basic 2017, the Visual Basic language offers built-in support for tuples that makes creating tuples and accessing the elements of tuples easier.</span></span> <span data-ttu-id="b93b2-104">元組是一種輕量的資料結構，具有特定數目和順序的值。</span><span class="sxs-lookup"><span data-stu-id="b93b2-104">A tuple is a lightweight data structure that has a specific number and sequence of values.</span></span> <span data-ttu-id="b93b2-105">當您具現化元組時，您會定義每個值 (或元素) 的數目和資料類型。</span><span class="sxs-lookup"><span data-stu-id="b93b2-105">When you instantiate the tuple, you define the number and the data type of each value (or element).</span></span> <span data-ttu-id="b93b2-106">例如，2個元組 (或配對) 有兩個元素。</span><span class="sxs-lookup"><span data-stu-id="b93b2-106">For example, a 2-tuple (or pair) has two elements.</span></span> <span data-ttu-id="b93b2-107">第一個可能是 `Boolean` 值，而第二個則是 `String` 。</span><span class="sxs-lookup"><span data-stu-id="b93b2-107">The first might be a `Boolean` value, while the second is a `String`.</span></span> <span data-ttu-id="b93b2-108">因為元組可讓您輕鬆地將多個值儲存在單一物件中，所以通常會用來作為從方法傳回多個值的輕量方式。</span><span class="sxs-lookup"><span data-stu-id="b93b2-108">Because tuples make it easy to store multiple values in a single object, they are often used as a lightweight way to return multiple values from a method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b93b2-109">元組支援需要 <xref:System.ValueTuple> 類型。</span><span class="sxs-lookup"><span data-stu-id="b93b2-109">Tuple support requires the <xref:System.ValueTuple> type.</span></span> <span data-ttu-id="b93b2-110">如果未安裝 .NET Framework 4.7，則您必須新增 nuget 套件 `System.ValueTuple` （可在 nuget 資源庫中取得）。</span><span class="sxs-lookup"><span data-stu-id="b93b2-110">If the .NET Framework 4.7 is not installed, you must add the NuGet package `System.ValueTuple`, which is available on the NuGet Gallery.</span></span> <span data-ttu-id="b93b2-111">如果沒有此封裝，您可能會收到類似以下的編譯錯誤：「未定義或匯入,,, ) ' 的預先定義類型 ValueTuple (」。</span><span class="sxs-lookup"><span data-stu-id="b93b2-111">Without this package, you may get a compilation error similar to, "Predefined type 'ValueTuple(Of,,,)' is not defined or imported."</span></span>

## <a name="instantiating-and-using-a-tuple"></a><span data-ttu-id="b93b2-112">具現化和使用元組</span><span class="sxs-lookup"><span data-stu-id="b93b2-112">Instantiating and using a tuple</span></span>

<span data-ttu-id="b93b2-113">您可以用括弧括住其逗點分隔值，將元組具現化。</span><span class="sxs-lookup"><span data-stu-id="b93b2-113">You instantiate a tuple by enclosing its comma-delimited values in parentheses.</span></span> <span data-ttu-id="b93b2-114">然後，每一個值都會變成元組的欄位。</span><span class="sxs-lookup"><span data-stu-id="b93b2-114">Each of those values then becomes a field of the tuple.</span></span> <span data-ttu-id="b93b2-115">例如，下列程式碼會定義三個 (或3個元組) ，其中包含 `Date` 做為其第一個值、 `String` 第二個值，以及 `Boolean` 做為第三個。</span><span class="sxs-lookup"><span data-stu-id="b93b2-115">For example, the following code defines a triple (or 3-tuple) with a `Date` as its first value, a `String` as its second, and a `Boolean` as its third.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

<span data-ttu-id="b93b2-116">依預設，元組中每個欄位的名稱都包含字串， `Item` 以及元組中欄位的一個位置。</span><span class="sxs-lookup"><span data-stu-id="b93b2-116">By default, the name of each field in a tuple consists of the string `Item` along with the field's one-based position in the tuple.</span></span> <span data-ttu-id="b93b2-117">這3個元組的欄位是，欄位是 `Date` `Item1` ，欄位 `String` `Item2` `Boolean` 是 `Item3` 。</span><span class="sxs-lookup"><span data-stu-id="b93b2-117">For this 3-tuple, the `Date` field is `Item1`, the `String` field is `Item2`, and the `Boolean` field is `Item3`.</span></span> <span data-ttu-id="b93b2-118">下列範例會顯示在前一行程式碼中具現化之元組的欄位值</span><span class="sxs-lookup"><span data-stu-id="b93b2-118">The following example displays the values of fields of the tuple instantiated in the previous line of code</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

<span data-ttu-id="b93b2-119">Visual Basic 元組的欄位為讀寫;在具現化元組之後，您可以修改其值。</span><span class="sxs-lookup"><span data-stu-id="b93b2-119">The fields of a Visual Basic tuple are read-write; after you've instantiated a tuple, you can modify its values.</span></span> <span data-ttu-id="b93b2-120">下列範例會修改前一個範例中所建立之元組的三個欄位中的兩個，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="b93b2-120">The following example modifies two of the three fields of the tuple created in the previous example and displays the result.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a><span data-ttu-id="b93b2-121">具現化和使用命名的元組</span><span class="sxs-lookup"><span data-stu-id="b93b2-121">Instantiating and using a named tuple</span></span>

<span data-ttu-id="b93b2-122">您可以將自己的名稱指派給元組的元素，以具現化 *命名的元組* ，而不是使用元組欄位的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="b93b2-122">Rather than using default names for a tuple's fields, you can instantiate a *named tuple* by assigning your own names to the tuple's elements.</span></span> <span data-ttu-id="b93b2-123">然後，元組的欄位可以依其指派的名稱 *或* 預設名稱存取。</span><span class="sxs-lookup"><span data-stu-id="b93b2-123">The tuple's fields can then be accessed by their assigned names *or* by their default names.</span></span> <span data-ttu-id="b93b2-124">下列範例會具現化與先前相同的3個元組，差別在於它會明確命名第一個欄位 `EventDate` 、第二個 `Name` 和第三個 `IsHoliday` 。</span><span class="sxs-lookup"><span data-stu-id="b93b2-124">The following example instantiates the same 3-tuple as previously, except that it explicitly names the first field `EventDate`, the second `Name`, and the third `IsHoliday`.</span></span> <span data-ttu-id="b93b2-125">然後，它會顯示域值、修改它們，然後再次顯示域值。</span><span class="sxs-lookup"><span data-stu-id="b93b2-125">It then displays the field values, modifies them, and displays the field values again.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="b93b2-126">Tuple 型別推導</span><span class="sxs-lookup"><span data-stu-id="b93b2-126">Inferred tuple element names</span></span>

<span data-ttu-id="b93b2-127">從 Visual Basic 15.3 開始，Visual Basic 可以推斷元組元素的名稱;您不需要明確地指派它們。</span><span class="sxs-lookup"><span data-stu-id="b93b2-127">Starting with Visual Basic 15.3, Visual Basic can infer the names of tuple elements; you do not have to assign them explicitly.</span></span> <span data-ttu-id="b93b2-128">當您從一組變數初始化元組，且您希望元組專案名稱與變數名稱相同時，推斷的元組名稱很有用。</span><span class="sxs-lookup"><span data-stu-id="b93b2-128">Inferred tuple names are useful when you initialize a tuple from a set of variables, and you want the tuple element name to be the same as the variable name.</span></span>

<span data-ttu-id="b93b2-129">下列範例會建立一個 `stateInfo` 元組，其中包含三個明確命名的元素、、 `state` `stateName` 和 `capital` 。</span><span class="sxs-lookup"><span data-stu-id="b93b2-129">The following example creates a `stateInfo` tuple that contains three explicitly named elements, `state`, `stateName`, and `capital`.</span></span> <span data-ttu-id="b93b2-130">請注意，在為專案命名時，元組初始化語句只會將相同名稱之變數的值指派給命名元素。</span><span class="sxs-lookup"><span data-stu-id="b93b2-130">Note that, in naming the elements, the tuple initialization statement simply assigns the named elements the values of the identically named variables.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]

<span data-ttu-id="b93b2-131">因為元素和變數具有相同的名稱，所以 Visual Basic 編譯器可以推斷欄位的名稱，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b93b2-131">Because elements and variables have the same name, the Visual Basic compiler can infer the names of the fields, as the following example shows.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

<span data-ttu-id="b93b2-132">若要啟用推斷的元組元素名稱，您必須定義要在 Visual Basic 專案中使用的 Visual Basic 編譯器版本 (\* . vbproj) 檔：</span><span class="sxs-lookup"><span data-stu-id="b93b2-132">To enable inferred tuple element names, you must define the version of the Visual Basic compiler to use in your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.3</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="b93b2-133">版本號碼可以是從15.3 開始的任何 Visual Basic 編譯器版本。</span><span class="sxs-lookup"><span data-stu-id="b93b2-133">The version number can be any version of the Visual Basic compiler starting with 15.3.</span></span> <span data-ttu-id="b93b2-134">您也可以指定「最新」作為的值， `LangVersion` 以在您的系統上安裝的 Visual Basic 編譯器的最新版本進行編譯，而不是針對特定編譯器版本進行硬式編碼。</span><span class="sxs-lookup"><span data-stu-id="b93b2-134">Rather than hard-coding a specific compiler version, you can also specify "Latest" as the value of `LangVersion` to compile with the most recent version of the Visual Basic compiler installed on your system.</span></span>

<span data-ttu-id="b93b2-135">如需詳細資訊，請參閱 [設定 Visual Basic 語言版本](../../../language-reference/configure-language-version.md)。</span><span class="sxs-lookup"><span data-stu-id="b93b2-135">For more information, see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

<span data-ttu-id="b93b2-136">在某些情況下，Visual Basic 編譯器無法從候選名稱推斷元組專案名稱，而且只能使用它的預設名稱（例如、等）來參考元組 `Item1` 欄位 `Item2` 。這些包括：</span><span class="sxs-lookup"><span data-stu-id="b93b2-136">In some cases, the Visual Basic compiler cannot infer the tuple element name from the candidate name, and the tuple field can only be referenced using its default name, such as `Item1`, `Item2`, etc. These include:</span></span>

- <span data-ttu-id="b93b2-137">候選名稱與元組成員的名稱相同，例如 `Item3` 、 `Rest` 或 `ToString` 。</span><span class="sxs-lookup"><span data-stu-id="b93b2-137">The candidate name is the same as the name of a tuple member, such as `Item3`, `Rest`, or `ToString`.</span></span>

- <span data-ttu-id="b93b2-138">元組中的候選名稱是重複的。</span><span class="sxs-lookup"><span data-stu-id="b93b2-138">The candidate name is duplicated in the tuple.</span></span>

<span data-ttu-id="b93b2-139">當功能變數名稱推斷失敗時，Visual Basic 不會產生編譯器錯誤，也不會在執行時間擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b93b2-139">When field name inference fails, Visual Basic does not generate a compiler error, nor is an exception thrown at runtime.</span></span> <span data-ttu-id="b93b2-140">相反地，元組欄位必須由其預先定義的名稱參考，例如 `Item1` 和 `Item2` 。</span><span class="sxs-lookup"><span data-stu-id="b93b2-140">Instead, tuple fields must be referenced by their predefined names, such as `Item1` and `Item2`.</span></span>

## <a name="tuples-versus-structures"></a><span data-ttu-id="b93b2-141">元組與結構的比較</span><span class="sxs-lookup"><span data-stu-id="b93b2-141">Tuples versus structures</span></span>

<span data-ttu-id="b93b2-142">Visual Basic 元組是實數值型別，它是 **ValueTuple** 泛型型別的其中一個實例。</span><span class="sxs-lookup"><span data-stu-id="b93b2-142">A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types.</span></span> <span data-ttu-id="b93b2-143">例如， `holiday` 在上一個範例中定義的元組是結構的實例 <xref:System.ValueTuple%603> 。</span><span class="sxs-lookup"><span data-stu-id="b93b2-143">For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure.</span></span> <span data-ttu-id="b93b2-144">它是設計成資料的輕量容器。</span><span class="sxs-lookup"><span data-stu-id="b93b2-144">It is designed to be a lightweight container for data.</span></span> <span data-ttu-id="b93b2-145">因為元組旨在讓您輕鬆地建立具有多個資料項目的物件，所以它缺少自訂結構可能具有的部分功能。</span><span class="sxs-lookup"><span data-stu-id="b93b2-145">Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have.</span></span> <span data-ttu-id="b93b2-146">其中包括：</span><span class="sxs-lookup"><span data-stu-id="b93b2-146">These include:</span></span>

- <span data-ttu-id="b93b2-147">自訂成員。</span><span class="sxs-lookup"><span data-stu-id="b93b2-147">Custom members.</span></span> <span data-ttu-id="b93b2-148">您無法為元組定義您自己的屬性、方法或事件。</span><span class="sxs-lookup"><span data-stu-id="b93b2-148">You cannot define your own properties, methods, or events for a tuple.</span></span>

- <span data-ttu-id="b93b2-149">驗證：</span><span class="sxs-lookup"><span data-stu-id="b93b2-149">Validation.</span></span> <span data-ttu-id="b93b2-150">您無法驗證指派給欄位的資料。</span><span class="sxs-lookup"><span data-stu-id="b93b2-150">You cannot validate the data assigned to fields.</span></span>

- <span data-ttu-id="b93b2-151">不變性.</span><span class="sxs-lookup"><span data-stu-id="b93b2-151">Immutability.</span></span> <span data-ttu-id="b93b2-152">Visual Basic 元組是可變動的。</span><span class="sxs-lookup"><span data-stu-id="b93b2-152">Visual Basic tuples are mutable.</span></span> <span data-ttu-id="b93b2-153">相反地，自訂結構可讓您控制實例是否可變動或不可變。</span><span class="sxs-lookup"><span data-stu-id="b93b2-153">In contrast, a custom structure allows you to control whether an instance is mutable or immutable.</span></span>

<span data-ttu-id="b93b2-154">如果自訂成員、屬性和欄位驗證或永久性很重要，您應該使用 Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) 語句來定義自訂實值型別。</span><span class="sxs-lookup"><span data-stu-id="b93b2-154">If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.</span></span>

<span data-ttu-id="b93b2-155">Visual Basic 元組會繼承其 **ValueTuple** 類型的成員。</span><span class="sxs-lookup"><span data-stu-id="b93b2-155">A Visual Basic tuple does inherit the members of its **ValueTuple** type.</span></span> <span data-ttu-id="b93b2-156">除了其欄位之外，這些還包括下列方法：</span><span class="sxs-lookup"><span data-stu-id="b93b2-156">In addition to its fields, these include the following methods:</span></span>

| <span data-ttu-id="b93b2-157">方法</span><span class="sxs-lookup"><span data-stu-id="b93b2-157">Method</span></span> | <span data-ttu-id="b93b2-158">描述</span><span class="sxs-lookup"><span data-stu-id="b93b2-158">Description</span></span> |
| ---|---|
| <span data-ttu-id="b93b2-159">CompareTo</span><span class="sxs-lookup"><span data-stu-id="b93b2-159">CompareTo</span></span> | <span data-ttu-id="b93b2-160">比較目前的元組與另一個具有相同元素數目的元組。</span><span class="sxs-lookup"><span data-stu-id="b93b2-160">Compares the current tuple to another tuple with the same number of elements.</span></span> |
| <span data-ttu-id="b93b2-161">Equals</span><span class="sxs-lookup"><span data-stu-id="b93b2-161">Equals</span></span> | <span data-ttu-id="b93b2-162">判斷目前的元組是否等於另一個元組或物件。</span><span class="sxs-lookup"><span data-stu-id="b93b2-162">Determines whether the current tuple is equal to another tuple or object.</span></span> |
| <span data-ttu-id="b93b2-163">GetHashCode</span><span class="sxs-lookup"><span data-stu-id="b93b2-163">GetHashCode</span></span> | <span data-ttu-id="b93b2-164">計算目前實例的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="b93b2-164">Calculates the hash code for the current instance.</span></span> |
| <span data-ttu-id="b93b2-165">ToString</span><span class="sxs-lookup"><span data-stu-id="b93b2-165">ToString</span></span> | <span data-ttu-id="b93b2-166">傳回這個元組的字串表示，其採用格式 `(Item1, Item2...)` ，其中 `Item1` 和 `Item2` 代表元組欄位的值。</span><span class="sxs-lookup"><span data-stu-id="b93b2-166">Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields.</span></span> |

<span data-ttu-id="b93b2-167">此外， **ValueTuple** 型別會執行 <xref:System.Collections.IStructuralComparable> 和 <xref:System.Collections.IStructuralEquatable> 介面，可讓您定義自訂比較子。</span><span class="sxs-lookup"><span data-stu-id="b93b2-167">In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define custom comparers.</span></span>

## <a name="assignment-and-tuples"></a><span data-ttu-id="b93b2-168">指派和 Tuple</span><span class="sxs-lookup"><span data-stu-id="b93b2-168">Assignment and tuples</span></span>

<span data-ttu-id="b93b2-169">Visual Basic 支援在具有相同欄位數目的元組類型之間指派。</span><span class="sxs-lookup"><span data-stu-id="b93b2-169">Visual Basic supports assignment between tuple types that have the same number of fields.</span></span> <span data-ttu-id="b93b2-170">如果下列其中一項為真，則可以轉換欄位類型：</span><span class="sxs-lookup"><span data-stu-id="b93b2-170">The field types can be converted if one of the following is true:</span></span>

- <span data-ttu-id="b93b2-171">來源和目標欄位的類型相同。</span><span class="sxs-lookup"><span data-stu-id="b93b2-171">The source and target field are of the same type.</span></span>

- <span data-ttu-id="b93b2-172">已定義將來源類型轉換成目標型別的擴展 (或隱含) 轉換。</span><span class="sxs-lookup"><span data-stu-id="b93b2-172">A widening (or implicit) conversion of the source type to the target type is defined.</span></span>

- <span data-ttu-id="b93b2-173">`Option Strict` 是 `On` ，而且會定義將來源類型轉換成目標型別的縮小 (或明確) 轉換。</span><span class="sxs-lookup"><span data-stu-id="b93b2-173">`Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined.</span></span> <span data-ttu-id="b93b2-174">如果來源值超出目標型別的範圍，則這項轉換可能會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b93b2-174">This conversion can throw an exception if the source value is outside the range of the target type.</span></span>

<span data-ttu-id="b93b2-175">不會考慮對指派進行其他轉換。</span><span class="sxs-lookup"><span data-stu-id="b93b2-175">Other conversions are not considered for assignments.</span></span> <span data-ttu-id="b93b2-176">讓我們看看 Tuple 類型之間允許的指派類型。</span><span class="sxs-lookup"><span data-stu-id="b93b2-176">Let's look at the kinds of assignments that are allowed between tuple types.</span></span>

<span data-ttu-id="b93b2-177">請考慮在下列範例中使用的這些參數：</span><span class="sxs-lookup"><span data-stu-id="b93b2-177">Consider these variables used in the following examples:</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

<span data-ttu-id="b93b2-178">前兩個變數（ `unnamed` 和 `anonymous` ）沒有針對欄位提供的語義名稱。</span><span class="sxs-lookup"><span data-stu-id="b93b2-178">The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields.</span></span> <span data-ttu-id="b93b2-179">它們的功能變數名稱是預設值 `Item1` 和 `Item2` 。</span><span class="sxs-lookup"><span data-stu-id="b93b2-179">Their field names are the default `Item1` and `Item2`.</span></span> <span data-ttu-id="b93b2-180">最後兩個變數， `named` 並 `differentName` 具有語義功能變數名稱稱。</span><span class="sxs-lookup"><span data-stu-id="b93b2-180">The last two variables, `named` and `differentName` have semantic field names.</span></span> <span data-ttu-id="b93b2-181">請注意，這兩個 Tuple 有不同的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="b93b2-181">Note that these two tuples have different names for the fields.</span></span>

<span data-ttu-id="b93b2-182">這四個元組都有相同數目的欄位 (稱為「arity」 ) ，而這些欄位的類型則相同。</span><span class="sxs-lookup"><span data-stu-id="b93b2-182">All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical.</span></span> <span data-ttu-id="b93b2-183">因此，所有這些指派都會運作︰</span><span class="sxs-lookup"><span data-stu-id="b93b2-183">Therefore, all of these assignments work:</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

<span data-ttu-id="b93b2-184">請注意，不會指派 Tuple 的名稱。</span><span class="sxs-lookup"><span data-stu-id="b93b2-184">Notice that the names of the tuples are not assigned.</span></span> <span data-ttu-id="b93b2-185">依欄位在 Tuple 中的順序，指派欄位的值。</span><span class="sxs-lookup"><span data-stu-id="b93b2-185">The values of the fields are assigned following the order of the fields in the tuple.</span></span>

<span data-ttu-id="b93b2-186">最後，請注意，我們可以將 `named` 元組指派給 `conversion` 元組，雖然的第一個欄位 `named` 是 `Integer` ，而的第一個欄位 `conversion` 是 `Long` 。</span><span class="sxs-lookup"><span data-stu-id="b93b2-186">Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`.</span></span> <span data-ttu-id="b93b2-187">這項指派會成功，因為將轉換成 `Integer` `Long` 是擴輾轉換。</span><span class="sxs-lookup"><span data-stu-id="b93b2-187">This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

<span data-ttu-id="b93b2-188">具有不同欄位數目的元組無法指派：</span><span class="sxs-lookup"><span data-stu-id="b93b2-188">Tuples with different numbers of fields are not assignable:</span></span>

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a><span data-ttu-id="b93b2-189">Tuple 作為方法傳回值</span><span class="sxs-lookup"><span data-stu-id="b93b2-189">Tuples as method return values</span></span>

<span data-ttu-id="b93b2-190">方法只能傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="b93b2-190">A method can return only a single value.</span></span> <span data-ttu-id="b93b2-191">不過，通常您會想要方法呼叫傳回多個值。</span><span class="sxs-lookup"><span data-stu-id="b93b2-191">Frequently, though, you'd like a method call to return multiple values.</span></span> <span data-ttu-id="b93b2-192">有幾種方法可以解決這項限制：</span><span class="sxs-lookup"><span data-stu-id="b93b2-192">There are several ways to work around this limitation:</span></span>

- <span data-ttu-id="b93b2-193">您可以建立自訂類別或結構，其屬性或欄位代表方法所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="b93b2-193">You can create a custom class or structure whose properties or fields represent values returned by the method.</span></span> <span data-ttu-id="b93b2-194">因此是重量級的解決方案;您需要定義一個自訂型別，其唯一目的是從方法呼叫中取出值。</span><span class="sxs-lookup"><span data-stu-id="b93b2-194">Thus is a heavyweight solution; it requires that you define a custom type whose only purpose is to retrieve values from a method call.</span></span>

- <span data-ttu-id="b93b2-195">您可以從方法傳回單一值，然後藉由傳址方式將這些值傳遞給方法，以傳回其餘的值。</span><span class="sxs-lookup"><span data-stu-id="b93b2-195">You can return a single value from the method, and return the remaining values by passing them by reference to the method.</span></span> <span data-ttu-id="b93b2-196">這包括將變數具現化的額外負荷，以及不小心覆寫您以傳址方式傳遞之變數值的風險。</span><span class="sxs-lookup"><span data-stu-id="b93b2-196">This involves the overhead of instantiating a variable and risks inadvertently overwriting the value of the variable that you pass by reference.</span></span>

- <span data-ttu-id="b93b2-197">您可以使用元組，以提供輕量解決方案來抓取多個傳回值。</span><span class="sxs-lookup"><span data-stu-id="b93b2-197">You can use a tuple, which provides a lightweight solution to retrieving multiple return values.</span></span>

<span data-ttu-id="b93b2-198">例如，.NET 中的 **TryParse** 方法會傳回一個 `Boolean` 值，指出剖析作業是否成功。</span><span class="sxs-lookup"><span data-stu-id="b93b2-198">For example, the **TryParse** methods in .NET return a `Boolean` value that indicates whether the parsing operation succeeded.</span></span> <span data-ttu-id="b93b2-199">剖析作業的結果會在以傳址方式傳遞給方法的變數中傳回。</span><span class="sxs-lookup"><span data-stu-id="b93b2-199">The result of the parsing operation is returned in a variable passed by reference to the method.</span></span> <span data-ttu-id="b93b2-200">一般來說，呼叫剖析方法（例如） <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> 看起來像下面這樣：</span><span class="sxs-lookup"><span data-stu-id="b93b2-200">Normally, a call to the a parsing method such as <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> looks like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

<span data-ttu-id="b93b2-201">如果我們在自己的方法中包裝方法的呼叫，我們可以從剖析作業傳回元組 <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b93b2-201">We can return a tuple from the parsing operation if we wrap the call to the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method in our own method.</span></span> <span data-ttu-id="b93b2-202">在下列範例中，會 `NumericLibrary.ParseInteger` 呼叫 <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> 方法，並傳回具有兩個元素的命名元組。</span><span class="sxs-lookup"><span data-stu-id="b93b2-202">In the following example, `NumericLibrary.ParseInteger` calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method and returns a named tuple with two elements.</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

<span data-ttu-id="b93b2-203">然後，您可以使用如下的程式碼呼叫方法：</span><span class="sxs-lookup"><span data-stu-id="b93b2-203">You can then call the method with code like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a><span data-ttu-id="b93b2-204">.NET Framework 中的 Visual Basic 元組和元組</span><span class="sxs-lookup"><span data-stu-id="b93b2-204">Visual Basic tuples and tuples in the .NET Framework</span></span>

<span data-ttu-id="b93b2-205">Visual Basic 元組是在 .NET Framework 4.7 中引進的其中一個 ValueTuple 泛型型別的實例 **。**</span><span class="sxs-lookup"><span data-stu-id="b93b2-205">A Visual Basic tuple is an instance of one of the **System.ValueTuple** generic types, which were introduced in the .NET Framework 4.7.</span></span> <span data-ttu-id="b93b2-206">.NET Framework 也包含一組泛型 **system.object** 類別。</span><span class="sxs-lookup"><span data-stu-id="b93b2-206">The .NET Framework also includes a set of generic **System.Tuple** classes.</span></span> <span data-ttu-id="b93b2-207">不過，這些類別與 Visual Basic 的元組和 **ValueTuple** 泛型型別有許多不同之處：</span><span class="sxs-lookup"><span data-stu-id="b93b2-207">These classes, however, differ from Visual Basic tuples and the **System.ValueTuple** generic types in a number of ways:</span></span>

- <span data-ttu-id="b93b2-208">**元組**類別的元素是名為 `Item1` 、等的屬性 `Item2` 。</span><span class="sxs-lookup"><span data-stu-id="b93b2-208">The elements of the **Tuple** classes are properties named `Item1`, `Item2`, and so on.</span></span> <span data-ttu-id="b93b2-209">在 Visual Basic 元組和 **ValueTuple** 類型中，元組元素為欄位。</span><span class="sxs-lookup"><span data-stu-id="b93b2-209">In Visual Basic tuples and the **ValueTuple** types, tuple elements are fields.</span></span>

- <span data-ttu-id="b93b2-210">您無法將有意義的名稱指派給 **元組** 實例的元素或 **ValueTuple** 實例。</span><span class="sxs-lookup"><span data-stu-id="b93b2-210">You cannot assign meaningful names to the elements of a **Tuple** instance or of a **ValueTuple** instance.</span></span> <span data-ttu-id="b93b2-211">Visual Basic 可讓您指派用來傳達欄位意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="b93b2-211">Visual Basic allows you to assign names that communicate the meaning of the fields.</span></span>

- <span data-ttu-id="b93b2-212">**元組**實例的屬性是唯讀的;元組是不可變的。</span><span class="sxs-lookup"><span data-stu-id="b93b2-212">The properties of a **Tuple** instance are read-only; the tuples are immutable.</span></span> <span data-ttu-id="b93b2-213">在 Visual Basic 元組和 **ValueTuple** 類型中，元組欄位為讀寫;元組是可變動的。</span><span class="sxs-lookup"><span data-stu-id="b93b2-213">In Visual Basic tuples and the **ValueTuple** types, tuple fields are read-write; the tuples are mutable.</span></span>

- <span data-ttu-id="b93b2-214">泛型 **元組** 類型是參考型別。</span><span class="sxs-lookup"><span data-stu-id="b93b2-214">The generic **Tuple** types are reference types.</span></span> <span data-ttu-id="b93b2-215">使用這些 **元組** 類型表示要設定物件。</span><span class="sxs-lookup"><span data-stu-id="b93b2-215">Using these **Tuple** types means allocating objects.</span></span> <span data-ttu-id="b93b2-216">在最忙碌路徑上，這可能會對您應用程式的效能造成可觀的衝擊。</span><span class="sxs-lookup"><span data-stu-id="b93b2-216">On hot paths, this can have a measurable impact on your application's performance.</span></span> <span data-ttu-id="b93b2-217">Visual Basic 元組和 **ValueTuple** 類型都是實數值型別。</span><span class="sxs-lookup"><span data-stu-id="b93b2-217">Visual Basic tuples and the **ValueTuple** types are value types.</span></span>

<span data-ttu-id="b93b2-218">類別中的擴充方法 <xref:System.TupleExtensions> 可讓您輕鬆地在 Visual Basic 元組和 .Net **元組** 物件之間進行轉換。</span><span class="sxs-lookup"><span data-stu-id="b93b2-218">Extension methods in the <xref:System.TupleExtensions> class make it easy to convert between Visual Basic tuples and .NET **Tuple** objects.</span></span> <span data-ttu-id="b93b2-219">**ToTuple**方法會將 Visual Basic 元組轉換為 .Net**元組**物件，而**ToValueTuple**方法會將 .net**元組**物件轉換成 Visual Basic 的元組。</span><span class="sxs-lookup"><span data-stu-id="b93b2-219">The **ToTuple** method converts a Visual Basic tuple to a .NET **Tuple** object, and the **ToValueTuple** method converts a .NET **Tuple** object to a Visual Basic tuple.</span></span>

<span data-ttu-id="b93b2-220">下列範例會建立元組、將其轉換為 .NET **元組** 物件，並將它轉換回 Visual Basic 的元組。</span><span class="sxs-lookup"><span data-stu-id="b93b2-220">The following example creates a tuple, converts it to a .NET **Tuple** object, and converts it back to a Visual Basic tuple.</span></span> <span data-ttu-id="b93b2-221">然後，此範例會比較這個元組與原始的元組，以確保它們相等。</span><span class="sxs-lookup"><span data-stu-id="b93b2-221">The example then compares this tuple with the original one to ensure that they are equal.</span></span>

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a><span data-ttu-id="b93b2-222">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b93b2-222">See also</span></span>

- [<span data-ttu-id="b93b2-223">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="b93b2-223">Visual Basic Language Reference</span></span>](index.md)
