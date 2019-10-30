---
title: 使用預設介面方法建立 mixin 類型
description: 使用預設介面成員，您可以使用實作者的選擇性預設實作為擴充介面。
ms.technology: csharp-advanced-concepts
ms.date: 10/04/2019
ms.openlocfilehash: 798413f0071159893de39f3e190a9b2693571bb7
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039280"
---
# <a name="tutorial-mix-in-functionality-when-creating-classes-using-interfaces-with-default-interface-methods"></a>教學課程：使用具有預設介面方法的介面建立類別時混用功能

從 C# 8.0 開始，您可以在宣告介面成員時，於 .NET Core 3.0 上定義實作。 這項功能提供新的功能，您可以在其中為介面中宣告的功能定義預設的執行方式。 類別可以挑選何時覆寫功能、何時使用預設功能，以及何時不宣告對離散功能的支援。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> * 使用可描述離散功能的實作為建立介面。
> * 建立使用預設實現的類別。
> * 建立會覆寫部分或全部預設實作為的類別。

## <a name="prerequisites"></a>Prerequisites

您必須設定電腦以執行 .NET Core，包括C# 8.0 編譯器。 C# 8.0 編譯器從[Visual Studio 2019、16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)或[.net Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) （含）以後版本開始提供。

## <a name="limitations-of-extension-methods"></a>擴充方法的限制

有一種方式可以實作為介面的一部分來執行行為，即定義提供預設行為的[擴充方法](../programming-guide/classes-and-structs/extension-methods.md)。 介面會宣告一組最小成員，同時為任何可實作為介面的類別提供更大的表面區域。 例如，<xref:System.Linq.Enumerable> 中的擴充方法會提供任何序列的執行，做為 LINQ 查詢的來源。

擴充方法會在編譯時期解析，並使用變數的宣告型別。 執行介面的類別可以為任何擴充方法提供更好的執行方式。 變數宣告必須符合實類型，才能讓編譯器選擇該執行。 當編譯時間型別符合介面時，方法呼叫會解析成擴充方法。 擴充方法還有另一個考慮，就是可存取包含擴充方法之類別的任何地方都可以存取這些方法。 如果類別不應該或不應該提供在擴充方法中宣告的功能，就無法宣告。

從C# 8.0 開始，您可以將預設的實作為介面方法來宣告。 然後，每個類別都會自動使用預設的實值。 可以提供更好的執行方式的任何類別，都可以使用更好的演算法來覆寫介面方法定義。 就這一點而言，這項技術與您可以使用[擴充方法](../programming-guide/classes-and-structs/extension-methods.md)的方式非常類似。

在本文中，您將瞭解預設介面的實現如何啟用新的案例。

## <a name="design-the-application"></a>設計應用程式

請考慮使用「家庭自動化」應用程式。 您可能會有許多不同類型的光源和指示器，可以在整個房屋中使用。 每個光線都必須支援 Api，才能開啟和關閉這些應用程式，以及報告目前的狀態。 有些光源和指示器可能支援其他功能，例如：

- 開啟 [亮]，然後在計時器之後關閉它。
- 將燈閃爍一段時間。

其中一些擴充功能可以在支援最小設定的裝置上進行模擬。 ，表示提供預設的執行。 對於內建更多功能的裝置，裝置軟體會使用原生功能。 針對其他光源，他們可以選擇執行介面，並使用預設的實作為。

在此案例中，預設介面成員是比擴充方法更好的解決方案。 類別作者可以控制他們選擇要執行的介面。 它們所選擇的介面可以做為方法。 此外，因為預設介面方法是虛擬的，所以方法分派一律會選擇類別中的實值。 

讓我們建立程式碼來示範這些差異。

## <a name="create-interfaces"></a>建立介面

首先建立介面來定義所有光源的行為：

