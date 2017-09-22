---
title: "委派簡介"
description: "透過此概觀主題了解委派，該主題介紹委派的基本概念，並討論委派的語言設計目標。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: dd4c68fb4f960d0c2d5cbdc9e699650070cacaf1
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="introduction-to-delegates"></a>委派簡介

[上一個](delegates-events.md)

委派提供 .NET 中的「晚期繫結」機制。 「晚期繫結」表示您建立演算法，在其中，呼叫端也會提供至少一個方法來實作演算法的一部分。

例如，請考慮排序天文學應用程式中的星星清單。
您可以選擇排序這些星星與地球的距離、星星的亮度，或其可察覺的亮度。

在所有這些情況下，Sort() 方法的做法基本上相同︰根據某個比較來排列清單中的項目。 針對每個排序順序，比較兩顆星的程式碼會不同。

這類解決方案已用於軟體達中半世紀之久。
C# 語言委派概念提供一流的語言支援，以及這類概念的型別安全。

如您將在本系列稍後所見，您為這類演算法所撰寫的 C# 程式碼為型別安全，並利用語言和編譯器確保引數和傳回型別的類型相符。

## <a name="language-design-goals-for-delegates"></a>委派的語言設計目標

語言設計人員會針對最後成為委派的功能列舉數個目標。

小組想要將通用語言建構用於任何晚期繫結演算法。 這可讓開發人員了解一個概念，並將這個相同的概念用於許多不同的軟體問題。

其次，小組想要同時支援單一和多點傳送方法呼叫 (多點傳送委派是已將多個方法鏈結在一起的委派)。 您將在[本系列稍後](delegate-class.md)看到範例。 

小組想要委派支援開發人員期待所有 C# 建構的相同型別安全。 

最後，小組已辨識事件模式是委派或任何晚期繫結演算法十分有用的一種特定模式。 小組想要確保委派的程式碼可以提供 .NET 事件模式的基礎。

該工作的結果已是 C# 和 .NET 中的委派和事件支援。 本節的其餘文章將涵蓋語言功能、程式庫支援，以及使用委派時所使用的一般慣用語。

您將了解 `delegate` 關鍵字和其所產生的程式碼。 您將了解 `System.Delegate` 類別的功能，以及如何使用這些功能。 您將了解如何建立型別安全委派，以及如何建立可透過委派叫用的方法。 您也將了解如何使用 Lambda 運算式來使用委派和事件。 您將看到委派成為一個 LINQ 之建置區塊的位置。 您將了解委派如何是 .NET 事件模式的基礎和其差異。

整體來說，您將看到委派如何在 .NET 中進行程式設計以及使用架構 API 時成為不可或缺部分。

我們現在就開始吧。

[下一個](delegate-class.md)

