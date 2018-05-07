---
title: 資源管理：use 關鍵字 (F#)
description: "了解 F # 關鍵字 'use' 和 '使用' 函式，可以控制的初始設定和版本的資源。"
ms.date: 05/16/2016
ms.openlocfilehash: c75783080d1d87c6ee75aede500d3d0b3fdf8355
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="resource-management-the-use-keyword"></a>資源管理：use 關鍵字

本主題描述關鍵字`use`和`using`函式，可以控制的初始設定和版本的資源。

## <a name="resources"></a>資源
詞彙*資源*以一個以上的方式使用。 [是]，資源可以是應用程式使用，例如字串、 圖形和類似項目，但在此內容中的資料*資源*指的是軟體或作業系統的資源，例如圖形裝置內容、 檔案控制代碼、 網路和資料庫的連接、 並行的物件，例如等候控制代碼，依此類推。 使用這些資源應用程式所牽涉到來自作業系統或其他資源提供者，後面接著之後版本的資源集區，讓它可以提供給另一個應用程式的資源擷取。 當應用程式不會釋放回一般的集區的資源時，會發生問題。

## <a name="managing-resources"></a>管理資源
若要有效率地和以負責的態度管理應用程式中的資源，您必須釋放資源，立即和可預測的方式。 .NET Framework 可協助您藉由提供執行這項操作`System.IDisposable`介面。 實作的型別`System.IDisposable`具有`System.IDisposable.Dispose`方法，這個方法會正確地釋放資源。 編寫完善的應用程式保證`System.IDisposable.Dispose`持有有限的資源的任何物件已不再需要時立即呼叫。 幸運的是，大部分的.NET 語言會提供支援服務以進行簡化，而 F # 也不例外。 有兩個有用的語言建構，支援的處置模式：`use`繫結和`using`函式。

## <a name="use-binding"></a>使用繫結
`use`關鍵字有類似的形式`let`繫結：

使用*值* = *運算式*

它會提供相同的功能`let`繫結，但將呼叫加入`Dispose`值超出範圍時的值。 請注意，編譯器會插入 null 值時，檢查，因此，如果值會`null`，呼叫`Dispose`未嘗試。

下列範例示範如何使用自動關閉檔案`use`關鍵字。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
您可以使用`use`在計算運算式中，在此情況下的自訂的版本`use`運算式使用。 如需詳細資訊，請參閱[序列](sequences.md)，[非同步工作流程](asynchronous-workflows.md)，和[計算運算式](computation-expressions.md)。


## <a name="using-function"></a>使用函式
`using`函式具有下列格式：

`using` (*expression1*)*函式或 lambda*

在`using`運算式*expression1*建立必須處置的物件。 結果*expression1* （必須處置的物件） 會變成引數，*值*至*函式或 lambda*，這是其中一個必須要有單一的函式其餘的值相符的型別引數所產生的*expression1*，或必須要有該類型的引數的 lambda 運算式。 在執行函式結束時，執行階段會呼叫`Dispose`並釋出資源 (除非值為`null`，在此情況下呼叫 Dispose 就不會嘗試)。

下列範例會示範`using`與 lambda 運算式的運算式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

下一個範例會示範`using`函式具有運算式。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

請注意，函式可能會有一些已套用的引數的函式。 下列程式碼範例示範此工作。 它會建立包含字串的檔案`XYZ`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using`函式和`use`繫結是幾乎相同的方式可以完成相同的動作。 `using`關鍵字，可提供更充分掌控時`Dispose`呼叫。 當您使用`using`，`Dispose`呼叫結尾的函式或 lambda 運算式中，當您使用`use`關鍵字，`Dispose`呼叫包含的程式碼區塊的結尾。 一般情況下，您應該最好使用`use`而不是`using`函式。


## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)
