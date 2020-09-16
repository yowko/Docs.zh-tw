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
ms.openlocfilehash: 2d1b35181f508a616ab264c859119da7512e5f23
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547567"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>適用於 Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援

.NET Framework 4.5 以 Windows 執行階段支援多種軟體發展案例。 這些案例可分成三個類別︰

- [使用 c # 或 Visual Basic 來](/previous-versions/windows/apps/br229583(v=win.10))開發 Windows 8. x 儲存應用程式（如 windows store 應用程式的藍圖所述）、[如何 (XAML) ](/previous-versions/windows/apps/br229566(v=win.10))和[適用于 windows store 應用程式的 .net 總覽](/previous-versions/windows/apps/br230302(v=vs.140))。

- 開發類別庫，以在您使用 .NET Framework 建立的 Windows 8. x 商店應用程式中使用。

- 開發封裝在中的 Windows 執行階段元件。WinMD 檔案，可供任何支援 Windows 執行階段的程式設計語言使用。 例如，請參閱 [在 c # 和 Visual Basic 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)。

本主題將概述 .NET Framework 針對這三種類別提供的支援，並說明 Windows 執行階段元件的案例。 第一個區段包含 .NET Framework 與 Windows 執行階段之間關聯性的基本資訊，並說明您可能會在說明系統和 IDE 中遇到的一些奇觀。 [第二節](#WindowsRuntimeComponents)討論開發 Windows 執行階段元件的案例。

## <a name="the-basics"></a>基本概念

.NET Framework 藉由提供適用于 Windows 8 x 存放區應用程式的 .NET，以及支援 Windows 執行階段本身，來支援先前所列的三種開發案例。

- [.NET Framework 和 Windows 執行階段命名空間](/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces) 提供 .NET Framework 類別庫的簡化觀點，並且只包含您可以用來建立 Windows 8. x 儲存區應用程式和 Windows 執行階段元件的類型和成員。

  - 當您使用 Visual Studio (Visual Studio 2012 或更新版本) 開發 Windows 8. x 存放區應用程式或 Windows 執行階段元件時，一組參考元件可確保您只會看到相關的類型和成員。

  - 這項簡化的 API 集會藉由移除 .NET Framework 內重複的功能，或重複的 Windows 執行階段功能來簡化。 例如，它僅包含集合類型的泛型版本，而 XML 檔物件模型則會被排除，以利 Windows 執行階段 XML API 集。

  - 也會移除單純包裝作業系統 API 的功能，因為 Windows 執行階段很容易從 managed 程式碼呼叫。

  若要深入瞭解適用于 Windows 8. x Store 應用程式的 .NET，請參閱 [適用于 Windows store 應用程式的 .net 總覽](/previous-versions/windows/apps/br230302(v=vs.140))。 若要閱讀有關 API 選擇程式的資訊，請參閱 .NET blog 中的 [適用于 Metro 樣式應用程式的 .net](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) 專案。

- [Windows 執行階段](/uwp/api/)提供用來建立 Windows 8. x 存放區應用程式的使用者介面元素，並提供作業系統功能的存取權。 就像 .NET Framework 一樣，Windows 執行階段具有中繼資料，可讓 c # 和 Visual Basic 編譯器使用 Windows 執行階段使用 .NET Framework 類別庫的方式。 .NET Framework 藉由隱藏一些差異，讓您更輕鬆地使用 Windows 執行階段：

  - .NET Framework 和 Windows 執行階段之間的程式設計模式有一些差異，例如新增和移除事件處理常式的模式都是隱藏的。 您僅需使用 .NET Framework 模式。

  - 常用類型 (例如基本類型和集合) 中的差異，即會予以隱藏。 您只需使用 .NET Framework 類型，如本文稍後 [的 IDE 中可見的差異](#DifferencesVisibleInIDE)所述。

大部分的情況下，.NET Framework 對 Windows 執行階段的支援是透明的。 下一節將討論 managed 程式碼與 Windows 執行階段之間的一些明顯差異。

<a name="AboutReferenceDocumentation"></a>

### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>.NET Framework 和 Windows 執行階段參考檔

Windows 執行階段和 .NET Framework 的檔集是分開的。 如果您按下 F1 鍵顯示類型或成員的 [說明]，則會顯示適當集合的參考文件。 但是，如果您流覽 [Windows 執行階段參考](/uwp/api/) ，您可能會遇到看似令人困惑的範例：

- 介面等主題 <xref:Windows.Foundation.Collections.IIterable%601> 沒有 Visual Basic 或 c # 的宣告語法。 相反地，附注會出現在語法區段的上方 (在此案例中為「.NET：此介面會顯示為 System.object」 \<T> ) 。 這是因為 .NET Framework 和 Windows 執行階段會提供與不同介面相同的功能。 此外，還有行為的差異︰`IIterable` 採用 `First` 方法，而不是 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法傳回列舉值。 .NET Framework 藉由將您的 managed 程式碼顯示為使用您熟悉的類型，而不是強迫您學習不同的方式來執行常見的工作，支援 Windows 執行階段。 您將不會 `IIterable` 在 IDE 中看到介面，因此您在 Windows 執行階段參考檔中遇到的唯一方法，就是直接流覽該檔。

- 本 <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)> 檔說明一個密切相關的問題：其參數類型對不同的語言而言看起來不同。 若為 C# 和 Visual Basic，參數類型為 <xref:System.String?displayProperty=nameWithType> 和 <xref:System.Uri?displayProperty=nameWithType>。 同樣地，這是因為 .NET Framework 有自己的 `String` 和 `Uri` 類型，而針對這類常用類型，強制 .NET Framework 使用者了解其他執行工作的方式並不合理。 在 IDE 中，.NET Framework 會隱藏對應的 Windows 執行階段類型。

- 在某些情況下（例如 <xref:Windows.UI.Xaml.GridLength> 結構），.NET Framework 會提供名稱相同但功能更多的型別。 例如，建構函式和屬性的主題集與 `GridLength`相關聯，但它們只有適用於 Visual Basic 和 C# 的語法區塊，這是因為成員僅適用於 Managed 程式碼。 在 Windows 執行階段中，結構只有欄位。 Windows 執行階段結構需要 helper 類別， <xref:Windows.UI.Xaml.GridLengthHelper> 才能提供對等的功能。 您不會在撰寫 Managed 程式碼時，於 IDE 中看到該協助程式類別。

- 在 IDE 中，Windows 執行階段類型會顯示為衍生自 <xref:System.Object?displayProperty=nameWithType> 。 它們似乎具有繼承自 <xref:System.Object>，例如 <xref:System.Object.ToString%2A?displayProperty=nameWithType>。 這些成員的運作方式就像是實際繼承自的型別 <xref:System.Object> ，而且 Windows 執行階段類型可以轉換成 <xref:System.Object> 。 這項功能屬於 .NET Framework 針對 Windows 執行階段所提供的支援。 但是，如果您在 Windows 執行階段參考檔中查看類型，則不會出現這類成員。 這些明顯繼承成員的文件由 <xref:System.Object?displayProperty=nameWithType> 參考文件提供。

<a name="DifferencesVisibleInIDE"></a>

### <a name="differences-that-are-visible-in-the-ide"></a>IDE 中可見的差異

在更先進的程式設計案例中，例如使用以 c # 撰寫的 Windows 執行階段元件，為使用 JavaScript 為 Windows 建立的 Windows 8. x 存放區應用程式提供應用程式邏輯，這類差異在 IDE 以及檔中都很明顯。 當您的元件傳回 `IDictionary<int, string>` 至 javascript，並在 javascript 偵錯工具中查看它時，您會看到的方法是 `IMap<int, string>` 因為 javascript 會使用 Windows 執行階段類型。 下表顯示一些常用的集合類型，其會在兩種語言中以不同的方式出現︰

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

在 Windows 執行階段中， `IMap<K, V>` `IMapView<K, V>` 會使用進行反覆運算 `IKeyValuePair` 。 當您將其傳遞至 Managed 程式碼時，它們會顯示成 `IDictionary<TKey, TValue>` 與 `IReadOnlyDictionary<TKey, TValue>`，以便您使用 `System.Collections.Generic.KeyValuePair<TKey, TValue>` 加以列舉。

介面在 Managed 程式碼中的顯示方式，會影響到實作這些介面之型别的顯示方式。 例如　`PropertySet` 類別會實作 `IMap<K, V>`，而這在 Managed 程式碼中會顯示為 `IDictionary<TKey, TValue>`。 `PropertySet` 會以實作了 `IDictionary<TKey, TValue>` (而不是 `IMap<K, V>`) 的形態出現，因此在 Managed 程式碼中，其看似具有 `Add` 方法 (此方法的行為類似於 .NET Framework 字典上的 `Add` 方法。 它看起來並沒有 `Insert` 方法。

如需使用 .NET Framework 建立 Windows 執行階段元件的詳細資訊，以及示範如何使用這類元件搭配 JavaScript 的逐步解說，請參閱使用 [c # 建立 Windows 執行階段元件和 Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)。

### <a name="primitive-types"></a>基本類型

若要在 managed 程式碼中啟用 Windows 執行階段的自然用法，.NET Framework 基本型別會顯示在程式碼中，而不是 Windows 執行階段基本型別的類型。 在 .NET Framework 中，基本型别 (如 `Int32` 結構) 具有許多有用的屬性和方法，例如 `Int32.TryParse` 方法。 相較之下，Windows 執行階段中的基本類型和結構只有欄位。 在 Managed 程式碼中使用基本項目時，將會顯示成 .NET Framework 類型，而您可以如常使用這些 .NET Framework 類型的屬性和方法。 下列清單提供摘要︰

- 針對 Windows 執行階段基本專案 `Int32` ， `Int64` 、 `Single` 、 `Double` 、 `Boolean` `String` () 、、、和等 Unicode 字元的不可變集合，請 `Enum` `UInt32` `UInt64` `Guid` 在命名空間中使用相同名稱的類型 `System` 。

- 如需 `UInt8`，請使用 `System.Byte`。

- 如需 `Char16`，請使用 `System.Char`。

- 對於 `IInspectable` 介面，請使用 `System.Object`。

- 若為 `HRESULT`，搭配使用結構與一個 `System.Int32` 成員。

如同介面型別，您可能只會看到此標記法的辨識項是當您的 .NET Framework 專案是由使用 JavaScript 建立的 Windows 8. x 商店應用程式所使用的 Windows 執行階段元件時。

在 managed 程式碼中出現的其他基本、常用的 Windows 執行階段型別，也就是在 managed 程式碼中出現的 .NET Framework 對等專案包含 `Windows.Foundation.DateTime` 結構，此結構會出現在 managed 程式碼中當做 <xref:System.DateTimeOffset?displayProperty=nameWithType> 結構，而 `Windows.Foundation.TimeSpan` 結構則會顯示為 <xref:System.TimeSpan?displayProperty=nameWithType> 結構

### <a name="other-differences"></a>其他差異

在少數情況下，.NET Framework 類型的事實會出現在您的程式碼中，而不是 Windows 執行階段類型需要您採取動作。 例如， <xref:Windows.Foundation.Uri?displayProperty=nameWithType> 在 .NET Framework 程式碼中，類別會顯示為 <xref:System.Uri?displayProperty=nameWithType> 。 <xref:System.Uri?displayProperty=nameWithType> 允許相對 URI，但 <xref:Windows.Foundation.Uri?displayProperty=nameWithType> 需要絕對 uri。 因此，當您將 URI 傳遞至 Windows 執行階段方法時，您必須確定它是絕對的。 請參閱[將 URI 傳送到 Windows 執行階段](passing-a-uri-to-the-windows-runtime.md)。

<a name="WindowsRuntimeComponents"></a>

## <a name="scenarios-for-developing-windows-runtime-components"></a>開發 Windows 執行階段元件的案例

受管理 Windows 執行階段元件支援的案例取決於下列一般原則：

- 使用 .NET Framework 建立 Windows 執行階段元件與其他 Windows Runtimelibraries 並沒有明顯的差異。 例如，如果您使用 managed 程式碼重新執行原生 Windows 執行階段元件，則這兩個元件的外表不區分。 使用您元件的程式碼不會察覺到該元件是以 Managed 程式碼撰寫，即使該程式碼本身為 Managed 程式碼亦然。 但在內部中，您的元件是實際的 Managed 程式碼且會在通用語言執行平台 (CLR) 上執行。

- 元件可以包含實作為應用程式邏輯、Windows 8. x 存放區 UI 控制項，或兩者的型別。

  > [!NOTE]
  > 將 UI 項目與應用程式邏輯分開是很好的做法。 此外，您無法在使用 JavaScript 和 HTML 為 Windows 建立的 Windows 8. x 存放區應用程式中，使用 Windows 8. x 商店 UI 控制項。

- 元件可以是 Windows 8. x 商店應用程式 Visual Studio 方案內的專案，或是可供您新增至多個解決方案的可重複使用元件。

  > [!NOTE]
  > 如果您的元件只會搭配 c # 或 Visual Basic 使用，則沒有理由將它設為 Windows 執行階段元件。 如果您改為使用一般的 .NET Framework 類別庫，就不需要將其公用 API 介面限制為 Windows 執行階段類型。

- 您可以使用 Windows 執行階段 <xref:Windows.Foundation.Metadata.VersionAttribute> 屬性來識別 (的類型，以及在不同版本中新增) 中哪些成員，以發行可重複使用元件的版本。

- 您元件中的類型可以衍生自 Windows 執行階段類型。 控制項可以衍生自命名空間中的基本控制項類型， <xref:Windows.UI.Xaml.Controls.Primitives> 或從更多完成的控制項（例如） <xref:Windows.UI.Xaml.Controls.Button> 。

  > [!IMPORTANT]
  > 從 Windows 8 和 .NET Framework 4.5 開始，managed Windows 執行階段元件中的所有公用類型都必須密封。 另一個 Windows 執行階段元件中的類型無法從這些類型衍生。 如果您想要在元件中提供多型行為，您可以建立介面並在多型類型中加以實作。

- 元件中公用類型上的所有參數和傳回型別都必須是 Windows 執行階段類型 (包括您的元件定義) 的 Windows 執行階段類型。

下列各節提供常見案例的範例。

### <a name="application-logic-for-a-windows-8x-store-app-with-javascript"></a>使用 JavaScript 的 Windows 8. x Store 應用程式的應用程式邏輯

當您使用 JavaScript 開發適用于 Windows 的 Windows 8. x 儲存應用程式時，您可能會發現應用程式邏輯的某些部分在 managed 程式碼中的執行效能較佳，或更容易開發。 JavaScript 不能直接使用 .NET Framework 類別庫，但是您可以將類別庫作為 .WinMD 檔案。 在此案例中，Windows 執行階段元件是應用程式不可或缺的一部分，因此提供版本屬性並不合理。

### <a name="reusable-windows-8x-store-ui-controls"></a>可重複使用 Windows 8. x 存放區 UI 控制項

您可以在可重複使用的 Windows 執行階段元件中封裝一組相關的 UI 控制項。 元件可以自我行銷，或作為您建立之應用程式中的項目。 在此案例中，使用 Windows 執行階段 <xref:Windows.Foundation.Metadata.VersionAttribute> 屬性來改善相容性，是合理的。

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>來自現有 .NET Framework 應用程式的可重複使用應用程式邏輯

您可以從現有的桌面應用程式將 managed 程式碼封裝為獨立 Windows 執行階段元件。 這可讓您在使用 c + + 或 JavaScript 建立的 Windows 8. x Store 應用程式中，以及使用 c # 或 Visual Basic 建立的 Windows 8. x Store 應用程式中使用此元件。 如果程式碼有多個重複使用的案例，也可選擇進行版本控制。

## <a name="related-topics"></a>[相關主題]

|標題|描述|
|-----------|-----------------|
|[適用於 Windows 市集應用程式的 .NET 概觀](/previous-versions/windows/apps/br230302(v=vs.140))|描述您可以用來建立 Windows 8. x 儲存區應用程式和 Windows RuntimeComponents 的 .NET Framework 類型和成員。 (在 Windows 開發人員中心中。)|
|[使用 C++ 或 Visual Basic 建立 Windows 市集應用程式的藍圖](/previous-versions/windows/apps/br229583(v=win.10))|提供重要的資源，協助您使用 c # 或 Visual Basic 開始開發 Windows 8. x 儲存應用程式，包括許多快速入門主題、指導方針和最佳作法。 (在 Windows 開發人員中心中。)|
|[如何 (XAML) ](/previous-versions/windows/apps/br229566(v=win.10))|提供重要的資源，協助您使用 c # 或 Visual Basic 開始開發 Windows 8. x 儲存應用程式，包括許多快速入門主題、指導方針和最佳作法。 (在 Windows 開發人員中心中。)|
|[在 C++ 和 Visual Basic 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|說明如何使用 .NET Framework 來建立 Windows 執行階段元件、說明如何將它作為使用 JavaScript 為 Windows 建立的 Windows 8. x 存放區應用程式的一部分，並說明如何使用 Visual Studio 進行偵錯工具的組合。 (在 Windows 開發人員中心中。)|
|[Windows 執行階段參考](/uwp/api/)|Windows 執行階段的參考檔。 (在 Windows 開發人員中心中。)|
|[將 URI 傳遞給 Windows 執行階段](passing-a-uri-to-the-windows-runtime.md)|描述當您從 managed 程式碼將 URI 傳遞至 Windows 執行階段時可能會發生的問題，以及如何避免這個問題。|
