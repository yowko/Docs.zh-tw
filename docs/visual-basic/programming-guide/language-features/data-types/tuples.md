---
title: 在 Visual Basic 中的 Tuple
ms.date: 04/23/2017
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
ms.openlocfilehash: 146e9c2360cea153d2f487769d5b983516861e8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663293"
---
# <a name="tuples-visual-basic"></a>Tuple (Visual Basic)

從 Visual Basic 2017 開始，Visual Basic 語言提供內建支援，讓 tuple 建立 tuple 和存取的更容易的 tuple 項目。 Tuple 是輕量級資料結構，其中有特定數目和值的序列。 當您具現化的元組時，您可以定義數目和每個值 （或元素） 的資料類型。 例如，2 tuple （或組） 有兩個項目。 第一個可能`Boolean`值，而第二個是`String`。 Tuple 可以方便將多個值儲存在單一物件，通常是當做從方法傳回多個值的輕量方式使用。

> [!IMPORTANT]
> Tuple 支援需要<xref:System.ValueTuple>型別。 如果未安裝.NET Framework 4.7 中，您必須新增 NuGet 套件`System.ValueTuple`，它位在 NuGet 資源庫。 沒有這個套件中，您可能會收到編譯錯誤類似於 「 預先定義類型 'ValueTuple(Of,,,)' 未定義或匯入 」。

## <a name="instantiating-and-using-a-tuple"></a>具現化，並使用 tuple

方法及其逗點分隔值 im 括號括住，您可以初始化 tuple。 每個這些值就會變成 tuple 的欄位。 比方說，下列程式碼會定義三重 （或 3-tuple） 與`Date`做為其第一個值，`String`做為第二個，和`Boolean`為其第三個。

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

根據預設，tuple 中每個欄位的名稱含有字串`Item`以及欄位的 tuple 中以一為位置。 這個的 3 元組，如`Date`欄位是`Item1`，則`String`欄位`Item2`，和`Boolean`欄位是`Item3`。 下列範例顯示的上一行程式碼中具現化的元組欄位的值

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Visual Basic tuple 的欄位會讀取-寫入;tuple 已具現化之後，您可以修改其值。 下列範例會修改兩個 tuple 的前一個範例中所建立的三個欄位，並顯示結果。

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>具現化，並使用具名的 tuple

而不是使用 tuple 欄位的預設名稱，您可以具現化*具名 tuple*藉由將您自己的名稱指派給 tuple 項目。 其指定名稱並可存取 tuple 欄位*或*由其預設名稱。 下列範例在不同之處在於它明確名稱的第一個欄位，具現化相同與之前，3 個 tuple `EventDate`，第二個`Name`，和第三個`IsHoliday`。 然後會顯示欄位值，修改它們，並會再次顯示欄位值。

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a>Tuple 型別推導

從 Visual Basic 15.3 開始，Visual Basic 可以推斷 tuple 項目的名稱;您不必明確指派給他們。 當您初始化 tuple 的一組變數，和您想要的變數名稱相同的元組元素名稱，推斷的元組名稱很有用。 

下列範例會建立`stateInfo`tuple，其中包含三個明確具名項目`state`， `stateName`，和`capital`。 請注意，在命名項目，元組初始化陳述式只會指派具名項目同名的變數的值。

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
項目和變數具有相同名稱，因為 Visual Basic 編譯器可以推斷欄位的名稱，如下列範例所示。

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

