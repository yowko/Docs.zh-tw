---
title: 擴充方法 - C# 程式設計手冊
ms.date: 03/19/2020
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: 0b35ad523fc7f0949cb5243edbdc50cd3e927999
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249216"
---
# <a name="extension-methods-c-programming-guide"></a>擴充方法 (C# 程式設計手冊)

擴充方法可讓您在現有類型中「加入」方法，而不需要建立新的衍生類型、重新編譯，或是修改原始類型。 擴充方法是靜態方法，但調用它們就像擴展類型的實例一樣。 對於用 C#、F# 和 Visual Basic 編寫的用戶端代碼，調用擴充方法與類型中定義的方法之間沒有明顯區別。

最常見的擴充方法是 LINQ 標準查詢運算子，它們將查詢功能添加到現有<xref:System.Collections.IEnumerable?displayProperty=nameWithType>和<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>類型。 若要使用標準查詢運算子，請先使用 `using System.Linq` 指示詞將它們帶入範圍內。 接著，任何實作 <xref:System.Collections.Generic.IEnumerable%601> 的類型都會具有執行個體方法，如 <xref:System.Linq.Enumerable.GroupBy%2A>、<xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.Average%2A> 等。 如果在 <xref:System.Collections.Generic.IEnumerable%601> 類型 (如 <xref:System.Collections.Generic.List%601> 或 <xref:System.Array>) 的執行個體後面輸入「點」，就可以在 IntelliSense 陳述式完成時看到這些額外的方法。

### <a name="orderby-example"></a>按訂單按示例

下列範例將示範如何在整數陣列上呼叫標準查詢運算子 `OrderBy` 方法。 括號括住的運算式就是 Lambda 運算式。 許多標準查詢運算子將 lambda 運算式作為參數，但這不是擴充方法的要求。 有關詳細資訊，請參閱[Lambda 運算式](../statements-expressions-operators/lambda-expressions.md)。

[!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]

擴充方法會定義為靜態方法，但透過執行個體方法語法呼叫。 他們的第一個參數指定該方法對哪個類型進行操作。 參數前面有[此](../../language-reference/keywords/this.md)修飾符。 您必須使用 `using` 指示詞將命名空間明確匯入至原始程式碼，擴充方法才會進入範圍中。

下列範例將示範針對 <xref:System.String?displayProperty=nameWithType> 類別定義的擴充方法。 它在非嵌套的非泛型靜態類中定義：

