---
title: 適用於 Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Windows Store apps, .NET Framework support for
- Windows Runtime, .NET Framework support for
- .NET for Windows Store apps
- .NET Framework, and Windows Store apps
- .NET Framework, and Windows Runtime
ms.assetid: 6fa7d044-ae12-4c54-b8ee-50915607a565
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2f46d21123ecfda4bd336edbbd79fabf01e002a4
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835334"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>適用於 Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援

.NET Framework 4.5 支援多個具有 Windows 執行階段的軟體發展案例。 這些案例可分成三個類別︰

- 如[使用C#或 Visual Basic 的 windows Store 應用程式藍圖](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))中所述，利用 XAML 控制項開發 @no__t 0 應用程式， [windows store 應用程式的](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))[如何（XAML）](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))和 .net 的總覽。

- 開發類別庫，在使用 .NET Framework 建立的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式中使用。

- 開發 Windows 執行階段元件，封裝在中。WinMD 檔案，可供支援 Windows 執行階段的任何程式設計語言使用。 例如，請參閱[在和 Visual Basic 中C#建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)。

本主題概述 .NET Framework 提供給這三個類別的支援，並說明 Windows 執行階段元件的案例。 第一節包含有關 .NET Framework 與 Windows 執行階段之間關聯性的基本資訊，並說明您可能會在協助系統和 IDE 中遇到的一些奇觀。 [第二個章節](#WindowsRuntimeComponents)討論開發 Windows 執行階段元件的案例。

## <a name="the-basics"></a>基本概念

.NET Framework 藉由提供 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]，以及支援 Windows 執行階段本身，來支援先前所列的三種開發案例。

- [.NET Framework 和 Windows 執行階段命名空間](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces)可讓您更有效率地看到 .NET Framework 類別庫，並僅包含您可以用來建立 @no__t 1 應用程式和 Windows 執行階段元件的類型和成員。

  - 當您使用 Visual Studio （Visual Studio 2012 或更新版本）開發 @no__t 0 應用程式或 Windows 執行階段元件時，一組參考元件可確保您只會看到相關的類型和成員。

  - 藉由移除在 .NET Framework 內重複的功能，或重複的 Windows 執行階段功能，可進一步簡化此簡化的 API 集。 例如，它只包含集合類型的泛型版本，而 XML 檔物件模型則會排除 Windows 執行階段 XML API 集。

  - 簡單地包裝作業系統 API 的功能也會移除，因為 Windows 執行階段很容易就能從 managed 程式碼呼叫。

  若要深入瞭解 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]，請參閱[適用于 Windows Store 應用程式的 .net 總覽](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))。 若要閱讀 API 選取程式的相關資訊，請參閱 .NET blog 中的[適用于 Metro 樣式應用程式的 .net](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/)專案。

