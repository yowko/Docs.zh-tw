---
title: 'C # 主要語言區域教學課程'
description: 第一次接觸 C#？ 了解該語言的基本概念。
ms.date: 08/06/2020
ms.openlocfilehash: e1e533982757c10085f0444197ff97ee7487391f
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414899"
---
# <a name="major-language-areas"></a>主要語言區域

## <a name="arrays-collections-and-linq"></a>陣列、集合和 LINQ

C # 和 .NET 提供許多不同的集合類型。 陣列具有由語言定義的語法。 泛型集合類型會列在 <xref:System.Collections.Generic?displayProperty=fullName> 命名空間中。 特製化集合包含用 <xref:System.Span%601?displayProperty=nameWithType> 來存取堆疊框架上的連續記憶體，以及 <xref:System.Memory%601?displayProperty=nameWithType> 存取 managed 堆積上的連續記憶體。 所有集合（包括陣列） <xref:System.Span%601> 和都會 <xref:System.Memory%601> 共用反覆運算的統一原則。 您可以使用此 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 介面。 這個統一的原則表示任何集合類型都可以搭配 LINQ 查詢或其他演算法使用。 您可以使用撰寫方法 <xref:System.Collections.Generic.IEnumerable%601> ，而這些演算法會搭配任何集合使用。

### <a name="arrays"></a>陣列

[***陣列***](../programming-guide/arrays/index.md)是一種資料結構，其中包含透過計算索引所存取的一些變數。 陣列中包含的變數（也稱為陣列的 ***元素*** ）全都是相同的類型。 此類型稱為陣列的 ***元素類型*** 。

陣列型別是參考型別，而陣列變數的宣告只是預留空間給陣列執行個體的參考。 實際的陣列實例會在執行時間使用運算子動態建立 `new` 。 作業 `new` 會指定新陣列實例的 ***長度*** ，然後針對實例的存留期進行修正。 陣列元素的索引範圍在 `0` 到 `Length - 1` 之間。 `new` 運算子會自動將陣列的元素初始化為其預設值，例如，針對所有數值型別，此值為零，而針對所有參考型別，此值為 `null`。

下列範例會建立 `int` 元素的陣列、初始化陣列，並印出陣列的內容。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="ArraysSample":::

這個範例會建立並操作***一維陣列***。 C# 也支援***多維陣列***。 一個陣列型別的維度數目 (亦稱為陣列型別的***順位***)，是寫入陣列型別的方括弧之間的逗號數目加一。 下列範例會分別配置一個單維、一個二維和一個三維陣列。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="DeclareArrays":::

`a1` 陣列包含 10 個元素、`a2`陣列包含 50 (10 × 5) 個元素，`a3` 陣列包含 100 (10 × 5 × 2) 個元素。
陣列的元素型別可以是任一型別，包括陣列型別。 陣列類型元素的陣列有時稱為 ***不規則陣列*** ，因為元素陣列的長度不一定相同。 下列範例會配置一個 `int` 型別的陣列：

:::code language="csharp" source="./snippets/shared/Features.cs" ID="ArrayOfArrays":::

第一行建立包含三個元素的陣列，每個元素的型別均為 `int[]`，每個元素的初始值均為 `null`。 接下來的幾行則會初始化具有不同長度之個別陣列實例參考的三個元素。

`new`運算子允許使用***陣列初始化***運算式來指定陣列元素的初始值，也就是在分隔符號和之間寫入的運算式清單 `{` `}` 。 下列範例使用三個元素配置並初始化 `int[]`。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="InitializeArray":::

陣列的長度是從和之間的運算式數目推斷而來 `{` `}` 。 區域變數和欄位宣告可以進一步縮短，因此不需要先重新開機陣列型別。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="InitializeShortened":::

上述兩個範例都相當於下列程式碼：

:::code language="csharp" source="./snippets/shared/Features.cs" ID="InitializeGenerated":::

`foreach`語句可以用來列舉任何集合的元素。 下列程式碼會列舉上述範例中的陣列：

:::code language="csharp" source="./snippets/shared/Features.cs" ID="EnumerateArray":::

`foreach`語句 <xref:System.Collections.Generic.IEnumerable%601> 會使用介面，因此可以使用任何集合。

## <a name="string-interpolation"></a>字串插補

C # [***字串插補***](../language-reference/tokens/interpolated.md) 可讓您藉由定義將結果放置在格式字串中的運算式，來格式化字串。 例如，下列範例會從一組氣象資料列印指定日期的溫度：

:::code language="csharp" source="./snippets/shared/Features.cs" ID="StringInterpolation":::

插入字串是使用 token 來宣告 `$` 。 字串插補會評估和之間的運算式 `{` `}` ，然後將結果轉換成 `string` ，並將括弧之間的文字取代為運算式的字串結果。 `:`第一個運算式中的會 `{weatherData.Date:MM-DD-YYYY}` 指定*格式字串*。 在上述範例中，它會指定應以 "MM-yyyy-mm-dd" 格式列印日期。

## <a name="pattern-matching"></a>模式比對