若要啟用推斷的元組元素名稱，您必須定義在 Visual Basic 專案中使用 Visual Basic 編譯器的版本 (\*.vbproj) 檔案： 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 
```

版本號碼可以是任何版本的 Visual Basic 編譯器從 15.3 開始。 而不是硬式編碼特定編譯器版本，您也可以指定"Latest"作為值`LangVersion`使用最新版本的系統上安裝的 Visual Basic 編譯器進行編譯。

如需詳細資訊，請參閱 <<c0> [ 設定的 Visual Basic 語言版本](../../../language-reference/configure-language-version.md)。

在某些情況下，Visual Basic 編譯器無法推斷元組元素名稱，從候選項目名稱和元組欄位只能參考使用預設名稱，例如`Item1`，`Item2`等等。它們包括：

- 候選名稱是相同的元組成員名稱，例如`Item3`， `Rest`，或`ToString`。

- 候選名稱重複的 tuple 中。
 
當欄位名稱推斷失敗時，Visual Basic 不會產生編譯器錯誤，也是在執行階段擲回的例外狀況。 相反地，元組欄位，必須以參考其預先定義的名稱，例如`Item1`和`Item2`。 
  
## <a name="tuples-versus-structures"></a>Tuple 與結構

Visual Basic tuple 是實值類型的其中一個執行個體**System.ValueTuple**泛型型別。 例如，`holiday`先前的範例中所定義的 tuple 是的執行個體<xref:System.ValueTuple%603>結構。 它被設計為輕量級容器以取得資料。 Tuple 的目標是要讓您輕鬆建立具有多個資料項目的物件，因為它缺少的一些功能可能會有一個自訂的結構。 它們包括：

- 自訂的成員。 您無法定義自己的屬性、 方法或事件的 tuple。

- 驗證。 您無法驗證指派給欄位的資料。

- 不是變性。 Visual Basic tuple 是可變動的。 相反地，自訂的結構可讓您控制執行個體是否可變動或不可變。

如果自訂成員、 屬性和欄位驗證或不變性是重要的您應該使用 Visual Basic[結構](../../../language-reference/statements/structure-statement.md)陳述式來定義自訂的實值型別。

Visual Basic tuple 沒有繼承的成員及其**ValueTuple**型別。 除了其欄位，包括下列方法：

| 成員 | 描述 |
| ---|---|
| CompareTo | 比較目前的 tuple，另一個具有相同數目的元素的元組。 |
| 等於 | 判斷目前的 tuple 是否等於另一個 tuple 或物件。 |
| GetHashCode | 計算目前的執行個體的雜湊碼。 |
| ToString | 傳回此 tuple，採用下列格式的字串表示法`(Item1, Item2...)`，其中`Item1`和`Item2`代表 tuple 欄位的值。 |

颾魤 ㄛ **ValueTuple**型別會實作<xref:System.Collections.IStructuralComparable>和<xref:System.Collections.IStructuralEquatable>介面，可讓您定義客戶的比較子。

## <a name="assignment-and-tuples"></a>指派和 Tuple

Visual Basic 支援欄位數目相同的元組類型間的指派。 如果下列其中一項為真，則可以轉換的欄位型別：

- 來源和目標的欄位都屬於相同的類型。

- 定義擴展 （或隱含） 轉換成來源型別的目標類型。 

- `Option Strict` 是`On`，並縮小 （或明確） 之來源型別的目標類型定義轉換。 如果來源值超出目標類型的範圍，則這項轉換會擲回例外狀況。

不會考慮對指派進行其他轉換。 讓我們看看 Tuple 類型之間允許的指派類型。

請考慮在下列範例中使用的這些參數：

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

前兩個變數中，`unnamed`和`anonymous`，不會有提供欄位的語意名稱。 欄位名稱都是預設`Item1`和`Item2`。 最後兩個變數中，`named`和`differentName`語意的欄位名稱。 請注意，這兩個 Tuple 有不同的欄位名稱。

所有四個 tuple 都有相同數目的欄位 （稱為 'arity'），而且這些欄位的類型完全相同。 因此，所有這些指派都會運作︰

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

請注意，不會指派 Tuple 的名稱。 依欄位在 Tuple 中的順序，指派欄位的值。

最後，請注意，我們可以將指派`named`tuple `conversion` tuple，即使的第一個欄位`named`是`Integer`，和的第一個欄位`conversion`是`Long`。 此指派會成功，因為轉換`Integer`至`Long`是擴展轉換。

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Tuple 的欄位數目不同則無法指派：

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>Tuple 作為方法傳回值

方法可傳回單一值。 通常，不過，您想要傳回多個值的方法呼叫。 有數種方式可解決這項限制：

- 您可以建立自訂的類別或結構的屬性或欄位代表的方法所傳回的值。 因此是重量級解決方案;它會要求您定義自訂類型，其唯一目的是要擷取的方法呼叫中的值。

- 您可以從方法傳回單一值，並將它們傳遞的參考，這個方法會傳回其餘的值。 這牽涉到變數，而不小心覆寫的傳址方式傳遞的變數值的風險，具現化額外的負荷。

- 您可以使用提供輕量型解決方案，以擷取多個傳回值的元組。

例如， **TryParse**方法在.NET 傳回`Boolean`值，指出是否在剖析作業成功。 在剖析作業的結果會傳回給方法的參考所傳遞的變數中。 一般來說，呼叫剖析方法，例如<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>看起來如下所示：

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

我們可以從剖析的作業傳回 tuple，如果我們將呼叫包裝至<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>我們自己的方法中的方法。 在下列範例中，`NumericLibrary.ParseInteger`呼叫<xref:System.Int32.TryParse%2A?displayProperty=nameWithType>方法，並傳回具有兩個元素的具名元組。 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

然後，您可以呼叫的方法，如下所示的程式碼：

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>Visual Basic 的 tuple 與.NET Framework 中的 tuple

Visual Basic tuple 是其中一個的執行個體**System.ValueTuple**引進.NET Framework 4.7 中的泛型型別。 .NET Framework 也包含一組的泛型**System.Tuple**類別。 這些類別，不過，與 Visual Basic tuple 不同， **System.ValueTuple**數種方式中的泛型類型：

- 項目**Tuple**類別是名為屬性`Item1`， `Item2`，依此類推。 在 Visual Basic 的 tuple 與**ValueTuple**型別，tuple 項目是欄位。

- 您無法將有意義的名稱指派至的項目**Tuple**執行個體或是**ValueTuple**執行個體。 Visual Basic 可讓您指派通訊之欄位的意義的名稱。

- 屬性**Tuple**執行個體是唯讀，是不可變的 tuple。 在 Visual Basic 的 tuple 與**ValueTuple**類型、 元組欄位會讀取寫入; 是可變動的 tuple。

- 泛型**Tuple**型別是參考型別。 使用這些**Tuple**類型表示配置物件。 在最忙碌路徑上，這可能會對您應用程式的效能造成可觀的衝擊。 Visual Basic 的 tuple 與**ValueTuple**類型為實值型別。

中的擴充方法<xref:System.TupleExtensions>類別讓您輕鬆轉換 Visual Basic 的 tuple 與.NET 之間**Tuple**物件。 **ToTuple**方法會將.NET 中的 Visual Basic tuple **Tuple**物件，而**ToValueTuple**方法會將轉換.NET **Tuple**Visual Basic tuple 物件。

下列範例建立的元組，然後將它轉換成.NET **Tuple**物件，並將它回復為 Visual Basic 的元組。 然後這個範例會比較此 tuple 與原始以確保它們相等。

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>另請參閱

- [Visual Basic 語言參考](index.md)
