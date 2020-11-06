---
title: '使用物件中的模式-c # 教學課程'
description: 本教學課程會教您如何在類別成員中使用模式比對來為物件行為建立更好的模型
ms.date: 11/05/2020
ms.openlocfilehash: 072f6f57696504c2d691473e3a43c1cda53f227f
ms.sourcegitcommit: 6bef8abde346c59771a35f4f76bf037ff61c5ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2020
ms.locfileid: "94332186"
---
# <a name="use-pattern-matching-to-build-your-class-behavior-for-better-code"></a>使用模式比對來建立您的類別行為，以取得更好的程式碼

C # 中的模式比對功能提供表達演算法的語法。 您可以使用這些技術來執行類別中的行為。 您可以將物件導向的類別設計與資料導向的實作為結合，以提供簡潔的程式碼，同時為真實世界的物件建立模型。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> - 使用資料模式表達您的面向物件類別。
> - 使用 c # 的模式比對功能來執行這些模式。
> - 利用編譯器診斷來驗證您的執行。

## <a name="prerequisites"></a>必要條件

您必須設定電腦以執行 .NET 5，包括 c # 9.0 編譯器。 從 [Visual Studio 2019 16.8 版 preview](https://visualstudio.microsoft.com/vs/preview/) 或 [.net 5.0 SDK preview](https://dotnet.microsoft.com/download/dotnet/5.0)開始，可以使用 c # 9.0 編譯器。

## <a name="build-a-simulation-of-a-canal-lock"></a>建立 canal 鎖定的模擬