[!code-csharp[csProgGuideExtensionMethods#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#4)]

使用這個 `WordCount` 指示詞就可以將 `using` 擴充方法帶入範圍中：

```csharp
using ExtensionMethods;
```

而使用下列語法，就可以從應用程式中呼叫它：

```csharp
string s = "Hello Extension Methods";
int i = s.WordCount();
```

使用實例方法語法調用代碼中的擴充方法。 編譯器生成的中間語言 （IL） 將代碼轉換為靜態方法上的調用。 封裝原則並沒有真正受到違反。 擴充方法無法訪問它們正在擴展的類型中的私有變數。

有關詳細資訊，請參閱[如何實現和調用自訂擴充方法](./how-to-implement-and-call-a-custom-extension-method.md)。

通常，調用擴充方法的頻率可能遠遠高於實現自己的擴充方法。 因為擴充方法是使用執行個體方法語法進行呼叫，所以不需要任何特殊知識就可以從用戶端程式碼使用它們。 若要啟用特定類型的擴充方法，只要針對定義這些方法所在的命名空間加入 `using` 指示詞即可。 例如，若要使用標準查詢運算子，請將下面這個 `using` 指示詞加入至程式碼：

```csharp
using System.Linq;
```

（您可能還必須添加對 System.Core.dll 的引用。您會注意到，標準查詢運算子現在顯示為適用于大多數<xref:System.Collections.Generic.IEnumerable%601>類型的其他方法。

## <a name="binding-extension-methods-at-compile-time"></a>在編譯時期繫結擴充方法

您可以使用擴充方法來擴充類別或介面，但無法覆寫它們。 而且永遠不會呼叫擁有與介面或類別方法相同名稱和簽章的擴充方法。 在編譯時期，擴充方法的優先順序一律低於類型本身中定義的執行個體方法。 換句話說，如果類型具有名為 `Process(int i)` 的方法，而您的擴充方法也具有相同的簽章，則編譯器一律會繫結至執行個體方法。 編譯器遇到方法引動過程時，會先在類型的執行個體方法中尋找相符項目。 如果找不到相符項目，則會搜尋任何針對該類型定義的擴充方法，並繫結至找到的第一個擴充方法。 下列範例將示範編譯器如何判斷要繫結的擴充方法或執行個體方法。

## <a name="example"></a>範例

下列範例將示範 C# 編譯器遵循的規則，用以判斷要將方法呼叫繫結至類型上的執行個體方法，還是繫結至擴充方法。 靜態類別 `Extensions` 包含針對任何實作 `IMyInterface` 之類型定義的擴充方法。 類別 `A`、`B` 和 `C` 都會實作這個介面。

因為 `MethodB` 擴充方法的名稱和簽章與這些類別已實作的方法完全相同，所以絕不會呼叫該方法。

當編譯器找不到具有匹配簽名的實例方法時，如果存在，它將綁定到匹配的擴充方法。

[!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]

## <a name="common-usage-patterns"></a>常見使用模式

### <a name="collection-functionality"></a>集合功能

過去，通常創建"集合類"，這些類實現了給定類型的<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>介面，並包含對該類型的集合執行操作的功能。 雖然創建這種類型的集合物件沒有錯，但使用 上的擴展可以實現相同的功能<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 擴展的優點是允許從任何集合（如 或<xref:System.Array?displayProperty=nameWithType><xref:System.Collections.Generic.List%601?displayProperty=nameWithType>在該類型上實現）<xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>調用功能。 [本文前面](#orderby-example)可以找到使用 Int32 陣列的示例。

### <a name="layer-specific-functionality"></a>特定于圖層的功能

使用洋蔥體系結構或其他分層應用程式設計時，通常有一組可用於跨應用程式邊界通信的域實體或資料傳輸物件。 這些物件通常不包含任何功能，也僅包含適用于應用程式所有層的最小功能。 擴充方法可用於添加特定于每個應用程式層的功能，而無需使用其他層中不需要或不需要的方法將物件載入下來。

```aspx-csharp
public class DomainEntity
{
    public int Id { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }
}

static class DomainEntityExtensions
{
    static string FullName(this DomainEntity value)
        => $"{value.FirstName} {value.LastName}";
}
```

### <a name="extending-predefined-types"></a>擴展預定義類型

在需要創建可重用功能時，我們通常可以擴展現有類型（如 .NET Framework 或 CLR 類型），而不是在需要創建可重用功能時創建新物件。 例如，如果我們不使用擴充方法，我們可能會創建一個`Engine`或`Query`類來執行在 SQL Server 上執行查詢的工作，該查詢可能從代碼中的多個位置調用。 但是，<xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType>我們可以使用擴充方法擴展類，從連接到 SQL Server 的任何位置執行該查詢。 其他示例可能是<xref:System.String?displayProperty=nameWithType>向類添加通用功能、擴展<xref:System.IO.File?displayProperty=nameWithType>和<xref:System.IO.Stream?displayProperty=nameWithType>物件的資料處理功能以及<xref:System.Exception?displayProperty=nameWithType>特定錯誤處理功能的物件。 這些類型的用例僅受您的想像力和良好感覺的限制。

擴展預定義類型在類型中`struct`可能很困難，因為它們通過值傳遞給方法。 這意味著對結構的任何更改都對結構的副本進行了更改。 擴充方法退出後，這些更改將不可見。 從 C# 7.2 開始，可以將`ref`修改器添加到擴充方法的第一個參數中。 添加`ref`修改符表示第一個參數通過引用傳遞。 這使您能夠編寫更改擴展結構狀態的擴充方法。

## <a name="general-guidelines"></a>一般準則

雖然仍然認為最好通過修改物件的代碼或在合理和可能時派生新類型來添加功能，但擴充方法已成為在整個 .NET 中創建可重用功能的關鍵選項生態。 對於原始源不在您控制範圍內、派生物件不恰當或不可能或功能不應超出其適用範圍的情況，擴充方法是一個絕佳的選擇。

有關派生類型的詳細資訊，請參閱[繼承](./inheritance.md)。

當使用擴充方法擴展原始程式碼無法控制的類型時，您會運行類型實現中的更改會導致擴充方法中斷的風險。

如果您要實作所指定類型的擴充方法，請記住下列幾點：

- 如果擴充方法的簽章與類型中定義的方法相同，則絕不會呼叫擴充方法。
- 擴充方法是帶入命名空間層級的範圍。 例如，如果多個靜態類在名為 的`Extensions`單個命名空間中包含擴充方法，則`using Extensions;`指令將所有這些類都引入作用域。

針對實作的類別庫，您不應該使用擴充方法阻止組件的版本號碼遞增。 如果您要在擁有其原始程式碼的程式庫中加入重要功能，則應遵循組件版本控制的標準 .NET Framework 方針。 如需詳細資訊，請參閱[組件版本控制](../../../standard/assembly/versioning.md)。

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [平行程式設計範例 (包括許多範例擴充方法)](https://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)
- [蘭姆達運算式](../statements-expressions-operators/lambda-expressions.md)
- [標準查詢運算子概觀](../concepts/linq/standard-query-operators-overview.md)
- [Conversion rules for Instance parameters and their impact](https://docs.microsoft.com/archive/blogs/sreekarc/conversion-rules-for-instance-parameters-and-their-impact) (執行個體參數的轉換規則與其影響)
- [Extension methods Interoperability between languages](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-interoperability-between-languages) (語言之間擴充方法的互通性)
- [Extension methods and Curried Delegates](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-and-curried-delegates) (擴充方法和局部調用委派)
- [Extension method Binding and Error reporting](https://docs.microsoft.com/archive/blogs/sreekarc/extension-method-binding-and-error-reporting) (擴充方法繫結和錯誤報告)
