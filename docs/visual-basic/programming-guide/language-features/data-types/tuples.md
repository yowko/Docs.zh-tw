---
title: "在 Visual Basic 中的 Tuple"
ms.custom: 
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2653b9dc8a6ecbcb718c20be8bd6275edf4cfb6e
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="tuples-visual-basic"></a>Tuple (Visual Basic)

從 Visual Basic 2017 開始，Visual Basic 語言提供了內建的 tuple，可支援建立 tuple 及存取更容易 tuple 的項目。 Tuple 是輕量的資料結構有特定數目和值的序列。 當您具現化 tuple 時，您可以定義數目和每個值 （或元素） 的資料類型。 例如，2-tuple （或組） 有兩個項目。 第一個可能`Boolean`值，而第二個是`String`。 Tuple 可以輕鬆將多個值儲存在單一物件，因為通常用做為從方法傳回多個值的輕量方式。

> [!IMPORTANT]
> Tuple 支援需要<xref:System.ValueTuple>型別。 如果未安裝.NET Framework 4.7，您必須先將 NuGet 封裝`System.ValueTuple`，它位在 NuGet Gallery 上。 沒有這個套件，您可能會收到編譯錯誤類似於 「 預先定義型別 'ValueTuple(Of,,,)' 未定義或匯入 」。

## <a name="instantiating-and-using-a-tuple"></a>具現化及使用 tuple

您只要將它以逗號分隔值的 im 括號初始化 tuple。 每個這些值就會變成 tuple 的欄位。 比方說，下列程式碼會定義三重 （或 3 tuple） 與`Date`做為其第一個值，`String`做為第二個，而`Boolean`做為其第三個。

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

根據預設，tuple 中每個欄位的名稱包含字串的`Item`以及 tuple 中的欄位 1 為基底位置。 針對此 3-tuple`Date`欄位是`Item1`、`String`欄位是`Item2`，而`Boolean`欄位是`Item3`。 下列範例顯示的 tuple 上一行的程式碼中具現化欄位的值

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Visual Basic tuple 的欄位會讀取寫入;tuple 已具現化之後，您可以修改它的值。 下列範例會修改兩個 tuple 上一個範例中所建立的三個欄位，並顯示結果。

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>具現化及使用具名的 tuple

而不是使用 tuple 欄位的預設名稱，您可以具現化*名為 tuple*藉由 tuple 的項目來指定您自己的名稱。 然後可以指派的名稱來存取的 tuple 欄位*或*藉由其預設名稱。 下列範例在不同之處在於它明確命名的第一個欄位，具現化相同以前，做為 3 個 tuple `EventDate`，第二個`Name`，第三個`IsHoliday`。 然後顯示欄位值，修改它們，並再次顯示欄位值。

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a>推斷的 tuple 項目名稱

從 Visual Basic 15.3 開始，Visual Basic 可推斷 tuple 項目; 的名稱您沒有明確指派給它們。 初始化變數，一組 tuple，而且您想要做為變數的名稱相同的 tuple 項目名稱時，推斷的 tuple 名稱很有用。 

下列範例會建立`stateInfo`tuple，其中包含三個明確的具名項目， `state`， `stateName`，和`capital`。 請注意，在中命名項目，tuple 的初始化陳述式只會指派具名項目同名的變數的值。

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
項目和變數具有相同的名稱，因為 Visual Basic 編譯器可以推斷出欄位的名稱，如下列範例所示。

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

若要啟用 interred 的 tuple 項目名稱，您必須定義要在 Visual Basic 專案中使用 Visual Basic 編譯器的版本 (\*.vbproj) 檔案： 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 

The version number can be any version of the Visual Basic compiler starting with 15.3. Rather than hard-coding a specific compiler version, you can also specify "Latest" as the value of `LangVersion` to compile with the most recent version of the Visual Basic compiler installed on your system.

In some cases, the Visual Basic compiler cannot infer the tuple element name from the candidate name, and the tuple field can only be referenced using its default name, such as `Item1`, `Item2`, etc. These include:

- The candidate name is the same as the name of a tuple member, such as `Item3`, `Rest`, or `ToString`.

- The candidate name is duplicated in the tuple.
 
When field name inference fails, Visual Basic does not generate a compiler error, nor is an exception thrown at runtime. Instead, tuple fields must be referenced by their predefined names, such as `Item1` and `Item2`. 
  
## Tuples versus structures

A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types. For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure. It is designed to be a lightweight container for data. Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have. These include:

- Customer members. You cannot define your own properties, methods, or events for a tuple.

