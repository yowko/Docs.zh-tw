---
title: 使用預設介面方法創建混合類型
description: 使用預設介面成員，您可以擴展具有實現器可選預設實現的介面。
ms.technology: csharp-advanced-concepts
ms.date: 10/04/2019
ms.openlocfilehash: aaf8d34e27c9c56d95560656eb7a7b24b152c053
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240102"
---
# <a name="tutorial-mix-functionality-in-when-creating-classes-using-interfaces-with-default-interface-methods"></a>教程：使用預設介面方法創建類時，在 中混合功能

從 C# 8.0 開始，您可以在宣告介面成員時，於 .NET Core 3.0 上定義實作。 此功能提供了新功能，您可以在其中為介面中聲明的功能定義預設實現。 類可以選擇何時重寫功能、何時使用預設功能以及何時不聲明對離散功能的支援。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> * 創建具有描述離散功能的實現的介面。
> * 創建使用預設實現的類。
> * 創建覆蓋部分或全部預設實現的類。

## <a name="prerequisites"></a>必要條件

您需要設置電腦以運行 .NET Core，包括 C# 8.0 編譯器。 C# 8.0 編譯器可從[Visual Studio 2019 版本 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)或[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core)或更高版本開始。

## <a name="limitations-of-extension-methods"></a>擴充方法的限制

實現作為介面一部分出現的行為的一種方法是定義提供預設行為的[擴充方法](../programming-guide/classes-and-structs/extension-methods.md)。 介面聲明最小成員集，同時為實現該介面的任何類提供更大的表面積。 例如，中的<xref:System.Linq.Enumerable>擴充方法為任何序列提供作為 LINQ 查詢源的實現。

擴充方法在編譯時使用變數的已聲明類型解析。 實現介面的類可以為任何擴充方法提供更好的實現。 變數聲明必須與實現類型匹配，以便編譯器能夠選擇該實現。 當編譯時間類型與介面匹配時，方法調用解析到擴充方法。 擴充方法的另一個問題是，無論包含擴充方法的類是可訪問的，都可以訪問這些方法。 類不能聲明它們是否應提供在擴充方法中聲明的功能。

從 C# 8.0 開始，可以將預設實現聲明為介面方法。 然後，每個類自動使用預設實現。 任何可以提供更好實現的類都可以用更好的演算法覆蓋介面方法定義。 從某種意義上說，這種技術聽起來類似于如何使用[擴充方法](../programming-guide/classes-and-structs/extension-methods.md)。

在本文中，您將瞭解預設介面實現如何啟用新方案。

## <a name="design-the-application"></a>設計應用程式

考慮家庭自動化應用程式。 您可能有許多不同類型的燈光和指示燈，可以在整個房子裡使用。 每個指示燈都必須支援 API 以打開和關閉它們，並報告目前狀態。 某些燈光和指示燈可能支援其他功能，例如：

- 打開燈，然後在計時器後將其關閉。
- 閃爍一段時間的燈。

其中一些擴展功能可以在支援最小集的設備上類比。 指示提供預設實現。 對於內置了更多功能的設備，設備軟體將使用本機功能。 對於其他燈光，他們可以選擇實現介面並使用預設實現。

預設介面成員是此方案比擴充方法更好的解決方案。 類作者可以控制他們選擇實現哪些介面。 他們選擇的介面可以作為方法提供。 此外，由於預設介面方法在預設情況下是虛擬的，因此方法調度始終選擇類中的實現。

讓我們創建代碼來演示這些差異。

## <a name="create-interfaces"></a>創建介面

首先創建定義所有燈光行為的介面：

