---
title: 資源管理:Use 關鍵字
description: 瞭解F#關鍵字「使用」和「using」函式, 其可控制資源的初始化和釋放。
ms.date: 05/16/2016
ms.openlocfilehash: 5e0838401bee02050343b2f6dcc646a8dc8b4dc0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627265"
---
# <a name="resource-management-the-use-keyword"></a>資源管理:Use 關鍵字

本主題描述關鍵字`use` `using`和函式, 此函式可以控制資源的初始化和釋放。

## <a name="resources"></a>資源

「*資源*」一詞會以多種方式使用。 是的, 資源可以是應用程式所使用的資料, 例如字串、圖形等等, 但是在此內容中,*資源*指的是軟體或作業系統資源, 例如圖形裝置內容、檔案控制代碼、網路和資料庫。連接、並行物件 (例如等候控制碼等等)。 應用程式使用這些資源牽涉到從作業系統或其他資源提供者取得資源, 然後將較新的資源發行至集區, 以便提供給另一個應用程式。 當應用程式未將資源釋放回通用集區時, 就會發生問題。

## <a name="managing-resources"></a>管理資源

若要有效率地管理應用程式中的資源, 您必須以可預測的方式立即發行資源。 .NET Framework 藉由提供`System.IDisposable`介面來協助您執行這項操作。 執行的類型`System.IDisposable`具有方法, `System.IDisposable.Dispose`可正確地釋出資源。 妥善撰寫的應用程式保證`System.IDisposable.Dispose`當您不再需要持有有限資源的任何物件時, 會立即呼叫。 幸運的是, 大部分的 .NET 語言都提供支援, 讓F#這種情況變得更容易, 而且也不例外。 有兩個實用的語言結構支援 dispose 模式: `use`系結`using`和函式。

## <a name="use-binding"></a>使用系結

關鍵字的形式類似`let`于系結: `use`

使用*值* = *運算式*

它會提供與系結相同`let`的功能, 但會在`Dispose`值超出範圍時, 將對值的呼叫加入。 請注意, 編譯器會在值上插入 null 檢查, 因此如果值為`null`, 則不`Dispose`會嘗試呼叫。

下列範例顯示如何使用`use`關鍵字自動關閉檔案。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

> [!NOTE]
> 您可以在`use`計算運算式中使用, 在此情況下會使用自`use`定義版本的運算式。 如需詳細資訊, 請參閱[序列](sequences.md)、[非同步工作流程](asynchronous-workflows.md)和[計算運算式](computation-expressions.md)。

## <a name="using-function"></a>使用函數

`using`函數的格式如下:

`using`(*運算式*=)*函數或 lambda*

在運算式中, 會建立必須處置的物件。 `using` *運算式*類型的結果 (必須處置的物件) 會變成函*式或 lambda*的引數、*值*, 這是需要符合所產生*之值的另一個型別引數的函數。運算式*型別, 或需要該類型之引數的 lambda 運算式。 在函式執行結束時, 執行時間會呼叫`Dispose`並釋出資源 (除非值為`null`, 在此情況下不會嘗試對 Dispose 進行呼叫)。

下列範例示範具有 lambda `using`運算式的運算式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

下一個範例會顯示`using`具有函數的運算式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

請注意, 函式可能是已套用一些引數的函式。 下列程式碼範例示範此工作。 它會建立包含字串`XYZ`的檔案。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using`函式`use`和系結幾乎等同于完成相同工作的方式。 關鍵字可讓您更充分掌控呼叫的時間`Dispose`。 `using` 當您使用`using`時`Dispose` , 會在函式或 lambda 運算式的結尾呼叫, 而當您使用`use`關鍵字時`Dispose` , 會在包含程式碼區塊的結尾呼叫。 一般來說, 您應該偏好使用`use` , 而不是`using`函式。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
