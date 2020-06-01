---
title: 擴充方法 - C# 程式設計手冊
ms.date: 03/19/2020
helpviewer_keywords:
- methods [C#], adding to existing types
- extension methods [C#]
- methods [C#], extension
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
ms.openlocfilehash: 5db2797870b6c2e1998f17f1d8e4df8aa3f95c9e
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241405"
---
# <a name="extension-methods-c-programming-guide"></a>擴充方法 (C# 程式設計手冊)

擴充方法可讓您在現有類型中「加入」方法，而不需要建立新的衍生類型、重新編譯，或是修改原始類型。 擴充方法是靜態方法，但它們的呼叫方式就如同擴充類型上的實例方法一樣。 對於以 c #、F # 和 Visual Basic 撰寫的用戶端程式代碼，呼叫擴充方法與在類型中定義的方法之間沒有明顯的差異。

最常見的擴充方法是 LINQ 標準查詢運算子，可將查詢功能加入至現有的 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 和 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 類型。 若要使用標準查詢運算子，請先使用 `using System.Linq` 指示詞將它們帶入範圍內。 接著，任何實作 <xref:System.Collections.Generic.IEnumerable%601> 的類型都會具有執行個體方法，如 <xref:System.Linq.Enumerable.GroupBy%2A>、<xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.Average%2A> 等。 如果在 <xref:System.Collections.Generic.IEnumerable%601> 類型 (如 <xref:System.Collections.Generic.List%601> 或 <xref:System.Array>) 的執行個體後面輸入「點」，就可以在 IntelliSense 陳述式完成時看到這些額外的方法。

### <a name="orderby-example"></a>OrderBy 範例

下列範例將示範如何在整數陣列上呼叫標準查詢運算子 `OrderBy` 方法。 括號括住的運算式就是 Lambda 運算式。 許多標準查詢運算子會採用 lambda 運算式做為參數，但這不是擴充方法的需求。 如需詳細資訊，請參閱[Lambda 運算式](../statements-expressions-operators/lambda-expressions.md)。

[!code-csharp[csProgGuideExtensionMethods#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#3)]

擴充方法會定義為靜態方法，但透過執行個體方法語法呼叫。 其第一個參數會指定方法操作的類型。 參數的前面會加上[this](../../language-reference/keywords/this.md)修飾詞。 您必須使用 `using` 指示詞將命名空間明確匯入至原始程式碼，擴充方法才會進入範圍中。

下列範例將示範針對 <xref:System.String?displayProperty=nameWithType> 類別定義的擴充方法。 它是在非嵌套的非泛型靜態類別中定義的：

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

您可以使用實例方法語法，在程式碼中叫用擴充方法。 編譯器所產生的中繼語言（IL）會將您的程式碼轉譯為靜態方法的呼叫。 封裝的原則並不是真的違反了。 擴充方法無法存取所擴充之類型中的私用變數。

如需詳細資訊，請參閱[如何執行和呼叫自訂擴充方法](./how-to-implement-and-call-a-custom-extension-method.md)。

一般來說，您可能會呼叫擴充方法，而不是執行自己的程式。 因為擴充方法是使用執行個體方法語法進行呼叫，所以不需要任何特殊知識就可以從用戶端程式碼使用它們。 若要啟用特定類型的擴充方法，只要針對定義這些方法所在的命名空間加入 `using` 指示詞即可。 例如，若要使用標準查詢運算子，請將下面這個 `using` 指示詞加入至程式碼：

```csharp
using System.Linq;
```

（您可能也必須新增對 system.string 的參考）。您會注意到，標準查詢運算子現在會出現在 IntelliSense 中，做為大部分類型可用的其他方法 <xref:System.Collections.Generic.IEnumerable%601> 。

## <a name="binding-extension-methods-at-compile-time"></a>在編譯時期繫結擴充方法

您可以使用擴充方法來擴充類別或介面，但無法覆寫它們。 而且永遠不會呼叫擁有與介面或類別方法相同名稱和簽章的擴充方法。 在編譯時期，擴充方法的優先順序一律低於類型本身中定義的執行個體方法。 換句話說，如果類型具有名為 `Process(int i)` 的方法，而您的擴充方法也具有相同的簽章，則編譯器一律會繫結至執行個體方法。 編譯器遇到方法引動過程時，會先在類型的執行個體方法中尋找相符項目。 如果找不到相符項目，則會搜尋任何針對該類型定義的擴充方法，並繫結至找到的第一個擴充方法。 下列範例將示範編譯器如何判斷要繫結的擴充方法或執行個體方法。

## <a name="example"></a>範例

下列範例將示範 C# 編譯器遵循的規則，用以判斷要將方法呼叫繫結至類型上的執行個體方法，還是繫結至擴充方法。 靜態類別 `Extensions` 包含針對任何實作 `IMyInterface` 之類型定義的擴充方法。 類別 `A`、`B` 和 `C` 都會實作這個介面。

因為 `MethodB` 擴充方法的名稱和簽章與這些類別已實作的方法完全相同，所以絕不會呼叫該方法。

當編譯器找不到具有相符簽章的實例方法時，它會系結至相符的擴充方法（如果有的話）。

[!code-csharp[csProgGuideExtensionMethods#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#5)]

## <a name="common-usage-patterns"></a>常見使用模式

### <a name="collection-functionality"></a>集合功能

在過去，通常會建立「集合類別」，為指定的型別實作為 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 介面，並針對該型別的集合採取動作。 雖然建立這種類型的集合物件沒有任何問題，但使用上的延伸模組也可以達到相同的功能 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 。 延伸模組的優點是允許從任何集合（例如 <xref:System.Array?displayProperty=nameWithType> <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 在該類型上執行的或）呼叫功能。 如需使用 Int32 陣列的範例，請參閱本文稍[早](#orderby-example)的。

### <a name="layer-specific-functionality"></a>圖層特有的功能

使用繪圖紙架構或其他分層應用程式設計時，通常會有一組可用於跨應用程式界限進行通訊的領域實體或資料傳輸物件。 這些物件通常不包含任何功能，或僅適用于應用程式所有層級的最低功能。 擴充方法可用來新增每個應用層特有的功能，而不需使用不需要或不想要在其他圖層中的方法將物件載入。

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

### <a name="extending-predefined-types"></a>擴充預先定義的類型

我們通常可以擴充現有的類型，例如 .NET 或 CLR 類型，而不是在需要建立可重複使用的功能時建立新的物件。 例如，如果我們不使用擴充方法，我們可能會建立 `Engine` 或 `Query` 類別來執行在程式碼中多個位置呼叫的 SQL Server 上執行查詢的工作。 不過，我們可以改為 <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> 使用擴充方法來擴充類別，以從已連接到 SQL Server 的任何地方執行該查詢。 其他範例可能是在類別中加入一般功能 <xref:System.String?displayProperty=nameWithType> 、擴充和物件的資料處理功能， <xref:System.IO.File?displayProperty=nameWithType> <xref:System.IO.Stream?displayProperty=nameWithType> 以及 <xref:System.Exception?displayProperty=nameWithType> 特定錯誤處理功能的物件。 這些類型的使用案例只受到您的想像和良好的限制。

延伸預先定義的類型可能會很棘手， `struct` 因為它們是以傳值方式傳遞至方法。 這表示結構的任何變更都會對結構的複本進行。 延伸方法結束後，就不會顯示這些變更。 從 c # 7.2 開始，您可以將 `ref` 修飾詞加入至擴充方法的第一個引數。 新增 `ref` 修飾詞表示第一個引數是以傳址方式傳遞。 這可讓您撰寫擴充方法，以變更所擴充之結構的狀態。

## <a name="general-guidelines"></a>一般準則

雖然它仍然被視為偏好藉由修改物件的程式碼來加入功能，或在合理的情況下衍生新的型別，但擴充方法已成為在整個 .NET 生態系統中建立可重複使用之功能的重要選項。 當原始來源不在您的控制之下、衍生物件不適當或不可能時，或不應在其適用範圍外公開功能時，您可以選擇擴充方法。

如需衍生類型的詳細資訊，請參閱[繼承](./inheritance.md)。

當使用擴充方法來擴充無法控制其原始程式碼的型別時，您會執行風險，讓型別的執行變更會導致擴充方法中斷。

如果您要實作所指定類型的擴充方法，請記住下列幾點：

- 如果擴充方法的簽章與類型中定義的方法相同，則絕不會呼叫擴充方法。
- 擴充方法是帶入命名空間層級的範圍。 例如，如果您在名為的單一命名空間中有多個包含擴充方法的靜態類別，則指示詞會將 `Extensions` 它們全部納入範圍中 `using Extensions;` 。

針對實作的類別庫，您不應該使用擴充方法阻止組件的版本號碼遞增。 如果您想要在您擁有原始程式碼的程式庫中新增重要功能，請遵循元件版本控制的 .NET 指導方針。 如需詳細資訊，請參閱[組件版本控制](../../../standard/assembly/versioning.md)。

## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [平行程式設計範例 (包括許多範例擴充方法)](/samples/browse/?products=dotnet-core%2Cdotnet-standard&term=parallel)
- [Lambda 運算式](../statements-expressions-operators/lambda-expressions.md)
- [標準查詢運算子概觀](../concepts/linq/standard-query-operators-overview.md)
- [Conversion rules for Instance parameters and their impact](https://docs.microsoft.com/archive/blogs/sreekarc/conversion-rules-for-instance-parameters-and-their-impact) (執行個體參數的轉換規則與其影響)
- [Extension methods Interoperability between languages](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-interoperability-between-languages) (語言之間擴充方法的互通性)
- [Extension methods and Curried Delegates](https://docs.microsoft.com/archive/blogs/sreekarc/extension-methods-and-curried-delegates) (擴充方法和局部調用委派)
- [Extension method Binding and Error reporting](https://docs.microsoft.com/archive/blogs/sreekarc/extension-method-binding-and-error-reporting) (擴充方法繫結和錯誤報告)
