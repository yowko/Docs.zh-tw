---
title: 資源管理：use 關鍵字 (F#)
description: "了解 F # 關鍵字 'use' 和 'using' 函式，可以控制的初始設定和版本的資源。"
ms.date: 05/16/2016
ms.openlocfilehash: ffa1cb515139a3705920d9d9f79be1a69602f7d8
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268220"
---
# <a name="resource-management-the-use-keyword"></a>資源管理：use 關鍵字

本主題說明關鍵字`use`而`using`函式，可以控制的初始設定和版本的資源。

## <a name="resources"></a>資源

詞彙*資源*以一個以上的方式使用。 是，資源可以是應用程式使用，例如字串、 圖形和類似項目，但此內容中的資料*資源*是指軟體或作業系統的資源，例如圖形裝置內容、 檔案控制代碼、 網路和資料庫連接、 並行處理的物件，例如等候控制代碼，依此類推。 使用這些資源的應用程式牽涉到取得來自作業系統或其他資源提供者，後面接著之後版本的資源集區，讓它可以提供給另一個應用程式的資源的作業。 當應用程式不會釋放回一般的集區的資源時，會發生問題。

## <a name="managing-resources"></a>管理資源

若要有效率地和負起責任管理應用程式中的資源，您必須釋放資源，立即與可預測的方式。 .NET Framework 可協助您執行此作業藉由提供`System.IDisposable`介面。 型別可實作`System.IDisposable`具有`System.IDisposable.Dispose`方法，這個方法會正確地釋放資源。 撰寫得當的應用程式保證`System.IDisposable.Dispose`時不再需要保留有限的資源的任何物件會立即呼叫。 幸運的是，大部分的.NET 語言提供支援更加容易，而 F # 也不例外。 有兩個實用的語言建構可支援的處置模式：`use`繫結和`using`函式。

## <a name="use-binding"></a>使用繫結

`use`關鍵字有類似的形式`let`繫結：

使用 *值* = *運算式*

它提供與相同的功能`let`繫結，但會增加呼叫`Dispose`值超出範圍時的值。 請注意，編譯器會插入 null 值，檢查，因此，如果值是`null`，呼叫`Dispose`未嘗試。

下列範例示範如何使用自動關閉檔案`use`關鍵字。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
您可以使用`use`在計算運算式中，在此情況下的自訂的版本`use`運算式的使用方式。 如需詳細資訊，請參閱 <<c0> [ 序列](sequences.md)，[非同步工作流程](asynchronous-workflows.md)，並[計算運算式](computation-expressions.md)。

## <a name="using-function"></a>使用函式

`using`函式具有下列格式：

`using` (*expression1*)*函式或 lambda*

在 `using`運算式*expression1*建立必須處置的物件。 結果*expression1* （必須處置的物件） 會變成引數，*值*至*函式或 lambda*，這是預期單一任一函式剩餘的值相符的類型引數所產生*expression1*，或該類型的引數的 lambda 運算式。 在執行函式結束時，執行階段會呼叫`Dispose`，並且釋放資源 (除非值為`null`，在此情況下對 Dispose 的呼叫就不會嘗試)。

下列範例示範`using`使用 lambda 運算式的運算式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

下一個範例顯示`using`函式的運算式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

請注意，此函式可能是有一些已套用的引數的函式。 下列程式碼範例示範此工作。 它會建立包含字串的檔案`XYZ`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using`函式和`use`繫結會幾乎相等的方法可以完成相同的動作。 `using`關鍵字，可提供更充分掌控時`Dispose`呼叫。 當您使用`using`，`Dispose`當您使用時呼叫的函式或 lambda 運算式的結尾`use`關鍵字，`Dispose`呼叫包含的程式碼區塊的結尾。 一般情況下，您應該想要使用`use`而不是`using`函式。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
