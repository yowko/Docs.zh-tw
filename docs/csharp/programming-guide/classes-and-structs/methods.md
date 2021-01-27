---
title: 方法 - C# 程式設計手冊
description: 'C # 中的方法是包含一連串語句的程式碼區塊。 程式會藉由呼叫方法並指定引數來執行語句。'
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: 879e57cfbce82f1aa77f8810e23d6a61a6ea5bc8
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899447"
---
# <a name="methods-c-programming-guide"></a>方法 (C# 程式設計手冊)

方法是包含一系列陳述式的程式碼區塊。 程式會造成呼叫方法並指定任何所需的方法引數來執行陳述式。 在 C# 中，每個執行的指示是在方法的內容中執行。 `Main`方法是每個 c # 應用程式的進入點，並會在程式啟動時由 common language runtime (CLR) 呼叫。

> [!NOTE]
> 本文討論命名方法。 如需匿名函式的資訊，請參閱[匿名函式](../statements-expressions-operators/anonymous-functions.md)。

## <a name="method-signatures"></a>方法簽章

方法是在 [類別](../../language-reference/keywords/class.md)、 [結構](../../language-reference/builtin-types/struct.md)或 [介面](../interfaces/index.md) 中宣告，方法是指定存取層級（例如 `public` 或 `private` ）、選擇性修飾詞（例如或）、傳回 `abstract` `sealed` 值、方法的名稱，以及任何方法參數。 這些部份放在一起即為方法的簽章。

> [!IMPORTANT]
> 方法的傳回類型不是方法多載用途的方法簽章的一部分。 不過，在判斷委派與所指向的方法之間的相容性時，它是方法簽章的一部分。

方法參數會放在括號中，並以逗號分隔。 空括號表示方法不需要任何參數。 這個類別包含四個方法：