[!code-csharp[Declare base interface](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

基本的額外負荷輕量裝置可能會實作為下列程式碼所示的介面：

[!code-csharp[First overhead light](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

在本教學課程中，程式碼不會驅動 IoT 裝置，而是會藉由將訊息寫入主控台來模擬這些活動。 您可以流覽程式碼，而不需要自動化您的公司。

接下來，我們將定義可在超時時間之後自動關閉的光線介面：

[!code-csharp[pure Timer interface](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

您可以將基本的執行方式新增至額外負荷，但更好的解決方案是修改此介面定義，以提供 `virtual` 的預設實作為方式：

[!code-csharp[Timer interface](~/samples/csharp/tutorials/mixins-with-interfaces/ITimerLight.cs?name=SnippetTimerLightFinal)]

藉由加入該變更，`OverheadLight` 類別可以藉由宣告介面的支援，來實作用計時器函式：

```csharp
public class OverheadLight : ITimerLight { }
```

不同的光源類型可能會支援更複雜的通訊協定。 它可以為 `TurnOnFor` 提供自己的執行，如下列程式碼所示：

[!code-csharp[Override the timer function](~/samples/csharp/tutorials/mixins-with-interfaces/HalogenLight.cs?name=SnippetHalogenLight)]

不同于覆寫虛擬類別方法，`HalogenLight` 類別中的 `TurnOnFor` 宣告不會使用 `override` 關鍵字。 

## <a name="mix-and-match-capabilities"></a>混合和比對功能

當您引進更先進的功能時，預設介面方法的優點會變得更清楚。 使用介面可讓您混合和比對功能。 它也可以讓每個類別作者在預設的執行和自訂執行之間做選擇。 讓我們使用閃爍燈的預設實來新增介面：

[!code-csharp[Define the blinking light interface](~/samples/csharp/tutorials/mixins-with-interfaces/IBlinkingLight.cs?name=SnippetBlinkingLight)]

預設的實值可讓任何光線閃爍。 額外負荷可能會使用預設的實作為新增計時器和閃爍功能：

[!code-csharp[Use the default blink function](~/samples/csharp/tutorials/mixins-with-interfaces/OverheadLight.cs?name=SnippetOverheadLight)]

新的光源類型，`LEDLight` 同時支援計時器函式和閃爍函式。 這個淺色樣式會同時執行 `ITimerLight` 和 `IBlinkingLight` 介面，並覆寫 `Blink` 方法：

[!code-csharp[Override the blink function](~/samples/csharp/tutorials/mixins-with-interfaces/LEDLight.cs?name=SnippetLEDLight)]

`ExtraFancyLight` 可能會直接支援閃爍和計時器函式：

[!code-csharp[Override the blink and timer function](~/samples/csharp/tutorials/mixins-with-interfaces/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

您稍早建立的 `HalogenLight` 不支援閃爍。 因此，請勿將 `IBlinkingLight` 新增至其支援的介面清單。

## <a name="detect-the-light-types-using-pattern-matching"></a>使用模式比對來偵測光源類型

接下來，讓我們撰寫一些測試程式碼。 您可以藉由檢查C#支援的介面，來利用的[模式](../pattern-matching.md)比對功能來判斷光線的功能。  下列方法會練習每個光線支援的功能：

[!code-csharp[Test a light's capabilities](~/samples/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetTestLightFunctions)]

`Main` 方法中的下列程式碼會依序建立每個光源類型，並測試該光線：

[!code-csharp[Test a light's capabilities](~/samples/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a>編譯器如何判斷最佳的執行方式

此案例顯示不含任何執行的基底介面。 將方法新增至 `ILight` 介面會帶來新的複雜性。 管理預設介面方法的語言規則會將對執行多個衍生介面之實體類別的影響降至最低。 讓我們使用新的方法來增強原始介面，以顯示如何變更其使用方式。 每個指示器光線都可以將其電源狀態報表為列舉值：

[!code-csharp[Enumeration for power status](~/samples/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetPowerStatus)]

預設的執行是採用 AC 電源：

[!code-csharp[Report a default power status](~/samples/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetILightInterface)]

這些變更會完全編譯，即使 `ExtraFancyLight` 宣告 `ILight` 介面和衍生介面的支援，`ITimerLight` 和 `IBlinkingLight`。 在 `ILight` 介面中，只會宣告一個「最接近」的實作為。 任何宣告覆寫的類別都會變成一個「最接近」的執行。 您在上述類別中看到的範例會已覆寫其他衍生介面的成員。

避免在多個衍生介面中覆寫相同的方法。 如此一來，每當類別同時執行兩個衍生介面時，就會建立不明確的方法呼叫。 編譯器無法挑選一個更好的方法，因此它會發出錯誤。 例如，如果 `IBlinkingLight` 和 `ITimerLight` 都實作為 `PowerStatus` 的覆寫，`OverheadLight` 就必須提供更明確的覆寫。 否則，編譯器就無法在兩個衍生介面中的執行之間進行選擇。 您通常可以藉由讓介面定義更小且專注于一項功能，來避免這種情況。 在此案例中，每個光線的功能都是它自己的介面;只有類別會繼承多個介面。

這個範例會示範一個案例，您可以在其中定義可以混合成類別的離散功能。 您可以宣告類別支援的介面，以宣告任何一組支援的功能。 使用虛擬預設介面方法，可讓類別針對任何或所有介面方法使用或定義不同的執行。 此語言功能提供新的方法，讓您建立您所打造的真實世界系統模型。 預設介面方法提供更清楚的方式來表達相關的類別，這些類別可能會使用這些功能的虛擬實現來混合和比對不同的功能。