在本教學課程中，您將建立模擬 [canal 鎖定](https://en.wikipedia.org/wiki/Lock_(water_navigation))的 c # 類別。 簡單來說，canal 鎖定是一種裝置，可在兩個不同層級的兩個水伸展之間移動時，引發並降低 boats。 鎖定有兩個閘道和一些機制來變更水等級。

在其正常作業中，船會進入其中一個閘道，而鎖定中的水層級則會與船輸入的一端上的水等級相符。 一旦進入鎖定，就會變更水位線，使其符合當船會離開鎖定的水。 當水等級符合該端時，就會開啟結束端的閘道。 安全措施可確保操作員無法在 canal 中建立危險的情況。 只有當兩個閘道都關閉時，才可以變更水源層級。 最多可以開啟一個閘道。 若要開啟閘道，鎖定中的水等級必須符合開啟閘道以外的水。

您可以建立 c # 類別來建立此行為的模型。 `CanalLock`類別會支援開啟或關閉任一個閘道的命令。 它會有其他命令來提高或降低水位線。 類別也應支援屬性，以讀取閘道和水等級的目前狀態。 您的方法會執行安全措施。

## <a name="define-a-class"></a>定義類別

您將建立主控台應用程式來測試您的 `CanalLock` 類別。 使用 Visual Studio 或 .NET CLI 建立適用于 .NET 5 的新主控台專案。 然後，新增類別並將其命名為 `CanalLock` 。 接下來，請設計您的公用 API，但不要執行這些方法：

:::code language="csharp" source="snippets/pattern-objects/InterimSteps.cs" ID="APIDesign":::

上述程式碼會初始化物件，因此會關閉這兩個閘道，而水層級則是低。 接下來，在您的方法中撰寫下列測試程式碼， `Main` 以引導您建立類別的第一個實作為：

:::code language="csharp" source="snippets/pattern-objects/Program.cs" ID="HappyTests":::

接下來，在類別中新增每個方法的第一個實作為 `CanalLock` 。 下列程式碼會執行類別的方法，而不會考慮安全性規則。 您稍後將會新增安全性測試：

:::code language="csharp" source="snippets/pattern-objects/InterimSteps.cs" ID="FirstImplementation":::

您到目前為止所撰寫的測試已通過。 您已實現基本概念。 現在，撰寫第一個失敗狀況的測試。 在先前的測試結束時，這兩個閘道都已關閉，而水層級設定為 [低]。 新增測試以嘗試開啟上層閘道：

:::code language="csharp" source="snippets/pattern-objects/Program.cs" ID="HighGateSafetyTest":::

此測試失敗，因為閘道開啟。 在第一次執行時，您可以使用下列程式碼來修正此問題：

:::code language="csharp" source="snippets/pattern-objects/InterimSteps.cs" ID="SecondImplementation":::

您的測試通過。 但是，當您新增更多測試時，將會新增更多和更多的 `if` 子句，並測試不同的屬性。 當您新增更多條件時，這些方法很快就會變得太複雜。

## <a name="implement-the-commands-with-patterns"></a>使用模式來執行命令

更好的方法是使用 *模式* 來判斷物件是否處於有效的狀態，以執行命令。 您可以表達是否允許命令為三個變數的函式：閘道的狀態、水的等級，以及新的設定：

| 新增設定 | 閘道狀態 | 水等級 | 結果             |
| ----------- | ---------- | ----------- | ------------------ |
| 關閉      | 關閉     | 高        | 關閉             |
| 關閉      | 關閉     | 低         | 關閉             |
| 關閉      | 開啟       | 高        | 開啟               |
| ~~已關閉~~  | ~~開啟~~   | ~~低~~     | ~~已關閉~~         |
| 開啟        | 已關閉     | 高        | 開啟               |
| 開啟        | 已關閉     | 低         | 關閉 (錯誤)      |
| 開啟        | 開啟       | 高        | 開啟               |
| ~~開啟~~    | ~~開啟~~   | ~~低~~     | ~~關閉 (錯誤) ~~ |

資料表中的第四個數據列和最後一個資料列的文字是不正確。 現在您要加入的程式碼應該要確定當水偏低時，不會開啟高水位閘道。  您可以將這些狀態編碼為單一 switch 運算式 (記得表示「 `false` 已關閉」 ) ：

:::code language="csharp" source="snippets/pattern-objects/InterimSteps.cs" ID="ThirdImplementation":::

請嘗試此版本。 您的測試會通過，並驗證程式代碼。 完整的表格會顯示輸入和結果的可能組合。 這表示您和其他開發人員可以快速查看表格，並看到您已涵蓋所有可能的輸入。 更簡單的一點是，編譯器也可以提供協助。 加入先前的程式碼之後，您可以看到編譯器產生警告： *CS8524* 指出 switch 運算式未涵蓋所有可能的輸入。 警告的原因是其中一個輸入是 `enum` 類型。 編譯器會將「所有可能的輸入」解讀為基礎類型的所有輸入，通常是 `int` 。 此 `switch` 運算式只會檢查中宣告的值 `enum` 。 若要移除警告，您可以為運算式的最後一個 arm 加入 catch 全部捨棄模式。 此條件會擲回例外狀況，因為它指出不正確輸入：

```csharp
_  => throw new InvalidOperationException("Invalid internal state"),
```

先前的 switch arm 必須是運算式中的最後一個參數， `switch` 因為它符合所有輸入。 依序移至先前的順序來進行實驗。 這會導致編譯器錯誤 *CS8510* 模式中無法連接的程式碼。  Switch 運算式的自然結構可讓編譯器針對可能的錯誤產生錯誤和警告。 編譯器「安全網路」可讓您更輕鬆地以較少的反復專案建立正確的程式碼，並可自由地結合 switch 臂與萬用字元。 如果您的組合導致您未預期的無法連線，則編譯器會發出錯誤，如果您移除需要的 arm，則會發出警告。

第一項變更是合併命令要關閉閘道的所有 arm;一律允許。 將下列程式碼新增為 switch 運算式中的第一個 arm：

```csharp
(false, _, _) => false,
```

在您新增先前的交換器 arm 之後，您將會收到四個編譯器錯誤，命令的每個 arm 各有一個錯誤 `false` 。 剛新增的 arm 已涵蓋這些 arm。 您可以安全地移除這四行。 您打算這個新的交換器 arm 來取代這些條件。

接下來，您可以簡化這四個 arm，命令是用來開啟閘道。 在這兩種情況下，您可以開啟閘道。  (其中一個已開啟 ) 。當水等級為低的情況下，會擲回例外狀況，而另一種情況則不應發生。 如果水位鎖已處於無效狀態，則應該安全地擲回相同的例外狀況。 您可以針對這些 arm 進行下列簡化：

```csharp
(true, _, WaterLevel.High) => true,
(true, false, WaterLevel.Low) => throw new InvalidOperationException("Cannot open high gate when the water is low"),
_ => throw new InvalidOperationException("Invalid internal state"),
```

再次執行您的測試，並通過測試。 以下是方法的最終版本 `SetHighGate` ：

:::code language="csharp" source="snippets/pattern-objects/CanalLock.cs" ID="FinalImplementaton":::

## <a name="implement-patterns-yourself"></a>自行執行模式

現在您已瞭解此技巧，請 `SetLowGate` 自行填入和 `SetWaterLevel` 方法。  首先，新增下列程式碼來測試這些方法的無效作業：

:::code language="csharp" source="snippets/pattern-objects/Program.cs" ID="FinalTestCode":::

重新執行您的應用程式。 您可以看到新的測試失敗，而且 canal 鎖定會進入不正確狀態。 嘗試自行執行其餘的方法。 設定下層閘道的方法應該類似于設定上層閘道的方法。 變更水層級的方法具有不同的檢查，但應遵循類似的結構。 您可能會發現對設定水層級的方法使用相同的程式很有用。 從四個輸入開始：兩個閘道的狀態、水線層級的目前狀態，以及要求的新水等級。 Switch 運算式的開頭應該是：

```csharp
CanalLockWaterLevel = (newLevel, CanalLockWaterLevel, LowWaterGateOpen, HighWaterGateOpen) switch
{
    // elided
};
```

您將有16個切換 arm 來填寫。 然後，測試並簡化。

您是否有像這樣的方法？

:::code language="csharp" source="snippets/pattern-objects/CanalLock.cs" ID="FinalExercise":::

您的測試應該會通過，而且 canal 鎖定應該安全地運作。

## <a name="summary"></a>摘要

在本教學課程中，您已瞭解如何使用模式比對來檢查物件的內部狀態，然後再將任何變更套用至該狀態。 您可以檢查屬性的組合。 一旦為這些轉換建立資料表之後，您就可以測試程式碼，然後簡化可讀性和維護性。 這些初始重構可能會建議進一步的重構，以驗證內部狀態或管理其他 API 變更。 本教學課程結合了類別和物件與以資料為導向，以模式為基礎的方法來執行這些類別。
