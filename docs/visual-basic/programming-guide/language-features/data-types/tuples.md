---
title: "在 Visual Basic 中的 Tuple"
ms.custom: 
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be50b22e9acca9ff8cfbde798d78869ee1c72634
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="tuples-visual-basic"></a><span data-ttu-id="1093b-102">Tuple (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1093b-102">Tuples (Visual Basic)</span></span>

<span data-ttu-id="1093b-103">從 Visual Basic 2017 開始，Visual Basic 語言提供了內建的 tuple，可支援建立 tuple 及存取更容易 tuple 的項目。</span><span class="sxs-lookup"><span data-stu-id="1093b-103">Starting with Visual Basic 2017, the Visual Basic language offers built-in support for tuples that makes creating tuples and accessing the elements of tuples easier.</span></span> <span data-ttu-id="1093b-104">Tuple 是輕量的資料結構有特定數目和值的序列。</span><span class="sxs-lookup"><span data-stu-id="1093b-104">A tuple is a light-weight data structure that has a specific number and sequence of values.</span></span> <span data-ttu-id="1093b-105">當您具現化 tuple 時，您可以定義數目和每個值 （或元素） 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="1093b-105">When you instantiate the tuple, you define the number and the data type of each value (or element).</span></span> <span data-ttu-id="1093b-106">例如，2-tuple （或組） 有兩個項目。</span><span class="sxs-lookup"><span data-stu-id="1093b-106">For example, a 2-tuple (or pair) has two elements.</span></span> <span data-ttu-id="1093b-107">第一個可能`Boolean`值，而第二個是`String`。</span><span class="sxs-lookup"><span data-stu-id="1093b-107">The first might be a `Boolean` value, while the second is a `String`.</span></span> <span data-ttu-id="1093b-108">Tuple 可以輕鬆將多個值儲存在單一物件，因為通常用做為從方法傳回多個值的輕量方式。</span><span class="sxs-lookup"><span data-stu-id="1093b-108">Because tuples make it easy to store multiple values in a single object, they are often used as a lightweight way to return multiple values from a method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1093b-109">Tuple 支援需要<xref:System.ValueTuple>型別。</span><span class="sxs-lookup"><span data-stu-id="1093b-109">Tuple support requires the <xref:System.ValueTuple> type.</span></span> <span data-ttu-id="1093b-110">如果未安裝.NET Framework 4.7，您必須先將 NuGet 封裝`System.ValueTuple`，它位在 NuGet Gallery 上。</span><span class="sxs-lookup"><span data-stu-id="1093b-110">If the .NET Framework 4.7 is not installed, you must add the NuGet package `System.ValueTuple`, which is available on the NuGet Gallery.</span></span> <span data-ttu-id="1093b-111">沒有這個套件，您可能會收到編譯錯誤類似於 「 預先定義型別 'ValueTuple(Of,,,)' 未定義或匯入 」。</span><span class="sxs-lookup"><span data-stu-id="1093b-111">Without this package, you may get a compilation error similar to, "Predefined type 'ValueTuple(Of,,,)' is not defined or imported."</span></span>

## <a name="instantiating-and-using-a-tuple"></a><span data-ttu-id="1093b-112">具現化及使用 tuple</span><span class="sxs-lookup"><span data-stu-id="1093b-112">Instantiating and using a tuple</span></span>

<span data-ttu-id="1093b-113">您只要將它以逗號分隔值的 im 括號初始化 tuple。</span><span class="sxs-lookup"><span data-stu-id="1093b-113">You instantiate a tuple by enclosing its comma-delimited values im parentheses.</span></span> <span data-ttu-id="1093b-114">每個這些值就會變成 tuple 的欄位。</span><span class="sxs-lookup"><span data-stu-id="1093b-114">Each of those values then becomes a field of the tuple.</span></span> <span data-ttu-id="1093b-115">比方說，下列程式碼會定義三重 （或 3 tuple） 與`Date`做為其第一個值，`String`做為第二個，而`Boolean`做為其第三個。</span><span class="sxs-lookup"><span data-stu-id="1093b-115">For example, the following code defines a triple (or 3-tuple) with a `Date` as its first value, a `String` as its second, and a `Boolean` as its third.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

<span data-ttu-id="1093b-116">根據預設，tuple 中每個欄位的名稱包含字串的`Item`以及 tuple 中的欄位 1 為基底位置。</span><span class="sxs-lookup"><span data-stu-id="1093b-116">By default, the name of each field in a tuple consists of the string `Item` along with the field's one-based position in the tuple.</span></span> <span data-ttu-id="1093b-117">針對此 3-tuple`Date`欄位是`Item1`、`String`欄位是`Item2`，而`Boolean`欄位是`Item3`。</span><span class="sxs-lookup"><span data-stu-id="1093b-117">For this 3-tuple, the `Date` field is `Item1`, the `String` field is `Item2`, and the `Boolean` field is `Item3`.</span></span> <span data-ttu-id="1093b-118">下列範例顯示的 tuple 上一行的程式碼中具現化欄位的值</span><span class="sxs-lookup"><span data-stu-id="1093b-118">The following example displays the values of fields of the tuple instantiated in the previous line of code</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

<span data-ttu-id="1093b-119">Visual Basic tuple 的欄位會讀取寫入;tuple 已具現化之後，您可以修改它的值。</span><span class="sxs-lookup"><span data-stu-id="1093b-119">The fields of a Visual Basic tuple are read-write; after you've instantiated a tuple, you can modify its values.</span></span> <span data-ttu-id="1093b-120">下列範例會修改兩個 tuple 上一個範例中所建立的三個欄位，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="1093b-120">The following example modifies two of the three fields of the tuple created in the previous example and displays the result.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a><span data-ttu-id="1093b-121">具現化及使用具名的 tuple</span><span class="sxs-lookup"><span data-stu-id="1093b-121">Instantiating and using a named tuple</span></span>

<span data-ttu-id="1093b-122">而不是使用 tuple 欄位的預設名稱，您可以具現化*名為 tuple*藉由 tuple 的項目來指定您自己的名稱。</span><span class="sxs-lookup"><span data-stu-id="1093b-122">Rather than using default names for a tuple's fields, you can instantiate a *named tuple* by assigning your own names to the tuple's elements.</span></span> <span data-ttu-id="1093b-123">然後可以指派的名稱來存取的 tuple 欄位*或*藉由其預設名稱。</span><span class="sxs-lookup"><span data-stu-id="1093b-123">The tuple's fields can then be accessed by their assigned names *or* by their default names.</span></span> <span data-ttu-id="1093b-124">下列範例在不同之處在於它明確命名的第一個欄位，具現化相同以前，做為 3 個 tuple `EventDate`，第二個`Name`，第三個`IsHoliday`。</span><span class="sxs-lookup"><span data-stu-id="1093b-124">The following example instantiates the same 3-tuple as previously, except that it explicitly names the first field `EventDate`, the second `Name`, and the third `IsHoliday`.</span></span> <span data-ttu-id="1093b-125">然後顯示欄位值，修改它們，並再次顯示欄位值。</span><span class="sxs-lookup"><span data-stu-id="1093b-125">It then displays the field values, modifies them, and displays the field values again.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="tuples-versus-structures"></a><span data-ttu-id="1093b-126">Tuple 與結構</span><span class="sxs-lookup"><span data-stu-id="1093b-126">Tuples versus structures</span></span>

<span data-ttu-id="1093b-127">Visual Basic tuple 都是實值類型的其中一個執行個體**System.ValueTuple**泛型型別。</span><span class="sxs-lookup"><span data-stu-id="1093b-127">A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types.</span></span> <span data-ttu-id="1093b-128">例如，`holiday`前一個範例中所定義的 tuple 都是執行個體<xref:System.ValueTuple%603>結構。</span><span class="sxs-lookup"><span data-stu-id="1093b-128">For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure.</span></span> <span data-ttu-id="1093b-129">它被設計為資料的輕量型容器。</span><span class="sxs-lookup"><span data-stu-id="1093b-129">It is designed to be a lightweight container for data.</span></span> <span data-ttu-id="1093b-130">Tuple 旨在讓您輕鬆建立具有多個資料項目的物件，因為其欠缺的一些功能可能會有自訂的結構。</span><span class="sxs-lookup"><span data-stu-id="1093b-130">Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have.</span></span> <span data-ttu-id="1093b-131">這些活動包括：</span><span class="sxs-lookup"><span data-stu-id="1093b-131">These include:</span></span>

- <span data-ttu-id="1093b-132">客戶成員。</span><span class="sxs-lookup"><span data-stu-id="1093b-132">Customer members.</span></span> <span data-ttu-id="1093b-133">您無法定義自己的屬性、 方法或事件的 tuple。</span><span class="sxs-lookup"><span data-stu-id="1093b-133">You cannot define your own properties, methods, or events for a tuple.</span></span>

- <span data-ttu-id="1093b-134">驗證。</span><span class="sxs-lookup"><span data-stu-id="1093b-134">Validation.</span></span> <span data-ttu-id="1093b-135">您無法驗證指派給欄位的資料。</span><span class="sxs-lookup"><span data-stu-id="1093b-135">You cannot validate the data assigned to fields.</span></span>

- <span data-ttu-id="1093b-136">不變性。</span><span class="sxs-lookup"><span data-stu-id="1093b-136">Immutability.</span></span> <span data-ttu-id="1093b-137">Visual Basic tuple 是可變動的。</span><span class="sxs-lookup"><span data-stu-id="1093b-137">Visual Basic tuples are mutable.</span></span> <span data-ttu-id="1093b-138">相反地，自訂結構可讓您控制執行個體是否處於可變動或不變。</span><span class="sxs-lookup"><span data-stu-id="1093b-138">In contrast, a custom structure allows you to control whether an instance is mutable or immutable.</span></span>

<span data-ttu-id="1093b-139">自訂成員、 屬性和欄位驗證或不變性來說很重要，您應該使用 Visual Basic[結構](../../../language-reference/statements/structure-statement.md)陳述式來定義自訂值型別。</span><span class="sxs-lookup"><span data-stu-id="1093b-139">If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.</span></span>

<span data-ttu-id="1093b-140">Visual Basic tuple 沒有繼承的成員及其**ValueTuple**型別。</span><span class="sxs-lookup"><span data-stu-id="1093b-140">A Visual Basic tuple does inherit the members of its **ValueTuple** type.</span></span> <span data-ttu-id="1093b-141">除了其欄位，這些需求包括下列方法：</span><span class="sxs-lookup"><span data-stu-id="1093b-141">In addition to its fields, these include the following methods:</span></span>

| <span data-ttu-id="1093b-142">成員</span><span class="sxs-lookup"><span data-stu-id="1093b-142">Member</span></span> | <span data-ttu-id="1093b-143">說明</span><span class="sxs-lookup"><span data-stu-id="1093b-143">Description</span></span> |
| ---|---|
| <span data-ttu-id="1093b-144">CompareTo</span><span class="sxs-lookup"><span data-stu-id="1093b-144">CompareTo</span></span> | <span data-ttu-id="1093b-145">比較目前的 tuple，至另一個 tuple 有相同數目的項目。</span><span class="sxs-lookup"><span data-stu-id="1093b-145">Compares the current tuple to another tuple with the same number of elements.</span></span> |
| <span data-ttu-id="1093b-146">等於</span><span class="sxs-lookup"><span data-stu-id="1093b-146">Equals</span></span> | <span data-ttu-id="1093b-147">判斷目前的 tuple 是否等於另一個 tuple 或物件。</span><span class="sxs-lookup"><span data-stu-id="1093b-147">Determines whether the current tuple is equal to another tuple or object.</span></span> |
| <span data-ttu-id="1093b-148">GetHashCode</span><span class="sxs-lookup"><span data-stu-id="1093b-148">GetHashCode</span></span> | <span data-ttu-id="1093b-149">計算目前的執行個體的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="1093b-149">Calculates the hash code for the current instance.</span></span> |
| <span data-ttu-id="1093b-150">ToString</span><span class="sxs-lookup"><span data-stu-id="1093b-150">ToString</span></span> | <span data-ttu-id="1093b-151">傳回 tuple，其格式的字串表示`(Item1, Item2...)`，其中`Item1`和`Item2`代表 tuple 的欄位的值。</span><span class="sxs-lookup"><span data-stu-id="1093b-151">Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields.</span></span> |

<span data-ttu-id="1093b-152">此外， **ValueTuple**型別會實作<xref:System.Collections.IStructuralComparable>和<xref:System.Collections.IStructuralEquatable>介面，讓您定義客戶比較子。</span><span class="sxs-lookup"><span data-stu-id="1093b-152">In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define customer comparers.</span></span>

## <a name="assignment-and-tuples"></a><span data-ttu-id="1093b-153">指派和 Tuple</span><span class="sxs-lookup"><span data-stu-id="1093b-153">Assignment and tuples</span></span>

<span data-ttu-id="1093b-154">Visual Basic 支援 tuple 類型有相同數目的欄位之間的指派。</span><span class="sxs-lookup"><span data-stu-id="1093b-154">Visual Basic supports assignment between tuple types that have the same number of fields.</span></span> <span data-ttu-id="1093b-155">如果下列其中一項為 true，則可以轉換的欄位型別：</span><span class="sxs-lookup"><span data-stu-id="1093b-155">The field types can be converted if one of the following is true:</span></span>

- <span data-ttu-id="1093b-156">來源和目標欄位屬於相同類型。</span><span class="sxs-lookup"><span data-stu-id="1093b-156">The source and target field are of the same type.</span></span>

- <span data-ttu-id="1093b-157">擴展 （或隱含） 的來源類型轉換成目標類型被定義。</span><span class="sxs-lookup"><span data-stu-id="1093b-157">A widening (or implicit) conversion of the source type to the target type is defined.</span></span> 

- <span data-ttu-id="1093b-158">`Option Strict`是`On`，和縮小 （或明確） 的來源類型轉換成目標類型定義。</span><span class="sxs-lookup"><span data-stu-id="1093b-158">`Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined.</span></span> <span data-ttu-id="1093b-159">如果來源值是目標類型的範圍之外，這項轉換可以擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1093b-159">This conversion can throw an exception if the source value is outside the range of the target type.</span></span>

<span data-ttu-id="1093b-160">不會考慮對指派進行其他轉換。</span><span class="sxs-lookup"><span data-stu-id="1093b-160">Other conversions are not considered for assignments.</span></span> <span data-ttu-id="1093b-161">讓我們看看 Tuple 類型之間允許的指派類型。</span><span class="sxs-lookup"><span data-stu-id="1093b-161">Let's look at the kinds of assignments that are allowed between tuple types.</span></span>

<span data-ttu-id="1093b-162">請考慮在下列範例中使用的這些參數：</span><span class="sxs-lookup"><span data-stu-id="1093b-162">Consider these variables used in the following examples:</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

<span data-ttu-id="1093b-163">前兩個變數，`unnamed`和`anonymous`，不會有語意提供欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="1093b-163">The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields.</span></span> <span data-ttu-id="1093b-164">欄位名稱都是預設值`Item1`和`Item2`。</span><span class="sxs-lookup"><span data-stu-id="1093b-164">Their field names are the default `Item1` and `Item2`.</span></span> <span data-ttu-id="1093b-165">最後兩個變數，`named`和`differentName`語意的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="1093b-165">The last two variables, `named` and `differentName` have semantic field names.</span></span> <span data-ttu-id="1093b-166">請注意，這兩個 Tuple 有不同的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="1093b-166">Note that these two tuples have different names for the fields.</span></span>

<span data-ttu-id="1093b-167">所有的這些 tuple 的四個有相同數目的欄位 （稱為 'arity'），與這些欄位類型完全相同。</span><span class="sxs-lookup"><span data-stu-id="1093b-167">All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical.</span></span> <span data-ttu-id="1093b-168">因此，所有這些指派都會運作︰</span><span class="sxs-lookup"><span data-stu-id="1093b-168">Therefore, all of these assignments work:</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

<span data-ttu-id="1093b-169">請注意，不會指派 Tuple 的名稱。</span><span class="sxs-lookup"><span data-stu-id="1093b-169">Notice that the names of the tuples are not assigned.</span></span> <span data-ttu-id="1093b-170">依欄位在 Tuple 中的順序，指派欄位的值。</span><span class="sxs-lookup"><span data-stu-id="1093b-170">The values of the fields are assigned following the order of the fields in the tuple.</span></span>

<span data-ttu-id="1093b-171">最後，請注意，我們可以將指派`named`tuple `conversion` tuple，即使的第一個欄位`named`是`Integer`，並將第一個欄位的`conversion`是`Long`。</span><span class="sxs-lookup"><span data-stu-id="1093b-171">Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`.</span></span> <span data-ttu-id="1093b-172">此指派會成功，因為轉換`Integer`至`Long`擴展轉換。</span><span class="sxs-lookup"><span data-stu-id="1093b-172">This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.</span></span>

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

<span data-ttu-id="1093b-173">Tuple 不同數目的欄位不可以指派：</span><span class="sxs-lookup"><span data-stu-id="1093b-173">Tuples with different numbers of fields are not assignable:</span></span>

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a><span data-ttu-id="1093b-174">Tuple 作為方法傳回值</span><span class="sxs-lookup"><span data-stu-id="1093b-174">Tuples as method return values</span></span>

<span data-ttu-id="1093b-175">方法可以傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="1093b-175">A method can return only a single value.</span></span> <span data-ttu-id="1093b-176">通常，不過，您會希望方法呼叫傳回多個值。</span><span class="sxs-lookup"><span data-stu-id="1093b-176">Frequently, though, you'd like a method call to return multiple values.</span></span> <span data-ttu-id="1093b-177">有數種方式來解決這項限制：</span><span class="sxs-lookup"><span data-stu-id="1093b-177">There are several ways to work around this limitation:</span></span>

- <span data-ttu-id="1093b-178">您可以建立自訂類別或結構的屬性或欄位代表的方法所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="1093b-178">You can create a custom class or structure whose properties or fields represent values returned by the method.</span></span> <span data-ttu-id="1093b-179">因此是重量型的解決方案。它會要求您定義自訂類型，其唯一目的是要從方法呼叫中擷取值。</span><span class="sxs-lookup"><span data-stu-id="1093b-179">Thus is a heavyweight solution; it requires that you define a custom type whose only purpose is to retrieve values from a method call.</span></span>

- <span data-ttu-id="1093b-180">您可以從方法傳回單一值，並將其餘的值傳回的參考，這個方法以傳送它們。</span><span class="sxs-lookup"><span data-stu-id="1093b-180">You can return a single value from the method, and return the remaining values by passing them by reference to the method.</span></span> <span data-ttu-id="1093b-181">這牽涉到變數和不小心覆寫的傳址方式傳遞的變數值的風險，具現化的額外的負荷。</span><span class="sxs-lookup"><span data-stu-id="1093b-181">This involves the overhead of instantiating a variable and risks inadvertently overwriting the value of the variable that you pass by reference.</span></span>

- <span data-ttu-id="1093b-182">您可以使用 tuple，提供要擷取多個傳回值的輕量型方案。</span><span class="sxs-lookup"><span data-stu-id="1093b-182">You can use a tuple, which provides a lightweight solution to retrieving multiple return values.</span></span>

<span data-ttu-id="1093b-183">例如， **TryParse**方法在.NET 傳回`Boolean`值，指出是否在剖析作業成功。</span><span class="sxs-lookup"><span data-stu-id="1093b-183">For example, the **TryParse** methods in .NET return a `Boolean` value that indicates whether the parsing operation succeeded.</span></span> <span data-ttu-id="1093b-184">在剖析作業的結果會傳回給方法的參考所傳遞的變數中。</span><span class="sxs-lookup"><span data-stu-id="1093b-184">The result of the parsing operation is returned in a variable passed by reference to the method.</span></span> <span data-ttu-id="1093b-185">一般來說，呼叫剖析方法時，例如<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>看起來像下面這樣：</span><span class="sxs-lookup"><span data-stu-id="1093b-185">Normally, a call to the a parsing method such as <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> looks like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

<span data-ttu-id="1093b-186">我們可以從在剖析作業傳回 tuple，如果我們將呼叫包裝至<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>我們自己的方法中的方法。</span><span class="sxs-lookup"><span data-stu-id="1093b-186">We can return a tuple from the parsing operation if we wrap the call to the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method in our own method.</span></span> <span data-ttu-id="1093b-187">在下列範例中，`NumericLibrary.ParseInteger`呼叫<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>方法，並傳回具有兩個元素的具名的 tuple。</span><span class="sxs-lookup"><span data-stu-id="1093b-187">In the following example, `NumericLibrary.ParseInteger` calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method and returns a named tuple with two elements.</span></span> 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

<span data-ttu-id="1093b-188">然後，您可以呼叫具有類似下列的程式碼的方法：</span><span class="sxs-lookup"><span data-stu-id="1093b-188">You can then call the method with code like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a><span data-ttu-id="1093b-189">Visual Basic 的 tuple 與.NET Framework 中</span><span class="sxs-lookup"><span data-stu-id="1093b-189">Visual Basic tuples and tuples in the .NET Framework</span></span>

<span data-ttu-id="1093b-190">Visual Basic tuple 是其中一個的執行個體**System.ValueTuple** .NET Framework 4.7 中導入的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="1093b-190">A Visual Basic tuple is an instance of one of the **System.ValueTuple** generic types, which were introduced in the .NET Framework 4.7.</span></span> <span data-ttu-id="1093b-191">.NET Framework 也會包含一組的泛型**System.Tuple**類別。</span><span class="sxs-lookup"><span data-stu-id="1093b-191">The .NET Framework also includes a set of generic **System.Tuple** classes.</span></span> <span data-ttu-id="1093b-192">這些類別，不過，與 Visual Basic tuple 不同而**System.ValueTuple**數種方式中的泛型類型：</span><span class="sxs-lookup"><span data-stu-id="1093b-192">These classes, however, differ from Visual Basic tuples and the **System.ValueTuple** generic types in a number of ways:</span></span>

- <span data-ttu-id="1093b-193">項目**Tuple**類別是名為屬性`Item1`， `Item2`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="1093b-193">The elements of the **Tuple** classes are properties named `Item1`, `Item2`, and so on.</span></span> <span data-ttu-id="1093b-194">在 Visual Basic tuple 和**ValueTuple**型別，tuple 項目是欄位。</span><span class="sxs-lookup"><span data-stu-id="1093b-194">In Visual Basic tuples and the **ValueTuple** types, tuple elements are fields.</span></span>

- <span data-ttu-id="1093b-195">您無法指派有意義的名稱的項目**Tuple**執行個體或**ValueTuple**執行個體。</span><span class="sxs-lookup"><span data-stu-id="1093b-195">You cannot assign meaningful names to the elements of a **Tuple** instance or of a **ValueTuple** instance.</span></span> <span data-ttu-id="1093b-196">Visual Basic 可讓您指定的通訊之欄位的意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="1093b-196">Visual Basic allows you to assign names that communicate the meaning of the fields.</span></span>

- <span data-ttu-id="1093b-197">內容**Tuple**執行個體是唯讀，則是不變的 tuple。</span><span class="sxs-lookup"><span data-stu-id="1093b-197">The properties of a **Tuple** instance are read-only; the tuples are immutable.</span></span> <span data-ttu-id="1093b-198">在 Visual Basic tuple 和**ValueTuple**型別，tuple 欄位是讀寫，則是可變動的 tuple。</span><span class="sxs-lookup"><span data-stu-id="1093b-198">In Visual Basic tuples and the **ValueTuple** types, tuple fields are read-write; the tuples are mutable.</span></span>

- <span data-ttu-id="1093b-199">泛型**Tuple**類型是參考型別。</span><span class="sxs-lookup"><span data-stu-id="1093b-199">The generic **Tuple** types are reference types.</span></span> <span data-ttu-id="1093b-200">使用這些**Tuple**類型配置物件的方法。</span><span class="sxs-lookup"><span data-stu-id="1093b-200">Using these **Tuple** types means allocating objects.</span></span> <span data-ttu-id="1093b-201">在最忙碌路徑上，這可能會對您應用程式的效能造成可觀的衝擊。</span><span class="sxs-lookup"><span data-stu-id="1093b-201">On hot paths, this can have a measurable impact on your application's performance.</span></span> <span data-ttu-id="1093b-202">Visual Basic tuple 和**ValueTuple**類型為實值類型。</span><span class="sxs-lookup"><span data-stu-id="1093b-202">Visual Basic tuples and the **ValueTuple** types are value types.</span></span>

<span data-ttu-id="1093b-203">中的擴充方法<xref:System.TupleExtensions>類別讓您輕鬆 tuple Visual Basic 和.NET 之間進行轉換**Tuple**物件。</span><span class="sxs-lookup"><span data-stu-id="1093b-203">Extension methods in the <xref:System.TupleExtensions> class make it easy to convert between Visual Basic tuples and .NET **Tuple** objects.</span></span> <span data-ttu-id="1093b-204">**ToTuple**方法會將 Visual Basic tuple 轉換至.NET **Tuple**物件，而**ToValueTuple**方法會將轉換.NET **Tuple**Visual Basic tuple 物件。</span><span class="sxs-lookup"><span data-stu-id="1093b-204">The **ToTuple** method converts a Visual Basic tuple to a .NET **Tuple** object, and the **ToValueTuple** method converts a .NET **Tuple** object to a Visual Basic tuple.</span></span>

<span data-ttu-id="1093b-205">下列範例會建立 tuple、 將它轉換成.NET **Tuple**物件，並將它回到 Visual Basic tuple。</span><span class="sxs-lookup"><span data-stu-id="1093b-205">The following example creates a tuple, converts it to a .NET **Tuple** object, and converts it back to a Visual Basic tuple.</span></span> <span data-ttu-id="1093b-206">然後這個範例會比較此 tuple 與原始以確保它們相等。</span><span class="sxs-lookup"><span data-stu-id="1093b-206">The example then compares this tuple with the original one to ensure that they are equal.</span></span>

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a><span data-ttu-id="1093b-207">請參閱</span><span class="sxs-lookup"><span data-stu-id="1093b-207">See also</span></span>

[<span data-ttu-id="1093b-208">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="1093b-208">Visual Basic Language Reference</span></span>](index.md)  