[!code-csharp[DifferentModifiersOnMethods#1](snippets/methods/Program.cs#1)]

## <a name="method-access"></a>方法存取

在物件上呼叫方法，就像是存取欄位。 在物件名稱後面加上句點、方法的名稱與括號。 引數會在括號中列出，並以逗號分隔。 因此可以如下列範例所示呼叫 `Motorcycle` 類別的方法：

[!code-csharp[CallingMethods#2](snippets/methods/Program.cs#2)]

## <a name="method-parameters-vs-arguments"></a>方法參數與引數

方法定義會指定所需的任何參數的名稱和類型。 在呼叫程式碼呼叫此方法時，它會提供對每個參數呼叫的引數的具體值。 引數必須與參數類型相容，但如果呼叫程式碼中使用的任何) 不需要與方法中所定義的參數相同，則引數名稱 (。 例如：

[!code-csharp[MethodExamples#3](snippets/methods/Program.cs#3)]

## <a name="passing-by-reference-vs-passing-by-value"></a>以傳址方式傳遞與以傳值方式傳遞

根據預設，當實 [值型](../../language-reference/builtin-types/value-types.md) 別的實例傳遞給方法時，會傳遞其複本，而不是實例本身。 因此，對引數所做的變更不會影響呼叫方法中的原始實例。 若要以傳址方式傳遞實數值型別的實例，請使用 `ref` 關鍵字。 如需詳細資訊，請參閱[傳遞實值型別參數](./passing-value-type-parameters.md)。

傳遞參考類型的物件至方法時，會傳遞物件的參考。 也就是說，此方法接收的不是物件本身，而是指出物件位置的引數。 如果您使用此參考變更物件的成員，變更會反映在呼叫方法的引數中，即使以傳值方式傳遞物件。

您可以使用關鍵字來建立參考型別 `class` ，如下列範例所示：

[!code-csharp[SampleRefTypeClass#4](snippets/methods/Program.cs#4)]

現在，如果您將此類型為基礎的物件傳遞至方法，即會傳遞物件的參考。 下列範例會將型別的物件傳遞 `SampleRefType` 給方法 `ModifyObject` ：

[!code-csharp[PassingAReferenceType#5](snippets/methods/Program.cs#5)]

此範例會執行與上一個範例基本上相同的動作，依傳值方式將引數傳遞至方法。 但是，由於使用參考類型，結果會不同。 `ModifyObject` 中對參數 `value` 的 `obj`欄位做的修改，也會變更 `value` 方法中引數 `rt`的 `TestRefType` 欄位。 `TestRefType` 方法會顯示 33 做為輸出。

如需如何依傳址和依傳值方式來傳遞參考型別的詳細資訊，請參閱[傳遞參考型別參數](./passing-reference-type-parameters.md)和[參考型別](../../language-reference/keywords/reference-types.md)。

## <a name="return-values"></a>傳回值

方法可以傳回值給呼叫者。 針對傳回類型，如果列在方法名稱前面的類型不是 `void`，方法可以使用 `return` 關鍵字傳回值。 具有 `return` 關鍵字後面接著符合傳回類型值的陳述式，會將該值傳回給方法呼叫者。

可以透過傳值方式將值傳回給呼叫者，或者，從 C# 7.0 開始，是[以傳址方式](ref-returns.md)。 如果 `ref` 關鍵字用於方法簽章中，並且接在每個 `return` 關鍵字後面，則會以傳址方式將值傳回給呼叫者。 例如，下列方法簽章和傳回陳述式指出方法以傳址方式將變數名稱 `estDistance` 傳回給呼叫者。

```csharp
public ref double GetEstimatedDistance()
{
    return ref estDistance;
}
```

`return` 關鍵字也會停止執行方法。 如果傳回類型為 `void`，不含值的 `return` 陳述式對於停止方法的執行仍很有用。 若沒有 `return` 關鍵字，在方法到達程式碼區塊的結尾時，方法將會停止執行。 具有非 void 傳回類型的方法需要使用 `return` 關鍵字以傳回值。 例如，這兩種方法使用 `return` 關鍵字傳回整數：

[!code-csharp[SimpleMathClass#6](snippets/methods/Program.cs#6)]

若要使用從方法傳回的值，呼叫方法可以在使用相同類型值的任意位置使用方法呼叫本身即已足夠。 您也可以指派傳回值給變數。 例如，下列兩個程式碼範例會達到相同的目標：

[!code-csharp[SquareANumberWithAddTwoNumbersUsingLocalVariable#7](snippets/methods/Program.cs#7)]

[!code-csharp[SquareANumberWithAddTwoNumbersInTheSameLine#8](snippets/methods/Program.cs#8)]

使用區域變數，在此情況下的 `result`來儲存值是選擇性的。 它有助於程式碼的可讀性，或如果您需要儲存方法的整個範圍引數的原始值，則可能為必要。

若要從方法使用以傳址方式傳回的值，則在您想要修改 [ref 區域變數](ref-returns.md#ref-locals)的值時必須宣告該變數。 例如，如果 `Planet.GetEstimatedDistance` 方法以傳址方式傳回 <xref:System.Double> 值，您可以使用下列這類程式碼將它定義為 ref 區域變數：

```csharp
ref int distance = plant
```

如果呼叫函式已將陣列傳入 `M`，則不需要從修改陣列內容的 `M` 方法傳回多維度陣列。  您可能會從 `M` 針對值的良好樣式或功能流程傳回產生的陣列，但這不需要，因為 C# 會以傳值方式傳遞所有參考型別，而且陣列參考的值是陣列的指標。 在方法中 `M` ，任何具有陣列參考的程式碼都可以觀察陣列內容的任何變更，如下列範例所示：

```csharp
static void Main(string[] args)
{
    int[,] matrix = new int[2, 2];
    FillMatrix(matrix);
    // matrix is now full of -1
}

public static void FillMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            matrix[i, j] = -1;
        }
    }
}
```

如需詳細資訊，請參閱 [return](../../language-reference/keywords/return.md)。

## <a name="async-methods"></a>非同步方法

使用非同步功能，您就可以呼叫非同步方法，而不需要使用明確回呼或手動將您的程式碼分散到多種方法或 lambda 運算式上。

如果您使用 [async](../../language-reference/keywords/async.md) 修飾詞來標示方法，可以在方法中使用 [await](../../language-reference/operators/await.md) 運算子。 當控制項到達 async 方法的 await 運算式時，控制項會傳回給呼叫者，方法中的進度會暫停，直到等候的工作完成。 當工作完成時，方法中的執行可以繼續。

> [!NOTE]
> 非同步方法會在遇到第一個尚未完成的等候物件，或到達非同步方法的結尾（以先發生者為准）時，傳回給呼叫端。

非同步方法的傳回類型可以是 <xref:System.Threading.Tasks.Task%601>、 <xref:System.Threading.Tasks.Task>或 void。 void 傳回類型主要用於定義需要 void 傳回類型的事件處理常式。 傳回 void 類型的非同步方法無法等候，而且 void 傳回方法的呼叫者無法攔截方法擲回的例外狀況。

在下列範例中， `DelayAsync` 是會傳回類型 <xref:System.Threading.Tasks.Task%601>的非同步方法。 `DelayAsync` 具有傳回整數的 `return` 陳述式。 因此 `DelayAsync` 的方法宣告必須具有傳回類型 `Task<int>`。 因為傳回類型是 `Task<int>`， `await` 中 `DoSomethingAsync` 運算式的評估會產生整數，如下列陳述式所示範： `int result = await delayTask`。

`Main`方法是具有傳回類型的非同步方法的範例 <xref:System.Threading.Tasks.Task> 。 它會移至 `DoSomethingAsync` 方法，因為它是以單一行表示，它可以省略 `async` 和 `await` 關鍵字。 因為 `DoSomethingAsync` 是非同步方法，對 `DoSomethingAsync` 的呼叫工作必須等候，如下列陳述式所示： `await DoSomethingAsync();`。

:::code language="csharp" source="snippets/classes-and-structs/methods/Program.cs":::

非同步方法不可以宣告任何 [ref](../../language-reference/keywords/ref.md) 或 [out](../../language-reference/keywords/out-parameter-modifier.md) 參數，但是可以呼叫具有這類參數的方法。

如需非同步方法的詳細資訊，請參閱 [使用 async 和 await 進行非同步程式設計](../concepts/async/index.md) 和非同步傳回 [類型](../concepts/async/async-return-types.md)。

## <a name="expression-body-definitions"></a>運算式主體定義

方法定義只是立即傳回運算式的結果，或是具有單一陳述式做為方法的主體是很常見的。 使用 `=>`定義這類方法有個語法捷徑：

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

如果方法會傳回 `void` 或非同步方法，則方法的主體必須是陳述式運算式 (如同 lambda)。 若為屬性和索引子，它們必須是唯讀，因此您不應使用 `get` 存取子關鍵字。

## <a name="iterators"></a>迭代器

迭代器會對集合執行自訂的反覆項目，例如清單或陣列。 迭代器會使用 [yield return](../../language-reference/keywords/yield.md) 陳述式來一次傳回一個項目。 當 [yield return](../../language-reference/keywords/yield.md) 到達陳述式時，會記住在程式碼中的目前位置。 下一次呼叫迭代器時，便會從這個位置重新開始執行。

您會使用 [foreach](../../language-reference/keywords/foreach-in.md) 陳述式，透過用戶端程式碼呼叫迭代器。

迭代器的傳回類型可以是 <xref:System.Collections.IEnumerable>、 <xref:System.Collections.Generic.IEnumerable%601>、 <xref:System.Collections.IEnumerator>或 <xref:System.Collections.Generic.IEnumerator%601>。

如需詳細資訊，請參閱 [反覆運算](../concepts/iterators.md)器。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [類別和結構](index.md)
- [存取修飾詞](access-modifiers.md)
- [靜態類別和靜態類別成員](static-classes-and-static-class-members.md)
- [繼承](inheritance.md)
- [抽象和密封類別以及類別成員](abstract-and-sealed-classes-and-class-members.md)
- [params](../../language-reference/keywords/params.md)
- [返回](../../language-reference/keywords/return.md)
- [out](../../language-reference/keywords/out.md)
- [ref](../../language-reference/keywords/ref.md)
- [傳遞參數](passing-parameters.md)