C # 語言提供 [***模式***](../pattern-matching.md) 比對運算式來查詢物件的狀態，並根據該狀態執行程式碼。 您可以檢查屬性和欄位的類型和值，以判斷要採取的動作。 `switch`運算式是適用于模式比對的主要運算式。

## <a name="delegates-and-lambda-expressions"></a>委派和 lambda 運算式

[***委派型***](../delegates-overview.md)別代表具有特定參數清單和傳回型別之方法的參考。 委派讓您可將方法視為實體，而實體能指派給變數或當作參數來傳遞。 委派類似于某些其他語言中的函式指標概念。 與函式指標不同的是，委派是物件導向且型別安全的。

下列範例會宣告並使用名為 `Function` 的委派型別。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="DelegateExample":::

`Function` 委派型別的執行個體可以參考任何採用 `double` 引數並傳回 `double` 值的方法。 `Apply`方法會將指定的套用 `Function` 至的元素 `double[]` ，並傳回 `double[]` 包含結果的。 在 `Main` 方法中，是使用 `Apply` 將三個不同的函式套用到 `double[]`。

委派可以參考靜態方法 (例如上一個範例中的 `Square` 或 `Math.Sin`)，或是參考執行個體方法 (例如上一個範例中的 `m.Multiply`)。 參考執行個體方法的委派也會參考特定的物件，而且透過委派來叫用執行個體方法時，該物件就會變成叫用中的 `this`。

您也可以使用匿名函式（宣告時所建立的「內嵌方法」）來建立委派。 匿名函式可以看見周圍方法的區域變數。 下列範例不會建立類別：

:::code language="csharp" source="./snippets/shared/Features.cs" ID="UseDelegate":::

委派不知道或在意它所參考之方法的類別。 重點是，參考的方法與委派具有相同的參數和傳回型別。

## <a name="async--await"></a>async/await

C # 支援具有兩個關鍵字的非同步程式： `async` 和 `await` 。 您將修飾詞加入 `async` 至方法宣告，以宣告方法是非同步。 `await`運算子會指示編譯器以非同步方式等待結果完成。 控制權會傳回給呼叫端，而此方法會傳回結構來管理非同步工作的狀態。 結構通常是 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> ，但可以是任何支援 awaiter 模式的型別。 這些功能可讓您撰寫程式碼，以讀取為其同步對應，但以非同步方式執行。 例如，下列程式碼會下載 [Microsoft](https://docs.microsoft.com)檔的首頁：

:::code language="csharp" source="./snippets/shared/Features.cs" ID="AsyncExample":::

此小範例顯示非同步程式設計的主要功能：

- 方法宣告包含修飾詞 `async` 。
- 方法的主體傳回 `await` `GetByteArrayAsync` 方法。
- 語句中指定的型別 `return` 與方法的宣告中的型別引數相符 `Task<T>` 。  (傳回的方法 `Task` 會使用 `return` 沒有任何引數) 的語句。

## <a name="attributes"></a>屬性

C# 程式中的型別、成員和其他實體支援控制其某方面行為的修飾詞。 例如，方法的協助工具是使用 `public`、`protected`、`internal` 和 `private` 修飾詞控制。 C# 將此能力一般化，宣告式資訊的使用者定義型別才能附加至程式實體，並在執行階段擷取。 程式會藉由定義和使用 [***屬性***](../programming-guide/concepts/attributes/index.md)來指定此額外的宣告式資訊。

下列範例宣告的 `HelpAttribute` 屬性可置於程式實體，以提供其相關文件的連結。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="DefineAttribute":::

所有屬性類別都是衍生自 <xref:System.Attribute> .net 程式庫所提供的基類。 在相關聯的宣告之前，於方括弧中提供屬性的名稱 (及任何引數) 即可套用屬性。 如果屬性名稱的結尾是 `Attribute`，則參考該屬性時可以省略該部分名稱。 例如，`HelpAttribute` 可以下列方式使用。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="UseAttributes":::

這個範例會將 `HelpAttribute` 附加至 `Widget` 類別。 它會在類別的 `Display` 方法中加入另一個 `HelpAttribute`。 屬性類別的公用建構函式控制將屬性附加至程式實體時必須提供的資訊。 透過參考屬性類別的公用讀寫屬性可提供其他資訊 (例如先前對 `Topic` 的參考 )。

由屬性定義的中繼資料可在執行階段使用反射來讀取及操控。 使用此技巧要求特定的屬性時，會以程式來源中提供的資訊叫用屬性類別的建構函式，並傳回產生的屬性執行個體。 如果是透過屬性提供其他資訊，傳回屬性執行個體之前，這些屬性會設為指定的值。

下列程式碼範例示範如何取得與 `Widget` 類別關聯的 `HelpAttribute` 執行個體與其 `Display` 方法。

:::code language="csharp" source="./snippets/shared/Features.cs" ID="ReadAttributes":::

## <a name="learn-more"></a>深入了解

您可以試用我們的其中一個 [教學](../tutorials/index.md)課程，以深入瞭解 c #。

>[!div class="step-by-step"]
>[[上一步]](program-building-blocks.md)