[!code-csharp[Declare base interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

基本開銷燈具可以實現此介面，如以下代碼所示：

[!code-csharp[First overhead light](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

在本教程中，代碼不會驅動 IoT 設備，而是通過向主控台寫入消息來類比這些活動。 您可以探索代碼，而無需自動執行您的房子。

接下來，讓我們為超時後可自動關閉的燈定義介面：

[!code-csharp[pure Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

您可以將基本實現添加到開銷燈中，但更好的解決方案是修改此介面定義以提供`virtual`預設實現：

[!code-csharp[Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ITimerLight.cs?name=SnippetTimerLightFinal)]

通過添加該更改，`OverheadLight`類可以通過聲明對介面的支援來實現計時器函數：

```csharp
public class OverheadLight : ITimerLight { }
```

不同的光類型可能支援更複雜的協定。 它可以為`TurnOnFor`提供自己的實現，如以下代碼所示：

[!code-csharp[Override the timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/HalogenLight.cs?name=SnippetHalogenLight)]

與重寫虛擬類方法不同，`TurnOnFor``HalogenLight`類 中的聲明不使用 關鍵字。 `override`

## <a name="mix-and-match-capabilities"></a>混合和匹配功能

隨著引入更高級的功能，預設介面方法的優點變得更加清晰。 使用介面使您能夠混合和匹配功能。 它還允許每個類作者在預設實現和自訂實現之間進行選擇。 讓我們為閃爍的燈光添加具有預設實現的介面：

[!code-csharp[Define the blinking light interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/IBlinkingLight.cs?name=SnippetBlinkingLight)]

預設實現允許任何指示燈閃爍。 使用預設實現，頂置指示燈可以同時添加計時器和閃爍功能：

[!code-csharp[Use the default blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/OverheadLight.cs?name=SnippetOverheadLight)]

新的光類型，直接`LEDLight`支援計時器功能和閃爍功能。 此光樣式同時實現`ITimerLight`和`IBlinkingLight`介面，並重寫`Blink`方法：

[!code-csharp[Override the blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/LEDLight.cs?name=SnippetLEDLight)]

可能`ExtraFancyLight`直接支援閃爍和計時器功能：

[!code-csharp[Override the blink and timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

`HalogenLight`您之前創建的不支援閃爍。 因此，不要將 添加到`IBlinkingLight`其支援的介面清單中。

## <a name="detect-the-light-types-using-pattern-matching"></a>使用模式匹配檢測光類型

接下來，讓我們編寫一些測試代碼。 您可以通過檢查其支援的介面來確定 C# 的模式[匹配](../pattern-matching.md)功能來確定燈光的功能。  以下方法執行每個光的支援功能：

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetTestLightFunctions)]

方法`Main`中的以下代碼按順序創建每個光類型，並測試該光：

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a>編譯器如何確定最佳實現

此方案顯示一個基本介面，沒有任何實現。 將方法添加到介面會`ILight`帶來新的複雜性。 管理預設介面方法的語言規則將實現多個派生介面的具體類的影響降至最低。 讓我們用新方法增強原始介面，以顯示如何更改其使用。 每個指示燈都可以將其電源狀態報表為枚舉值：

[!code-csharp[Enumeration for power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetPowerStatus)]

預設實現假定交流電源：

[!code-csharp[Report a default power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetILightInterface)]

這些更改`ExtraFancyLight`編譯乾淨，即使 聲明支援`ILight`介面和派生介面和`ITimerLight``IBlinkingLight`。 `ILight`介面中只聲明瞭一個"最近"實現。 任何聲明重寫的類都將成為"最接近"的實現。 您看到前面的類中的示例超過了其他派生介面的成員。

避免在多個派生介面中重寫相同的方法。 這樣做會在類實現兩個派生介面時創建不明確的方法調用。 編譯器無法選擇一種更好的方法，因此會發出錯誤。 例如，如果`IBlinkingLight`和`ITimerLight`都實現了 對`PowerStatus`的重寫`OverheadLight`，則需要提供更具體的重寫。 否則，編譯器無法在兩個派生介面中的實現之間進行選擇。 通常可以通過保持介面定義小而專注于一個功能來避免這種情況。 在這種情況下，光的每個功能都是它自己的介面;多個介面僅由類繼承。

此示例顯示了一個方案，您可以在其中定義可混合到類中的離散要素。 通過聲明類支援的介面來聲明任何受支援的功能集。 使用虛擬預設介面方法使類能夠為任何或所有介面方法使用或定義不同的實現。 這種語言功能為構建的真實系統提供了建模的新方法。 預設介面方法提供了一種更清晰的方式來表達使用這些功能的虛擬實現混合和匹配不同功能的相關類。
