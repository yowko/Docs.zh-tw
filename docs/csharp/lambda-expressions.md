---
title: "Lambda 運算式"
description: "了解如何使用 Lambda 運算式，這是可當做引數傳遞的可執行程式碼區塊。"
keywords: ".NET, .NET Core, Lambda 運算式, Lambda, 委派"
ms-author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 82b912eb393aeaf6e222f2ce20e6a1a99b4a3662
ms.lasthandoff: 03/13/2017

---

# <a name="lambda-expressions"></a>Lambda 運算式 #

「Lambda 運算式」**是當做物件處理的程式碼區塊 (運算式或陳述式區塊)。 它可當做方法的引數傳遞，也可由方法呼叫傳回。 Lambda 運算式可大量用於：

- 將要執行的程式碼傳遞至非同步方法，例如 @System.Threading.Tasks.Task.Run(System.Action)。

- 撰寫 [LINQ 查詢運算式](linq/index.md)。

- 建立[運算式樹狀架構](expression-trees-building.md)。

Lambda 運算式是可表示為委派或編譯成委派之運算式樹狀架構的程式碼。 Lambda 運算式的特定委派類型取決於其參數和傳回值。 未傳回值的 Lambda 運算式會根據其參數數目對應至特定 `Action` 委派。 傳回值的 Lambda 運算式會根據其參數數目對應至特定 `Func` 委派。 例如，具有兩個參數但未傳回值的 Lambda 運算式會對應至 @System.Action%602 委派。 具有一個參數且傳回值的 Lambda 運算式會對應至 @System.Func%602 委派。

Lambda 運算式使用 [Lambda 宣告運算子](language-reference/operators/lambda-operator.md) `=>`，來分隔 Lambda 的參數清單及其可執行程式碼。 若要建立 Lambda 運算式，請在 Lambda 運算子的左邊指定輸入參數 (如果有的話)，並將運算式或陳述式區塊放在另一邊。 例如，單行 Lambda 運算式 `x => x * x` 會指定名為 `x` 的參數，並傳回 `x` 的平方值。 您可以將這個運算式指派給委派類型，如下列範例所示：

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

您也可以將它當做方法引數直接傳遞：

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a>運算式 Lambda ##

 在 => 運算子右邊有運算式的 Lambda 運算式稱為「運算式 Lambda」**。 運算式 Lambda 會在[運算式樹狀架構](expression-trees.md)的建構過程中大量使用。 運算式 Lambda 會傳回運算式的結果，並採用下列基本形式：

```csharp
(input parameters) => expression
```

只有在 Lambda 包含一個輸入參數時，括號才是選擇項，否則括號是必要項。 以空括號指定零個輸入參數：

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

兩個或多個輸入參數會包含在括號中，並且以逗號分隔：

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

通常，編譯器會使用型別推斷來判斷參數類型。 不過，有時候編譯器會很難或是無法推斷輸入類型。 當這種情形發生時，您可以明確指定類型，如下列範例所示：

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

請注意，在上面的範例中，運算式 Lambda 的主體可以包含方法呼叫。 不過，如果您要建立在 .NET Framework 外部 (例如在 SQL Server 或 Entity Framework (EF) 中) 評估的運算式樹狀架構，則不應在 Lambda 運算式中使用方法呼叫，因為這些方法在 .NET 執行階段內容之外可能不具任何意義。 如果您在此情況下確實選擇使用方法呼叫，請務必徹底測試，以確保可成功解析方法呼叫。

## <a name="statement-lambdas"></a>陳述式 Lambda ##

陳述式 Lambda 看起來就像是運算式 Lambda，不同之處在於，陳述式會包含於大括號內：

```csharp
(input parameters) => { statement; }
```

陳述式 Lambda 的主體可以包含任意數目的陳述式，但是實際上通常不會超過兩個或三個陳述式。

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

陳述式 Lambda 就像匿名方法，它不能用來建立運算式樹狀架構。

## <a name="async-lambdas"></a>非同步 Lambda ##

您可以使用 [async](language-reference/keywords/async.md) 和 [await](language-reference/keywords/await.md) 關鍵字，輕鬆建立結合非同步處理的 Lambda 運算式和陳述式。 例如，下列範例會呼叫以非同步方式執行的 `ShowSquares` 方法。

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

如需如何建立和使用非同步方法的詳細資訊，請參閱[使用 Async 和 Await 進行非同步程式設計](programming-guide/concepts/async/index.md)。

## <a name="lambda-expressions-and-tuples"></a>Lambda 運算式和元組 ##

從 C# 7.0 開始，C# 語言提供元組的內建支援。 您可以將元組當做引數提供給 Lambda 運算式，而您的 Lambda 運算式也可以傳回元組。 在某些情況下，C# 編譯器會使用型別推斷來判斷元組元件的類型。 

