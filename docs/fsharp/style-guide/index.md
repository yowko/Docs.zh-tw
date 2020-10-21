---
title: F# 樣式指南
description: '瞭解良好 F # 程式碼的五個原則。'
ms.date: 12/10/2018
ms.openlocfilehash: 9f47257626e04b09b546de2ae315d48d791678be
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223652"
---
# <a name="f-style-guide"></a>F# 樣式指南

下列文章說明格式化 F # 程式碼的指導方針，以及語言功能和其使用方式的主題指引。

本指南的設計是根據在大型程式碼基底中使用 F # 搭配不同的程式設計人員群組。 本指引通常會在程式的需求隨著時間而變更時，導致成功使用 F # 並將挫折降到最低。

## <a name="five-principles-of-good-f-code"></a>優質 F # 程式碼的五個準則

當您撰寫 F # 程式碼時，請記住下列原則，特別是在將隨著時間變更的系統中。 進一步文章中的每一項指導方針都是來自這五個重點。

1. **良好的 F # 程式碼簡潔、易懂且可組合**

    F # 有許多功能可讓您以較少的程式碼來表達動作，並重複使用一般功能。 F # 核心程式庫也包含許多實用的型別和函式，可用來處理常見的資料集合。 撰寫您自己的函式，以及 F # 核心程式庫中的函式 (或其他程式庫) 屬於常式慣用 F # 程式設計的一部分。 一般來說，如果您可以用較少的程式碼來表達問題的解決方案，其他開發人員 (或未來的自我) 將會令人激賞。 此外，強烈建議您在需要執行重要工作時使用程式庫（例如 Fsharp.core）、執行 F # 的 [大型 .net 程式庫](../../../api/index.md) ，或 [NuGet](https://www.nuget.org/) 上的協力廠商套件。

2. **良好的 F # 程式碼可互通**

    交互操作可採用多種形式，包括使用不同語言的程式碼。 與其他呼叫端交互操作的程式碼界限是很重要的部分，即使呼叫端也在 F # 中也是一樣。 在撰寫 F # 時，您應該一律考慮其他程式碼如何呼叫您所撰寫的程式碼，包括從另一種語言（例如 c #）。 [F # 元件設計指導方針](component-design-guidelines.md)會詳細描述互通性。

3. **良好的 F # 程式碼會使用物件程式設計，而不是物件方向**

    F # 具有在 .NET 中使用物件進行程式設計的完整支援，包括 [類別](../language-reference/classes.md)、 [介面](../language-reference/interfaces.md)、 [存取](../language-reference/access-control.md)修飾詞、 [抽象類別](../language-reference/abstract-classes.md)等等。 針對更複雜的功能程式碼（例如必須是內容感知的函式），物件可以輕鬆地以函式不能的方式封裝內容資訊。 [選擇性參數和選擇性](../language-reference/members/methods.md#optional-arguments)地使用多[載的功能，可讓](../language-reference/members/methods.md#overloaded-methods)呼叫者更容易使用這項功能。

4. **良好的 F # 程式碼順利執行而不會公開變化**

    這不是撰寫高效能程式碼的秘密，您必須使用變化。 這就是電腦的運作方式。 這類程式碼通常很容易出錯，因此很難正確取得。 避免對呼叫端公開變化。 相反地，請 [建立一個功能介面，以](conventions.md#performance) 在效能很重要時隱藏以變化為基礎的實作為基礎。

5. **Toolable 良好的 F # 程式碼**

    工具很適合用於大型程式碼基底，而且您可以撰寫 F # 程式碼，以便使用 F # 語言工具來更有效地使用它。 其中一個範例是確保您不會以無點的程式設計方式來濫用這個方法它，如此就可以使用偵錯工具來檢查中繼值。 另一個範例是使用 [XML 檔批註](../language-reference/xml-documentation.md) 來描述結構，讓編輯器中的工具提示可以在呼叫位置顯示這些批註。 請務必考慮其他程式設計人員如何使用其工具來讀取、流覽、調試和操作您的程式碼。

## <a name="next-steps"></a>後續步驟

[F # 程式碼格式設定指導方針](formatting.md)提供有關如何格式化程式碼以方便閱讀的指引。

[F # 編碼慣例](conventions.md)提供 f # 程式設計慣用語的指引，可協助長期維護較大的 f # 程式碼基底。

[F # 元件設計指導方針](component-design-guidelines.md)提供撰寫 F # 元件的指引，例如程式庫。
