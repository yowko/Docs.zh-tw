---
title: "System.Delegate 和 `delegate` 關鍵字"
description: "System.Delegate 和 `delegate` 關鍵字"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f3742fda-13c2-4283-8966-9e21c2674393
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b20c4816582ef3e4d36512c38947f64e86d26541
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---

# <a name="systemdelegate-and-the-delegate-keyword"></a>System.Delegate 和 `delegate` 關鍵字

[上一個](delegates-overview.md)

本文將介紹 .NET Framework 中支援委派的類別，以及這些類別與 `delegate` 關鍵字的對應關係。

## <a name="defining-delegate-types"></a>定義委派型別

首先讓我們說明 'delegate' 關鍵字，因為您在使用委派時主要會用到這個項目。 當您使用 `delegate` 關鍵字時，編譯器產生的程式碼會對應到叫用 @System.Delegate 和 @System.MulticastDelegate 類別成員的方法呼叫。 

定義委派型別的語法與定義方法簽章的語法類似。 您只需要將 `delegate` 關鍵字加入定義中。

讓我們繼續使用 List.Sort() 方法作為範例。 第一個步驟是建立比較委派的型別：

```csharp
// From the .NET Core library

// Define the delegate type:
public delegate int Comparison<in T>(T left, T right);
```

編譯器會產生一個衍生自 `System.Delegate` 且符合所用簽章的類別 (在此情況下，其為一個會傳回整數且具有兩個引數的方法)。 該委派的型別為 `Comparison`。 `Comparison` 委派型別是泛型型別。 如需泛型的詳細資料，請參閱[這裡](generics.md)。

請注意，此語法看似在宣告一個變數，但實際上是宣告「型別」**。 您可以在類別中定義委派型別、直接在命名空間中定義，或甚至在全域命名空間中加以定義。

> [!NOTE]
> 不過，我們並不建議您直接宣告全域命名空間中的委派型別 (或其他型別)。 

編譯器也會產生這個新型別的加入處理常式和移除處理常式，該類別的用戶端即可在執行個體的引動過程清單中加入和移除方法。 編譯器會強制確保您要加入或移除的方法簽章符合宣告方法時所用的簽章。 

## <a name="declaring-instances-of-delegates"></a>宣告委派的執行個體

定義委派之後，您可以建立該型別的執行個體。
如同 C# 中的所有變數一般，您無法直接宣告命名空間或全域命名空間中的委派執行個體。

```csharp
// inside a class definition:

// Declare an instance of that type:
public Comparison<T> comparator;
```

變數的型別為稍早定義的 `Comparison<T>` 委派型別。 變數的名稱為 `comparator`。
 
 上述程式碼片段會宣告類別內的成員變數。 您也可以宣告本身為區域變數或方法引數的委派變數。

## <a name="invoking-delegates"></a>叫用委派

您可以呼叫委派，藉此叫用該委派引動過程清單中的方法。 在 `Sort()` 方法中，程式碼會呼叫比較方法以判斷物件的放置順序：

```csharp
int result = comparator(left, right);
```

在上述該行中，程式碼會「叫用」**附加至委派的方法。
您可將變數視為方法名稱，並使用一般方法呼叫語法加以叫用。

該行程式碼會進行不安全的假設︰因此無法保證目標已新增至委派。 如果未附加任何目標，上述行會導致系統擲回 `NullReferenceException`。 我們會在本[系列](delegates-patterns.md)稍後說明可用來解決這個問題的慣用語，這些慣用語比簡單的 null 檢查更複雜。

## <a name="assigning-adding-and-removing-invocation-targets"></a>指派、加入和移除引動過程的目標

這涉及委派型別的定義方式，以及委派執行個體的宣告和叫用方式。

如果開發人員想要使用 `List.Sort()` 方法，則需要先定義一個方法，使其簽章符合委派型別的定義，並將它指派給排序方法所用的委派。 此指派會將這個方法新增至該委派物件的引動過程清單。

假設您想要依據字串長度來排序清單， 您的比較函式可能如下︰

