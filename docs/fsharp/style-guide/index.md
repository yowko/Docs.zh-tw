---
title: 'F # 文件編寫指南'
description: '了解五個良好的 F # 程式碼的原則。'
ms.date: 05/14/2018
ms.openlocfilehash: 6d8c1336ca991040a8f6e13290d209cb3b70054d
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "34235901"
---
# <a name="f-style-guide"></a>F # 文件編寫指南

下列文章描述格式化的 F # 程式碼和主題的指導方針的語言功能與它們的使用方式的指導方針。

本指南已編寫，根據 F # 中的使用大型程式碼基底與各種程式設計人員組成的群組。 本指導方針通常要成功使用 F #，而且經過一段時間的程式的需求變更時，減少挫折。

## <a name="five-principles-of-good-f-code"></a>良好的 F # 程式碼的五個原則

您應該記住下列原則您撰寫 F # 程式碼，尤其是在系統將會隨著時間變更的任何時間。 在其他文章中的指引的每個片段，源自於這些五個點。

1. **良好的 F # 程式碼是簡潔且具表達性**

    F # 提供許多功能，可讓您在短短幾行程式碼的動作，並重複使用的一般功能。 F # 核心程式庫也包含許多有用的型別及使用資料的常見集合功能。 一般而言，如果您可以在短短幾行程式碼的問題的解決方案來表示其他開發人員 （或您未來的自助） 會令人激賞。 也強烈建議您使用 FSharp.Core，例如程式庫[vast 的.NET 程式庫](https://docs.microsoft.com/dotnet/api/)F # 執行，或第三方封裝上的[NuGet](https://www.nuget.org/)當您需要執行重要工作。

2. **良好的 F # 程式碼可互通**

    交互操作可能需要多個表單，包括使用不同語言的程式碼。 與交互操作的其他呼叫端程式碼的界限是正確的關鍵部分。 在撰寫 F #，您應該一律認為關於如何其他程式碼會呼叫您正在撰寫，包括如果從另一個語言，例如 C# 程式碼。 [F # 元件的設計指導方針](component-design-guidelines.md)描述詳細資料中的互通性。

3. **良好的 F # 程式碼會建立物件程式設計使用，不物件方向**

    F # 進行程式設計物件的完整支援已在.NET 中，包括[類別](../language-reference/classes.md)，[介面](../language-reference/interfaces.md)，[存取修飾詞](../language-reference/access-control.md)，[抽象類別](../language-reference/abstract-classes.md)等等。 針對更複雜功能的程式碼，例如函式，必須了解內容，物件可以輕鬆地將封裝內容資訊的函式不能的方式。 這類功能[選擇性參數](../language-reference/members/methods.md#optional-arguments)小心地使用並[多載](../language-reference/members/methods.md#overloaded-methods)可以取用這項功能的更輕鬆地進行呼叫端。

4. **良好的 F # 程式碼執行，也不暴露變動**

    它是大家撰寫高效能的程式碼，您必須使用變化。 它是電腦的運作方式，畢竟。 這類程式碼通常是容易出錯且很難取得正確的。 避免公開給呼叫端的變化。 相反地，[建置功能的介面，它會隱藏的變化型實作](conventions.md#performance)效能至關重要。

5. **良好的 F # 程式碼是靈活**

    在大型程式碼基底，並使它可更有效地與 F # 語言工具，您可以撰寫 F # 程式碼，是非常寶貴工具。 其中一個範例確保您不要濫用它使用點自由樣式的程式設計，以便偵錯工具可以進行檢查的中繼值。 另一個範例使用[XML 文件註解](../language-reference/xml-documentation.md)描述建構，使得在呼叫站台，在編輯器中的工具提示可以顯示這些註解。 一定會想要如何您的程式碼來讀取、 巡覽、 偵錯，並操作其工具與其他程式設計人員。

## <a name="next-steps"></a>後續步驟

[F # 程式碼格式化方針](formatting.md)指導您如何格式化程式碼，使其易於閱讀。

[F # 程式碼撰寫慣例](conventions.md)F # 程式設計語言，有助於長期維護的較大的 F # 程式碼基底提供指引。

[F # 元件的設計指導方針](component-design-guidelines.md)提供撰寫 F # 元件，例如程式庫指引。
