---
title: F# 樣式指南
description: 瞭解良好 F# 代碼的五個原則。
ms.date: 12/10/2018
ms.openlocfilehash: 9f47257626e04b09b546de2ae315d48d791678be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400264"
---
# <a name="f-style-guide"></a>F# 樣式指南

以下文章介紹了 F# 代碼的格式設置指南以及語言功能的專題指南以及如何使用它們。

本指南是根據在具有不同程式師組的大型代碼庫中使用 F# 制定的。 本指南通常會導致 F# 的成功使用，並最大限度地減少程式要求隨時間變化時的挫折感。

## <a name="five-principles-of-good-f-code"></a>良好 F# 代碼的五個原則

在編寫 F# 代碼時，請記住以下原則，尤其是在隨時間變化的系統中。 進一步文章中的每一條指導都源于這五點。

1. **好的 F# 代碼簡潔、富有表現力且可組合**

    F# 具有許多功能，允許您以更少的程式碼表示操作並重用通用功能。 F# 核心庫還包含許多有用的類型和函數，用於處理常見的資料集合。 您自己的函數和 F# 核心庫（或其他庫）中的函數的組成是常規慣用 F# 程式設計的一部分。 通常，如果能夠用更少的程式碼來表達問題的解決方案，其他開發人員（或您未來的自我）將非常感激。 強烈建議您使用 FSharp.Core、F# 運行[的龐大 .NET 庫](../../../api/index.md)等庫，或者當您需要執行一項不平凡的任務時，使用[NuGet](https://www.nuget.org/)上的協力廠商包。

2. **好的 F# 代碼是可交互操作的**

    交互操作可以採取多種形式，包括使用不同語言的代碼。 其他調用方交互操作的代碼邊界是正確獲取的關鍵區段，即使調用方也位於 F#中也是如此。 編寫 F#時，應始終考慮如何將其他代碼調用您編寫的代碼，包括它們是否從其他語言（如 C#）調用。 [F# 元件設計指南](component-design-guidelines.md)詳細介紹了互通性。

3. **好的 F# 代碼使用物件程式設計，而不是物件導向**

    F# 完全支援使用 .NET 中的物件進行程式設計，包括[類](../language-reference/classes.md)、[介面](../language-reference/interfaces.md)、[訪問修改器](../language-reference/access-control.md)、[抽象類別](../language-reference/abstract-classes.md)等。 對於更複雜的功能代碼（如必須具有上下文感知功能的函數），物件可以輕鬆地以函數無法的方式封裝上下文資訊。 [可選參數](../language-reference/members/methods.md#optional-arguments)和謹慎使用[重載](../language-reference/members/methods.md#overloaded-methods)等功能可以使調用方更輕鬆地使用此功能。

4. **良好的 F# 代碼在未暴露突變的情況下表現良好**

    編寫高性能代碼，必須使用突變，這已不為人有。 畢竟，這是電腦的工作原理。 此類代碼通常容易出錯，難以正確。 避免向呼叫者公開突變。 相反，[構建一個功能介面，在性能至關重要時隱藏基於突變的實現](conventions.md#performance)。

5. **好的 F# 代碼是可工具的**

    工具對於在大型代碼庫中工作非常寶貴，您可以編寫 F# 代碼，以便可以更有效地將其用於 F# 語言工具。 一個例子是確保您不會使用無點程式設計樣式過度使用，以便可以使用調試器檢查中間值。 另一個示例是使用[XML 文檔注釋](../language-reference/xml-documentation.md)來描述構造，以便編輯器中的工具提示可以在調用網站顯示這些注釋。 始終思考如何被其他程式師使用他們的工具讀取、導航、調試和操作代碼。

## <a name="next-steps"></a>後續步驟

[F# 代碼格式設置指南](formatting.md)提供有關如何設置代碼格式以便易於閱讀的指導。

[F# 編碼約定](conventions.md)為 F# 程式設計習慣用語提供指導，這將有助於對較大的 F# 代碼庫進行長期維護。

[F# 元件設計指南](component-design-guidelines.md)為編寫 F# 元件（如庫）提供了指南。
