---
title: F#風格指南
description: 了解的良好的五個原則F#程式碼。
ms.date: 12/10/2018
ms.openlocfilehash: 9f47257626e04b09b546de2ae315d48d791678be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61901845"
---
# <a name="f-style-guide"></a>F#風格指南

下列文章描述格式的指導方針F#程式碼和主題的指導方針的語言功能及如何使用它們。

本指南已編寫，以使用F#在大型程式碼基底與各種程式設計人員組成的群組。 本指導方針通常會導致成功使用F#，而且經過一段時間的程式的需求變更時，減少挫折。

## <a name="five-principles-of-good-f-code"></a>為 「 好的五個原則F#程式碼

請記住您撰寫的任何時間的下列原則F#程式碼，尤其是會隨著時間而變更的系統。 在其他文章中的指引的每個片段，源自於這些五個點。

1. **良好F#程式碼是簡潔、 易懂且可組合**

    F#有許多功能可讓您在短短幾行程式碼的動作，並重複使用的一般功能。 F#核心程式庫也包含許多有用的型別及使用資料的常見集合功能。 撰寫您自己的函式和中的F#核心程式庫 （或其他程式庫） 是慣用的例行工作F#程式設計。 一般而言，如果您可以在短短幾行程式碼的問題的解決方案來表示其他開發人員 （或您未來的自助） 會令人激賞。 此外，強烈建議您使用的程式庫，例如 FSharp.Core， [vast 的.NET 程式庫](../../../api/index.md)，F#上，執行或第三方封裝上的[NuGet](https://www.nuget.org/)當您需要執行重要工作。

2. **良好F#程式碼可互通**

    交互操作可能需要多個表單，包括使用不同語言的程式碼。 與交互操作的其他呼叫端程式碼的界限是關鍵的部分，以取得正確的即使呼叫端也會在F#。 在撰寫F#，您應該一律認為關於如何其他程式碼會呼叫您要撰寫，包括如果從另一個語言，例如程式碼C#。 [ F#元件的設計指導方針](component-design-guidelines.md)說明詳細的互通性。

3. **良好F#程式碼會建立物件程式設計使用，不物件方向**

    F#提供完整的支援，使用物件進行程式設計，在.NET 中，包括[類別](../language-reference/classes.md)，[介面](../language-reference/interfaces.md)，[存取修飾詞](../language-reference/access-control.md)，[抽象類別](../language-reference/abstract-classes.md)等等。 針對更複雜功能的程式碼，例如函式，必須了解內容，物件可以輕鬆地將封裝內容資訊的函式不能的方式。 這類功能[選擇性參數](../language-reference/members/methods.md#optional-arguments)小心地使用並[多載](../language-reference/members/methods.md#overloaded-methods)可以取用這項功能的更輕鬆地進行呼叫端。

4. **良好F#程式碼會執行也不暴露變動**

    它是大家撰寫高效能的程式碼，您必須使用變化。 它是電腦的運作方式，畢竟。 這類程式碼通常是容易出錯且很難取得正確的。 避免公開給呼叫端的變化。 相反地，[建置功能的介面，它會隱藏的變化型實作](conventions.md#performance)效能至關重要。

5. **良好F#程式碼是靈活**

    工具很寶貴，針對在大型程式碼基底，而且您可以撰寫F#程式碼，它可更有效地與F#語言的工具。 其中一個範例確保您不要濫用它使用點自由樣式的程式設計，以便偵錯工具可以進行檢查的中繼值。 另一個範例使用[XML 文件註解](../language-reference/xml-documentation.md)描述建構，使得在呼叫站台，在編輯器中的工具提示可以顯示這些註解。 一定會想要如何您的程式碼來讀取、 巡覽、 偵錯，並操作其工具與其他程式設計人員。

## <a name="next-steps"></a>後續步驟

[ F#程式碼格式設定指導方針](formatting.md)指導您如何格式化程式碼，使其易於閱讀。

[ F#程式碼撰寫慣例](conventions.md)提供的指引F#程式設計慣用語有助於長期維護較大的F#程式碼基底。

[ F#元件的設計指導方針](component-design-guidelines.md)提供撰寫指引F#元件，例如程式庫。