- Validation. You cannot validate the data assigned to fields.

- Immutability. Visual Basic tuples are mutable. In contrast, a custom structure allows you to control whether an instance is mutable or immutable.

If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.

A Visual Basic tuple does inherit the members of its **ValueTuple** type. In addition to its fields, these include the following methods:

| Member | Description |
| ---|---|
| CompareTo | Compares the current tuple to another tuple with the same number of elements. |
| Equals | Determines whether the current tuple is equal to another tuple or object. |
| GetHashCode | Calculates the hash code for the current instance. |
| ToString | Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields. |

In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define customer comparers.

## Assignment and tuples

Visual Basic supports assignment between tuple types that have the same number of fields. The field types can be converted if one of the following is true:

- The source and target field are of the same type.

- A widening (or implicit) conversion of the source type to the target type is defined. 

- `Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined. This conversion can throw an exception if the source value is outside the range of the target type.

Other conversions are not considered for assignments. Let's look at the kinds of assignments that are allowed between tuple types.

Consider these variables used in the following examples:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields. Their field names are the default `Item1` and `Item2`. The last two variables, `named` and `differentName` have semantic field names. Note that these two tuples have different names for the fields.

All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical. Therefore, all of these assignments work:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Notice that the names of the tuples are not assigned. The values of the fields are assigned following the order of the fields in the tuple.

Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`. This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Tuples with different numbers of fields are not assignable:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>Tuple 作為方法傳回值

方法可以傳回單一值。 通常，不過，您會希望方法呼叫傳回多個值。 有數種方式來解決這項限制：

- 您可以建立自訂類別或結構的屬性或欄位代表的方法所傳回的值。 因此是重量型的解決方案。它會要求您定義自訂類型，其唯一目的是要從方法呼叫中擷取值。

- 您可以從方法傳回單一值，並將其餘的值傳回的參考，這個方法以傳送它們。 這牽涉到變數和不小心覆寫的傳址方式傳遞的變數值的風險，具現化的額外的負荷。

- 您可以使用 tuple，提供要擷取多個傳回值的輕量型方案。

例如， **TryParse**方法在.NET 傳回`Boolean`值，指出是否在剖析作業成功。 在剖析作業的結果會傳回給方法的參考所傳遞的變數中。 一般來說，呼叫剖析方法時，例如<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>看起來像下面這樣：

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

我們可以從在剖析作業傳回 tuple，如果我們將呼叫包裝至<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>我們自己的方法中的方法。 在下列範例中，`NumericLibrary.ParseInteger`呼叫<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>方法，並傳回具有兩個元素的具名的 tuple。 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

然後，您可以呼叫具有類似下列的程式碼的方法：

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>Visual Basic 的 tuple 與.NET Framework 中

Visual Basic tuple 是其中一個的執行個體**System.ValueTuple** .NET Framework 4.7 中導入的泛型型別。 .NET Framework 也會包含一組的泛型**System.Tuple**類別。 這些類別，不過，與 Visual Basic tuple 不同而**System.ValueTuple**數種方式中的泛型類型：

- 項目**Tuple**類別是名為屬性`Item1`， `Item2`，依此類推。 在 Visual Basic tuple 和**ValueTuple**型別，tuple 項目是欄位。

- 您無法指派有意義的名稱的項目**Tuple**執行個體或**ValueTuple**執行個體。 Visual Basic 可讓您指定的通訊之欄位的意義的名稱。

- 內容**Tuple**執行個體是唯讀，則是不變的 tuple。 在 Visual Basic tuple 和**ValueTuple**型別，tuple 欄位是讀寫，則是可變動的 tuple。

- 泛型**Tuple**類型是參考型別。 使用這些**Tuple**類型配置物件的方法。 在最忙碌路徑上，這可能會對您應用程式的效能造成可觀的衝擊。 Visual Basic tuple 和**ValueTuple**類型為實值類型。

中的擴充方法<xref:System.TupleExtensions>類別讓您輕鬆 tuple Visual Basic 和.NET 之間進行轉換**Tuple**物件。 **ToTuple**方法會將 Visual Basic tuple 轉換至.NET **Tuple**物件，而**ToValueTuple**方法會將轉換.NET **Tuple**Visual Basic tuple 物件。

下列範例會建立 tuple、 將它轉換成.NET **Tuple**物件，並將它回到 Visual Basic tuple。 然後這個範例會比較此 tuple 與原始以確保它們相等。

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>另請參閱

[Visual Basic 語言參考](index.md)  