- [Windows 執行階段](/uwp/api/)提供用來建立 @no__t 1 應用程式的使用者介面元素，並提供作業系統功能的存取權。 如同 .NET Framework，Windows 執行階段的中繼資料可讓C#和 Visual Basic 編譯器使用 .NET Framework 類別庫的 Windows 執行階段方式。 .NET Framework 藉由隱藏一些差異，讓您更輕鬆地使用 Windows 執行階段：

  - .NET Framework 和 Windows 執行階段之間的程式設計模式有一些差異，例如新增和移除事件處理常式的模式，則會隱藏起來。 您僅需使用 .NET Framework 模式。

  - 常用類型 (例如基本類型和集合) 中的差異，即會予以隱藏。 您只需使用 .NET Framework 類型，如本文稍後[的 IDE 中可見的差異](#DifferencesVisibleInIDE)中所述。

大部分的情況下，.NET Framework Windows 執行階段的支援都是透明的。 下一節將討論 managed 程式碼與 Windows 執行階段之間的一些明顯差異。

<a name="AboutReferenceDocumentation"></a>

### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>.NET Framework 和 Windows 執行階段參考檔

Windows 執行階段和 .NET Framework 檔集是分開的。 如果您按下 F1 鍵顯示類型或成員的 [說明]，則會顯示適當集合的參考文件。 不過，如果您流覽[Windows 執行階段參考](/uwp/api/)，您可能會遇到看起來令人困惑的範例：

- @No__t-0 介面之類的主題沒有 Visual Basic 或C#的宣告語法。 相反地，附注會出現在語法區段的上方（在此案例中為「.NET：這個介面會顯示為 System.object @ no__t-0T > "）。 這是因為 .NET Framework 和 Windows 執行階段會提供具有不同介面的類似功能。 此外，還有行為的差異︰`IIterable` 採用 `First` 方法，而不是 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法傳回列舉值。 .NET Framework 不會強迫您學習不同的方式來執行一般工作，而是讓您的 managed 程式碼看起來使用您熟悉的型別，藉此支援 Windows 執行階段。 您不會在 IDE 中看到 @no__t 0 介面，因此您在 Windows 執行階段參考檔中遇到的唯一方法，就是直接流覽該檔。

- @No__t-0 檔說明密切相關的問題：針對不同的語言，其參數類型看起來會不同。 若為 C# 和 Visual Basic，參數類型為 <xref:System.String?displayProperty=nameWithType> 和 <xref:System.Uri?displayProperty=nameWithType>。 同樣地，這是因為 .NET Framework 有自己的 `String` 和 `Uri` 類型，而針對這類常用類型，強制 .NET Framework 使用者了解其他執行工作的方式並不合理。 在 IDE 中，.NET Framework 會隱藏對應的 Windows 執行階段類型。

- 在少數情況下，例如 <xref:Windows.UI.Xaml.GridLength> 結構，.NET Framework 提供具有相同名稱但具有更多功能的類型。 例如，建構函式和屬性的主題集與 `GridLength`相關聯，但它們只有適用於 Visual Basic 和 C# 的語法區塊，這是因為成員僅適用於 Managed 程式碼。 在 Windows 執行階段中，結構只有欄位。 Windows 執行階段結構需要 helper 類別，<xref:Windows.UI.Xaml.GridLengthHelper>，才能提供對等的功能。 您不會在撰寫 Managed 程式碼時，於 IDE 中看到該協助程式類別。

- 在 IDE 中，Windows 執行階段類型似乎衍生自 <xref:System.Object?displayProperty=nameWithType>。 它們似乎具有繼承自 <xref:System.Object>，例如 <xref:System.Object.ToString%2A?displayProperty=nameWithType>。 這些成員的運作方式與實際繼承自 <xref:System.Object> 的類型相同，而且 Windows 執行階段類型可以轉換成 <xref:System.Object>。 這項功能屬於 .NET Framework 為 Windows 執行階段提供的支援。 不過，如果您在 Windows 執行階段參考檔中查看類型，則不會顯示這類成員。 這些明顯繼承成員的文件由 <xref:System.Object?displayProperty=nameWithType> 參考文件提供。

<a name="DifferencesVisibleInIDE"></a>

### <a name="differences-that-are-visible-in-the-ide"></a>IDE 中可見的差異

在更先進的程式設計案例中，例如使用在中C#撰寫的 Windows 執行階段元件，為使用 JavaScript 為 Windows 建立的 @no__t 1 應用程式提供應用程式邏輯，這類差異在 IDE 和檔中都很明顯。 當您的元件傳回 `IDictionary<int, string>` 至 JavaScript，而您在 JavaScript 偵錯工具中查看時，您會看到 `IMap<int, string>` 的方法，因為 JavaScript 會使用 Windows 執行階段類型。 下表顯示一些常用的集合類型，其會在兩種語言中以不同的方式出現︰

|Windows 執行階段類型|對應的 .NET Framework 類型|
|--------------------------------------------------------------|---------------------------------------|
|`IIterable<T>`|`IEnumerable<T>`|
|`IIterator<T>`|`IEnumerator<T>`|
|`IVector<T>`|`IList<T>`|
|`IVectorView<T>`|`IReadOnlyList<T>`|
|`IMap<K, V>`|`IDictionary<TKey, TValue>`|
|`IMapView<K, V>`|`IReadOnlyDictionary<TKey, TValue>`|
|`IBindableIterable`|`IEnumerable`|
|`IBindableVector`|`IList`|
|`Windows.UI.Xaml.Data.INotifyPropertyChanged`|`System.ComponentModel.INotifyPropertyChanged`|
|`Windows.UI.Xaml.Data.PropertyChangedEventHandler`|`System.ComponentModel.PropertyChangedEventHandler`|
|`Windows.UI.Xaml.Data.PropertyChangedEventArgs`|`System.ComponentModel.PropertyChangedEventArgs`|

在 Windows 執行階段中，`IMap<K, V>` 和 `IMapView<K, V>` 會使用 `IKeyValuePair` 進行反覆運算。 當您將其傳遞至 Managed 程式碼時，它們會顯示成 `IDictionary<TKey, TValue>` 與 `IReadOnlyDictionary<TKey, TValue>`，以便您使用 `System.Collections.Generic.KeyValuePair<TKey, TValue>` 加以列舉。

介面在 Managed 程式碼中的顯示方式，會影響到實作這些介面之型别的顯示方式。 例如　`PropertySet` 類別會實作 `IMap<K, V>`，而這在 Managed 程式碼中會顯示為 `IDictionary<TKey, TValue>`。 `PropertySet` 會以實作了 `IDictionary<TKey, TValue>` (而不是 `IMap<K, V>`) 的形態出現，因此在 Managed 程式碼中，其看似具有 `Add` 方法 (此方法的行為類似於 .NET Framework 字典上的 `Add` 方法。 它看起來並沒有 `Insert` 方法。

如需使用 .NET Framework 建立 Windows 執行階段元件的詳細資訊，以及示範如何搭配使用這類元件與 JavaScript 的逐步解說，請參閱[在和 Visual Basic 中C#建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)。

### <a name="primitive-types"></a>基本類型

若要在 managed 程式碼中啟用 Windows 執行階段的自然用法，.NET Framework 基本型別會出現，而不是在程式碼中 Windows 執行階段基本型別的類型。 在 .NET Framework 中，基本型别 (如 `Int32` 結構) 具有許多有用的屬性和方法，例如 `Int32.TryParse` 方法。 相較之下，Windows 執行階段中的基本型別和結構只有欄位。 在 Managed 程式碼中使用基本項目時，將會顯示成 .NET Framework 類型，而您可以如常使用這些 .NET Framework 類型的屬性和方法。 下列清單提供摘要︰

- 針對 Windows 執行階段基本型 `Int32`、`Int64`、`Single`、`Double`、`Boolean`、`String` （Unicode 字元的不可變集合）、`Enum`、`UInt32`、`UInt64` 和 `Guid`，請在 0 命名空間中使用相同名稱的類型。

- 對於 `UInt8`，請使用 `System.Byte`。

- 對於 `Char16`，請使用 `System.Char`。

- 對於 `IInspectable` 介面，請使用 `System.Object`。

- 若為 `HRESULT`，搭配使用結構與一個 `System.Int32` 成員。

如同介面類別型，只有當您的 .NET Framework 專案是使用 JavaScript 建立的 @no__t 0 應用程式所使用的 Windows 執行階段元件時，您才會看到此標記法的辨識項。

其他在 managed 程式碼中顯示為其 .NET Framework 對等專案的基本常用 Windows 執行階段類型，包括 `Windows.Foundation.DateTime` 結構，這會在 managed 程式碼中顯示為 @no__t 1 結構，而 `Windows.Foundation.TimeSpan` 結構則會顯示為 <xref:System.TimeSpan?displayProperty=nameWithType>表示.

### <a name="other-differences"></a>其他差異

在少數情況下，.NET Framework 類型會出現在您的程式碼中，而不是 Windows 執行階段類型需要您採取動作。 例如，<xref:Windows.Foundation.Uri?displayProperty=nameWithType> 類別在 .NET Framework 程式碼中會顯示為 <xref:System.Uri?displayProperty=nameWithType>。 <xref:System.Uri?displayProperty=nameWithType> 允許相對 URI，但 <xref:Windows.Foundation.Uri?displayProperty=nameWithType> 需要絕對 URI。 因此，當您將 URI 傳遞至 Windows 執行階段方法時，您必須確定它是絕對的。 請參閱將[URI 傳遞給 Windows 執行階段](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)。

<a name="WindowsRuntimeComponents"></a>

## <a name="scenarios-for-developing-windows-runtime-components"></a>開發 Windows 執行階段元件的案例

受管理 Windows 執行階段元件支援的案例取決於下列一般原則：

- 使用 .NET Framework 建立 Windows 執行階段元件，與其他 Windows Runtimelibraries 沒有明顯的差異。 例如，如果您使用 managed 程式碼重新執行原生 Windows 執行階段元件，則這兩個元件外表無法區分。 使用您元件的程式碼不會察覺到該元件是以 Managed 程式碼撰寫，即使該程式碼本身為 Managed 程式碼亦然。 但在內部中，您的元件是實際的 Managed 程式碼且會在通用語言執行平台 (CLR) 上執行。

- 元件所包含的類型可實作應用程式邏輯、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI 控制項，或同時實作兩者。

  > [!NOTE]
  > 將 UI 項目與應用程式邏輯分開是很好的做法。 此外，您無法在使用 JavaScript 和 HTML 建置且適用於 Windows 的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式中，使用 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI 控制項。

- 元件可以是 Visual Studio 解決方案中適用於 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式的專案，或是可新增至多個解決方案的可重複使用元件。

  > [!NOTE]
  > 如果您的元件只會搭配C#或 Visual Basic 使用，則不需要讓它成為 Windows 執行階段元件。 如果您將它設為一般 .NET Framework Class Library，就不需要將其公用 API 介面限制為 Windows 執行階段類型。

- 您可以藉由使用 Windows 執行階段 <xref:Windows.Foundation.Metadata.VersionAttribute> 屬性來發行可重複使用元件的版本，以識別不同版本中新增了哪些類型（以及類型中的哪些成員）。

- 元件中的類型可以衍生自 Windows 執行階段類型。 控制項可以衍生自 <xref:Windows.UI.Xaml.Controls.Primitives> 命名空間中的基本控制項類型，或從更多完成的控制項（例如 <xref:Windows.UI.Xaml.Controls.Button>）。

  > [!IMPORTANT]
  > 從 [!INCLUDE[win8](../../../includes/win8-md.md)] 開始，.NET Framework 4.5，managed Windows 執行階段元件中的所有公用類型都必須密封。 另一個 Windows 執行階段元件中的類型無法衍生自它們。 如果您想要在元件中提供多型行為，您可以建立介面並在多型類型中加以實作。

- 元件中公用類型上的所有參數和傳回類型，都必須是 Windows 執行階段類型（包括元件所定義的 Windows 執行階段類型）。

下列各節提供常見案例的範例。

### <a name="application-logic-for-a-includewin8_appname_longincludeswin8-appname-long-mdmd-app-with-javascript"></a>[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式的應用程式邏輯與 JavaScript

當您使用 JavaScript 為 Windows 開發 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式時，您可能會發現應用程式邏輯的某些部分在 Managed 程式碼中，有較佳的效能或較容易開發。 JavaScript 不能直接使用 .NET Framework 類別庫，但是您可以將類別庫作為 .WinMD 檔案。 在此案例中，Windows 執行階段元件是應用程式不可或缺的一部分，所以提供版本屬性並沒有意義。

### <a name="reusable-includewin8_appname_longincludeswin8-appname-long-mdmd-ui-controls"></a>可重複使用的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI 控制項

您可以在可重複使用的 Windows 執行階段元件中封裝一組相關的 UI 控制項。 元件可以自我行銷，或作為您建立之應用程式中的項目。 在此案例中，使用 Windows 執行階段 <xref:Windows.Foundation.Metadata.VersionAttribute> 屬性來改善相容性是合理的。

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>來自現有 .NET Framework 應用程式的可重複使用應用程式邏輯

您可以將現有桌面應用程式中的受控碼封裝為獨立 Windows 執行階段元件。 這可讓您將元件用於使用 C++ 或 JavaScrip 所建置的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式，以及使用 C# 或 Visual Basic 所建置的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式。 如果程式碼有多個重複使用的案例，也可選擇進行版本控制。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[適用於 Windows 市集應用程式的 .NET 概觀](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|說明您可以用來建立 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式和 Windows RuntimeComponents 的 .NET Framework 類型和成員。 (在 Windows 開發人員中心中。)|
|[使用C#或 Visual Basic 的 Windows Store 應用程式藍圖](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|提供重要資源，協助您使用 C# 或 Visual Basic 開始開發 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式，包括許多快速入門主題、指導方針和最佳做法。 (在 Windows 開發人員中心中。)|
|[How to （XAML）](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|提供重要資源，協助您使用 C# 或 Visual Basic 開始開發 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式，包括許多快速入門主題、指導方針和最佳做法。 (在 Windows 開發人員中心中。)|
|[在 C++ 和 Visual Basic 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|說明如何使用 .NET Framework 建立 Windows 執行階段元件、說明如何將它當做使用 JavaScript 為 Windows 建立之 @no__t 0 應用程式的一部分，並說明如何使用 Visual Studio 來進行合併。 (在 Windows 開發人員中心中。)|
|[Windows 執行階段參考](/uwp/api/)|Windows 執行階段的參考檔。 (在 Windows 開發人員中心中。)|
|[將 URI 傳遞給 Windows 執行階段](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|描述當您將 URI 從 managed 程式碼傳遞至 Windows 執行階段時可能發生的問題，以及如何避免此錯誤。|
