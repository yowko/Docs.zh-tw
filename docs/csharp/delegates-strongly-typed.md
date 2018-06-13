---
title: 強類型委派
description: 了解如何在建立需要委派的功能時，使用泛型委派類型來宣告自訂類型。
ms.date: 06/20/2016
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 2e4cc1c7bfa0aaa90f3aaefa0da64c5486a9d10f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215160"
---
# <a name="strongly-typed-delegates"></a>強類型委派

[上一步](delegate-class.md)

在前一篇文章中，您看到您使用 `delegate` 關鍵字來建立特定委派類型。 

抽象委派類別提供進行鬆散結合和叫用的基礎結構。 具體委派類型會變得更為好用，原因是採行和強制新增至委派物件的引動過程清單之方法的型別安全。 當您使用 `delegate` 關鍵字並定義具體委派類型時，編譯器會產生這些方法。

實際上，只要您需要不同的方法簽章，這就會建立新的委派類型。 這項工作在一段時間之後會十分繁瑣。 每項新功能都需要新的委派類型。

還好，這不是必要的。 .NET 核心架構包含您只要需要委派類型即可重複使用的數個類型。 這些是[泛型](programming-guide/generics/index.md)定義，因此當您需要新的方法宣告時，可以宣告自訂項目。 

這些類型的第一個是 <xref:System.Action> 類型和數個變化：

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

有關共變數的文章涵蓋泛型型別引數上的 `in` 修飾詞。

最多包含 16 個引數的 `Action` 委派有多種變化，例如 <xref:System.Action%6016>。
這些定義一定要為每個委派引數使用不同的泛型引數：這讓您擁有最大的彈性。 方法引數不需要但可以是相同的類型。

針對任何具有 void 傳回型別的委派類型，使用其中一個 `Action` 類型。

此架構也包含數個泛型委派類型，可用於傳回值的委派類型︰

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

有關共變數的文章涵蓋結果泛型型別引數上的 `out` 修飾詞。

最多有 16 個輸入引數的 `Func` 委派有多種變化，例如 <xref:System.Func%6017>。
依照慣例，結果的類型一律是所有 `Func` 宣告中的最後一個型別參數。

針對任何傳回值的委派類型，使用其中一個 `Func` 類型。

針對在單一值上傳回測試的委派，也有特殊的 <xref:System.Predicate%601> 類型：

```csharp
public delegate bool Predicate<in T>(T obj);
```

您可能會注意到，針對任何 `Predicate` 類型，會有結構上相等的 `Func` 類型。例如︰

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

您可能會將這兩個類型視為相等。 但它們並不相等。
這兩個變數不能交換使用。 某個類型的變數無法獲指派另一個類型。 C# 型別系統會使用所定義類型的名稱，而不是結構。

.NET 核心程式庫中的所有這些委派類型定義都應該表示，您不需要針對任何您所建立且需要委派的新功能定義新的委派類型。 這些泛型定義應該提供您在大部分情況下所需要的所有委派類型。 您可以只具現化具有必要型別參數的其中一個類型。 如果是可以設為泛型的演算法，則可以將這些委派用作泛型型別。 

這應該會節省時間，並將您建立來使用委派所需的新類型數目減到最少。

在下一篇文章中，您將看到實際使用委派的數個常見模式。

[下一步](delegates-patterns.md)