若要定義元組，請以括號括住其元件的逗號分隔清單。 下列範例使用具有 5 個元件的元組將一連串數字傳遞至 Lambda 運算式，這會使每個值加倍，並傳回內含乘法運算結果之具有 5 個元件的元組。

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

通常，元組的欄位會命名為 `Item1`、`Item2`，依此類推。不過，您可以定義具有具名元件的元組，如下列範例所示。

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

如需 C# 中元組支援的詳細資訊，請參閱 [C# 元組類型](tuples.md)。

## <a name="lambdas-with-the-standard-query-operators"></a>具有標準查詢運算子的 Lambda ##

其他實作中的 LINQ to Objects 具有輸入參數，其類型是其中一種 @System.Func%601 系列的泛型委派。 這些委派使用型別參數定義輸入參數的數目和類型，以及委派的傳回型別。 對於封裝套用至一組來源資料中每個項目的使用者定義運算式而言，`Func` 委派非常實用。 例如，假設 @System.Func%601 委派的語法如下：

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

委派可以透過下列程式碼具現化

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

其中 `int` 是輸入參數，而 `bool` 是傳回值。 傳回值一律在最後一個類型參數中指定。 叫用下列 `Func` 委派時將會傳回 true 或 false，指出輸入參數是否等於 5：

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

您也可以在引數類型為 @System.Linq.Expressions.Expression%601 時提供 Lambda 運算式，例如在定義於 @System.Linq.Queryable 類型的標準查詢運算子中。 當您指定 @System.Linq.Expressions.Expression%601 引數時，Lambda 會編譯成運算式樹狀架構。 下列範例使用 [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) 標準查詢運算子。

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

編譯器會推斷輸入參數的類型，您也可以明確指定類型。 這個特殊 Lambda 運算式會計算除以二之後餘數為 1 的整數 (`n`)。

下列範例產生的序列會包含 `numbers` 陣列中所有位於 9 前面的項目，因為 9 是序列中第一個不符合條件的數字。

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

下列範例會用括號括住的方式來指定多個輸入參數。 這個方法會傳回數字陣列中的所有項目，直到遇到其值小於陣列中的序數位置的數字為止。

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a>Lambda 運算式中的型別推斷 ##

撰寫 Lambda 時，您通常不需要指定輸入參數的類型，這是因為編譯器可以根據 Lambda 主體、參數類型，以及 C# 語言規格中所述的其他因素來推斷類型。 對於大多數的標準查詢運算子而言，第一項輸入是來源序列中項目的類型。 如果您要查詢 `IEnumerable<Customer>`，則輸入變數就會推斷為 `Customer` 物件，這表示您可以存取其方法和屬性：

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

以下是 Lambda 型別推斷的一般規則：

- Lambda 必須包含與委派類型相同數目的參數。

- Lambda 中的每個輸入引數都必須能夠隱含轉換為其對應的委派參數。

- Lambda 的傳回值 (如果有的話) 必須能夠隱含轉換為委派的傳回類型。

請注意，Lambda 運算式本身並沒有類型，因為一般類型系統沒有內建的「Lambda 運算式」概念。 不過，有時候一般所稱的 Lambda 運算式「類型」會很實用。 在這類情況下，類型是指委派類型或是 Lambda 運算式轉換成的 @System.Linq.Expressions.Expression 類型。

## <a name="variable-scope-in-lambda-expressions"></a>Lambda 運算式中的變數範圍 ##

Lambda 可以參考「外部變數」**(請參閱[匿名方法](programming-guide/statements-expressions-operators/anonymous-methods.md))，這些變數必須包含在定義 Lambda 函式的方法範圍內，或是在包含 Lambda 運算式的類型範圍內。 以這種方式擷取的變數會加以儲存，以便在 Lambda 運算式中使用，即使這些變數可能會超出範圍而遭到記憶體回收。 外部變數必須確實指派，才能用於 Lambda 運算式。 下列範例將示範這些規則。

[!CODE [csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 下列規則適用於 Lambda 運算式中的變數範圍：

- 已擷取的變數要等到參考該變數的委派符合記憶體回收的資格時，才會進行記憶體回收。

- 導入 Lambda 運算式內的變數無法在外部方法中看見。

- Lambda 運算式無法直接從封入方法擷取 `ref` 或 `out` 參數。

- Lambda 運算式中的 return 陳述式不會造成封入方法傳回。

- 如果跳躍陳述式的目標不在區塊內，則 Lambda 運算式不可包含 Lambda 函式內的 `goto` 陳述式、 `break` 陳述式或 `continue` 陳述式。 即使目標位於區塊內，跳躍陳述式出現在 Lambda 函式區塊外部也一樣是錯誤。

## <a name="see-also"></a>請參閱 ##

[LINQ (Language-Integrated Query)](../standard/using-linq.md)   
[匿名方法](programming-guide/statements-expressions-operators/anonymous-methods.md)   
[運算式樹狀架構](expression-trees.md)

