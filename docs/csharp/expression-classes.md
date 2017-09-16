---
title: "支援運算式樹狀架構的架構類型"
description: "了解支援運算式樹狀架構的架構類型、建立運算式樹狀架構，以及使用運算式樹狀架構 API 的技術。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ed89b286eee9b4c2e11bb27d18e50f777f94f33e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="framework-types-supporting-expression-trees"></a>支援運算式樹狀架構的架構類型

[上一篇 -- 說明運算式樹狀架構](expression-trees-explained.md)

.NET Core Framework 中有使用運算式樹狀架構類別的大型清單。
[這裡](/dotnet/core/api/System.Linq.Expressions)可以看到完整清單。
讓我們了解架構類別是如何設計的，而不是執行完整的清單。

在語言設計中，運算式是估算並傳回值的程式碼本文。 運算式可以非常簡單︰常數運算式 `1` 傳回常數值 1。 它們可以很複雜︰運算式 `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` 傳回一個二次方程式的根 (方程式有解決方案的情況下)。  

## <a name="it-all-starts-with-systemlinqexpression"></a>一切都從 System.Linq.Expression 開始

使用運算式樹狀架構的複雜性之一是許多不同種類的運算式在程式的許多地方都有效。 考慮指派運算式。 指派的右邊可以是常數值、變數、呼叫運算式的方法，或其他。 該語言的彈性表示，當您周遊運算式樹狀結構時，可能會在樹狀結構節點中的任何位置遇到許多不同的運算式類型。 因此，當您可以使用基底運算式類型時，這是最簡單的運作方式。 不過，有時候您需要了解更多。
基底運算式類別包含此用途的 `NodeType` 屬性。
它會傳回 `ExpressionType`，其為可能的運算式類型列舉。
一旦您知道節點類型，就可以將它轉換成該類型，並執行知道運算式節點類型的特定動作。 您可以搜尋特定的節點類型，然後使用這類運算式的特定屬性。

例如，此程式碼會列印變數存取運算式的變數名稱。 我遵循做法先檢查節點類型，然後轉換成變數存取運算式，再檢查特定運算式類型的屬性︰

```csharp
Expression<Func<int, int>> addFive = (num) => num + 5;

if (addFive.NodeType == ExpressionType.Lambda)
{
    var lambdaExp = (LambdaExpression)addFive;

    var parameter = lambdaExp.Parameters.First();

    Console.WriteLine(parameter.Name);
    Console.WriteLine(parameter.Type);
}
```

## <a name="creating-expression-trees"></a>建立運算式樹狀架構

`System.Linq.Expression` 類別也包含許多建立運算式的靜態方法。 這些方法會建立使用其子系所提供引數的運算式節點。 如此一來，您就可以從其分葉節點向上建置運算式。 例如，此程式碼會建立 Add 運算式︰

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

您可以在此簡單的範例中看到，建立和使用運算式樹狀架構牽涉到許多類型。 這種複雜性是必要的，以提供 C# 語言所提供之豐富詞彙的功能。

## <a name="navigating-the-apis"></a>巡覽 API
有可對應幾乎所有 C# 語言語法項目的運算式節點類型。 每個類型都有針對該語言項目類型的特定方法。 您一次要記得很多東西。 我在這裡用的技巧是使用運算式樹狀架構，而不是嘗試記下一切︰
1. 查看 `ExpressionType` 列舉的成員來判斷您應該檢查的可能節點。 當您要周遊並了解運算式樹狀架構時，這真的很有幫助。
2. 查看 `Expression` 類別的靜態成員來建立運算式。 這些方法可以從其一組子節點建置任何運算式類型。
3. 查看 `ExpressionVisitor` 類別來建立修改的運算式樹狀架構。

當您一一查看這三個區域時，會找到更多。 唯一不變的是，當您開始使用這三個步驟的其中一個時，您會找到您要的資訊。
 
 [下一篇 - 執行運算式樹狀架構](expression-trees-execution.md)
 

