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

## <a name="tuples-versus-structures"></a>Tuple 與結構

Visual Basic tuple 都是實值類型的其中一個執行個體**System.ValueTuple**泛型型別。 例如，`holiday`前一個範例中所定義的 tuple 都是執行個體<xref:System.ValueTuple%603>結構。 它被設計為資料的輕量型容器。 Tuple 旨在讓您輕鬆建立具有多個資料項目的物件，因為其欠缺的一些功能可能會有自訂的結構。 這些活動包括：

- 客戶成員。 您無法定義自己的屬性、 方法或事件的 tuple。

- 驗證。 您無法驗證指派給欄位的資料。

- 不變性。 Visual Basic tuple 是可變動的。 相反地，自訂結構可讓您控制執行個體是否處於可變動或不變。

自訂成員、 屬性和欄位驗證或不變性來說很重要，您應該使用 Visual Basic[結構](../../../language-reference/statements/structure-statement.md)陳述式來定義自訂值型別。

Visual Basic tuple 沒有繼承的成員及其**ValueTuple**型別。 除了其欄位，這些需求包括下列方法：

| 成員 | 說明 |
| ---|---|
| CompareTo | 比較目前的 tuple，至另一個 tuple 有相同數目的項目。 |
| 等於 | 判斷目前的 tuple 是否等於另一個 tuple 或物件。 |
| GetHashCode | 計算目前的執行個體的雜湊碼。 |
| ToString | 傳回 tuple，其格式的字串表示`(Item1, Item2...)`，其中`Item1`和`Item2`代表 tuple 的欄位的值。 |

此外， **ValueTuple**型別會實作<xref:System.Collections.IStructuralComparable>和<xref:System.Collections.IStructuralEquatable>介面，讓您定義客戶比較子。

## <a name="assignment-and-tuples"></a>指派和 Tuple

Visual Basic 支援 tuple 類型有相同數目的欄位之間的指派。 如果下列其中一項為 true，則可以轉換的欄位型別：

- 來源和目標欄位屬於相同類型。

- 擴展 （或隱含） 的來源類型轉換成目標類型被定義。 

- `Option Strict`是`On`，和縮小 （或明確） 的來源類型轉換成目標類型定義。 如果來源值是目標類型的範圍之外，這項轉換可以擲回例外狀況。

不會考慮對指派進行其他轉換。 讓我們看看 Tuple 類型之間允許的指派類型。

請考慮在下列範例中使用的這些參數：

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

前兩個變數，`unnamed`和`anonymous`，不會有語意提供欄位的名稱。 欄位名稱都是預設值`Item1`和`Item2`。 最後兩個變數，`named`和`differentName`語意的欄位名稱。 請注意，這兩個 Tuple 有不同的欄位名稱。

所有的這些 tuple 的四個有相同數目的欄位 （稱為 'arity'），與這些欄位類型完全相同。 因此，所有這些指派都會運作︰

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

請注意，不會指派 Tuple 的名稱。 依欄位在 Tuple 中的順序，指派欄位的值。

最後，請注意，我們可以將指派`named`tuple `conversion` tuple，即使的第一個欄位`named`是`Integer`，並將第一個欄位的`conversion`是`Long`。 此指派會成功，因為轉換`Integer`至`Long`擴展轉換。

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Tuple 不同數目的欄位不可以指派：

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

## <a name="see-also"></a>請參閱

[Visual Basic 語言參考](index.md)  