```csharp
private static int CompareLength(string left, string right)
{
    return left.Length.CompareTo(right.Length);
}
```

此方法會以私用方法的形式宣告。 沒關係， 您可能不希望這個方法成為公用介面的一部分。 它仍可以在附加至委派時作為比較方法來使用。 呼叫程式碼會將這個方法附加至委派物件的目標清單，並透過該委派進行存取。

您可以該方法傳遞給 `List.Sort()` 方法，以建立這種關聯性：

```csharp
phrases.Sort(CompareLength);
```

請注意，使用的方法名稱不含括弧。 將方法作為引數使用時，系統會指示編譯器將方法參考轉換成可作為委派引動過程的目標，並將該方法附加為叫用目標。

您可能也已宣告 'Comparison<string>` 型別的變數並進行指派，以便明確宣告：

```csharp
Comparison<string> comparer = CompareLength;
phrases.Sort(comparer);
```

適用於作為委派目標的方法是小型方法的情況，且通常會使用 [Lambda 運算式](lambda-expressions.md)語法來執行指派：

```csharp
Comparison<string> comparer = (left, right) => left.Length.CompareTo(right.Length);
phrases.Sort(comparer);
```

[稍後章節](delegates-patterns.md)會進一步說明如何針對委派目標使用 Lambda 運算式。

Sort() 範例通常會將單一的目標方法附加至委派。 即便如此，委派物件仍支援具有多個目標方法 (附加至委派物件) 的引動過程清單。

## <a name="delegate-and-multicastdelegate-classes"></a>Delegate 和 MulticastDelegate 類別

上述語言支援提供使用委派時通常需要的功能與支援。 這些功能都是建置在 .NET Core Framework 的 @System.Delegate 和 @"System.MulticastDelegate" 兩個類別之上。

`System.Delegate` 類別和其單一的直接子類別 `System.MulticastDelegate` 提供的架構支援，可用來建立委派、將方法註冊為委派目標，以及叫用註冊為委派目標的所有方法。 

有趣的是，`System.Delegate` 和 `System.MulticastDelegate` 類別本身不是委派型別， 卻可提供所有特定委派型別的基礎。 這個相同的語言設計程序要求您不能宣告衍生自 `Delegate` 或 `MulticastDelegate` 的類別。 C# 語言規則禁止使用該類別。
 
相反地，當您使用 C# 語言關鍵字來宣告委派型別時，C# 編譯器會建立一個衍生自 `MulticastDelegate` 的類別執行個體。

這種設計起源於第一版的 C# 和 .NET。 設計團隊的其中一個目標是要確保使用委派時，語言能強制執行型別安全。 亦即，系統必須確保叫用委派時使用正確的引數型別和數目， 以及在編譯時間能正確表示任何傳回的型別。 委派是屬於 .NET 1.0 版本的一部分，也就是泛型之前的版本。

要強制執行此型別安全的最佳方式，是讓編譯器建立具象委派類別，以表示要使用的方法簽章。

雖然您不能直接建立衍生的類別，但仍會用到這些類別上所定義的方法。 接著，我們將逐步解說使用委派時最常使用的方法。

首先，最重要的是記住您使用的每個委派皆衍生自 `MulticastDelegate`。 多點傳送委派是指，透過委派叫用時，可以叫用一個以上的方法目標。 原本的設計考量是要區隔只能附加並叫用一個目標方法的委派，以及可以附加並叫用多個目標方法的委派。 但經過證實，這種區隔的實務效果比原先設想的還要差。 不過這兩個不同的類別自其初始公開版本就已經建立，且在架構當中。

您最常搭配使用委派的方法是 `Invoke()` 和 `BeginInvoke()` / `EndInvoke()`。 `Invoke()` 會叫用已附加至特定委派執行個體的所有方法。 如上方所見，您通常會使用委派變數上的方法呼叫語法來叫用委派。 您可在[本系列中稍後](delegates-patterns.md)看到直接使用這些方法的模式。

現在，您已了解支援委派的語言語法與類別，讓我們來查看如何使用、建立及叫用強型別的委派。

[下一個](delegates-strongly-typed.md)
