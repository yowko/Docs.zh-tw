---
title: 'F # 樣式指南'
description: '了解五個很好的 F # 程式碼的原則。'
ms.date: 05/14/2018
ms.openlocfilehash: 6d8c1336ca991040a8f6e13290d209cb3b70054d
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235901"
---
# <a name="f-style-guide"></a>F # 樣式指南

下列文章描述格式化 F # 程式碼的語言功能的主題是指導和它們的使用方式的指導方針。

本指南已成形，根據 F # 中的使用大型程式碼基底與不同的程式設計人員群組。 本指南通常會導致成功使用 F # 的而且程式的需求會隨時間變更時，最小化麻煩。

## <a name="five-principles-of-good-f-code"></a>五個很好的 F # 程式碼原則

您應該記住下列原則您撰寫 F # 程式碼，尤其是在系統將會隨著時間變更的任何時間。 指南進一步文件中的每個片段都源自於這些五個點。

1. **簡潔且具表達性，是很好的 F # 程式碼**

    F # 具有許多功能，讓您表示較少的程式碼行中的動作，並重複使用的一般功能。 F # 核心程式庫也包含許多有用的型別和使用通用的資料集合的功能。 一般而言，如果你可以解決問題，以較少的行程式碼，其他開發人員 （或您未來自助） 將感激。 也強烈建議您使用的程式庫，例如 FSharp.Core， [vast 的.NET 程式庫](https://docs.microsoft.com/dotnet/api/)F # 執行，或第三方封裝上的[NuGet](https://www.nuget.org/)當您需要執行重要的工作。

2. **良好的 F # 程式碼具有互通性**

    互通性可以有多個形式，包括使用不同語言的程式碼。 與交互操作的其他呼叫端程式碼的界限是正確的重要片段。 在撰寫 F #，您應該一律想成有關如何其他程式碼會呼叫您要撰寫，包括若從另一個語言，例如 C# 程式碼。 [F # 元件的設計指導方針](component-design-guidelines.md)說明詳細的互通性。

3. **良好 F # 程式碼會使用程式設計物件，不是物件的方向**

    F # 的程式設計物件的完整支援已在.NET 中，包括[類別](../language-reference/classes.md)，[介面](../language-reference/interfaces.md)，[存取修飾詞](../language-reference/access-control.md)，[抽象類別](../language-reference/abstract-classes.md)，依此類推。 對於更複雜功能的程式碼，例如函式，必須了解內容，物件可以輕鬆地將封裝內容的資訊函式不能儲存方式。 這類功能[選擇性參數](../language-reference/members/methods.md#optional-arguments)和[多載](../language-reference/members/methods.md#overloaded-methods)也有助於讓呼叫端的耗用量的這項功能。

4. **良好的 F # 程式碼執行也而不會暴露變動**

    若要撰寫高效能程式碼，您必須使用變動沒有密碼它。 它是電腦的運作方式，在所有。 這類程式碼通常是容易出錯且難度增加正確。 避免公開給呼叫端的變化。 透過變動為基礎的實作搜尋功能的介面。

5. **良好的 F # 程式碼是 toolable**

    在大型程式碼基底的工具是重要的您可以撰寫 F # 程式碼，它可更有效地與 F # 語言工具。 其中一個範例確定您不要過量使用點可用樣式的程式設計，以便可以進行偵錯工具檢查中繼值。 另一個範例使用[XML 文件註解](../language-reference/xml-documentation.md)描述建構，以便在編輯器中的工具提示可以顯示這些註解位於呼叫位置。 一律思考如何您的程式碼將會讀取、 巡覽、 偵錯，以及操作工具與其他程式設計人員的。

## <a name="next-steps"></a>後續步驟

[F # 程式碼格式化方針](formatting.md)提供如何格式化程式碼，使其更易讀的指引。

[F # 編碼慣例](conventions.md)F # 的程式設計語言，有助於長期維護較大的 F # 程式碼基底提供指引。

[F # 元件的設計指導方針](component-design-guidelines.md)提供指導方針撰寫 F # 元件，例如文件庫。
