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
ms.openlocfilehash: c49e9a5c4b8785704f8c4cbd1c9b7af10dc0c689
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661788"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>適用於 Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援

.NET Framework 4.5 支援與 Windows 執行階段的軟體開發案例的數目。 這些案例可分成三個類別︰

- 開發[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式與 XAML 控制項中所述[藍圖適用於 Windows 市集應用程式使用 C# 或 Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))，[如何主題 (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))，和[適用於 Windows 市集應用程式的概觀](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

- 開發類別庫，在使用 .NET Framework 建立的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式中使用。

- 開發 Windows 執行階段元件，以封裝。WinMD 檔案，可供任何程式設計語言，支援 Windows 執行階段。 例如，請參閱[Creating Windows Runtime Components in C# 和 Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)。

本主題概述.NET Framework 提供所有的三個類別目錄，並說明的案例，Windows 執行階段元件的支援。 第一個區段包含.NET Framework 和 Windows 執行階段之間的關聯性的基本資訊，並說明中的說明系統和 IDE 可能會遇到的異狀。 [一節的第二個](#WindowsRuntimeComponents)討論開發 Windows 執行階段元件的案例。

## <a name="the-basics"></a>基本概念

.NET Framework 支援藉由提供稍早所列的三種開發案例[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]，並支援 Windows 執行階段本身。

- [.NET framework 和 Windows 執行階段命名空間](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces)提供.NET Framework 類別庫的精簡的觀點，並只包含的類型和成員可用來建立[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式和 Windows 執行階段元件。

  - 當您使用 Visual Studio (Visual Studio 2012 或更新版本) 來開發[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]參考組件的一組應用程式或 Windows 執行階段元件中，確保您會看到只有相關型別和成員。

  - 這個簡化的 API 集已經過簡化進一步移除.NET Framework 中重複或可重複的 Windows 執行階段功能的功能。 比方說，它包含集合類型的泛型版本，而 XML 文件物件模型也會刪除由 Windows 執行階段的 XML API 設定。

  - 僅包裝作業系統 API 的功能會一併移除，因為 Windows 執行階段輕鬆地從 managed 程式碼呼叫。

  若要深入了解[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]，請參閱 <<c2> [ 適用於 Windows 市集應用程式的概觀](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))。 若要深入了解 API 選擇程序，請參閱[適用於 Metro 樣式應用程式的.NET](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) .NET 部落格中的項目。

- [Windows 執行階段](/uwp/api/)提供使用者介面項目，用於建立[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式，並提供作業系統功能的存取權。 .NET Framework 中，例如 Windows 執行階段有中繼資料，可讓C#和 Visual Basic 編譯器，若要使用 Windows 執行階段的方式，使用.NET Framework 類別庫。 .NET Framework 可讓您更輕鬆地使用 Windows 執行階段隱藏一些差異：

  - 會隱藏一些程式設計模式，.NET Framework 和 Windows 執行階段，例如新增和移除事件處理常式的模式之間的差異。 您僅需使用 .NET Framework 模式。

  - 常用類型 (例如基本類型和集合) 中的差異，即會予以隱藏。 您只需使用.NET Framework 型別中所述[可見的差異在 IDE 中](#DifferencesVisibleInIDE)稍後在本文中。

大部分下，.NET Framework 支援的 Windows 執行階段是情況的透明的。 下一節將討論一些 managed 程式碼和 Windows 執行階段的明顯差異。

<a name="AboutReferenceDocumentation"></a>

### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>.NET Framework 和 Windows 執行階段參考文件

Windows 執行階段和.NET Framework 文件集是分開的。 如果您按下 F1 鍵顯示類型或成員的 [說明]，則會顯示適當集合的參考文件。 不過，如果您瀏覽[Windows 執行階段參考](/uwp/api/)您可能會遇到令人感到困惑的範例：

- 主題，例如<xref:Windows.Foundation.Collections.IIterable%601>介面沒有宣告語法的 Visual Basic 或 C#。 相反地，語法區段上方出現一個附註 (在此情況下，「.NET:這個介面會顯示為 System.Collections.Generic.IEnumerable\<T >")。 這是因為.NET Framework 和 Windows 執行階段提供類似的功能，使用不同的介面。 此外，還有行為的差異︰`IIterable` 採用 `First` 方法，而不是 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法傳回列舉值。 不會強迫您了解執行常見工作的不同方式，.NET Framework 會支援 Windows 執行階段藉由 managed 程式碼以使用您熟悉的類型。 您不會看到`IIterable`在 IDE 中，介面，並因此會發生這個情形中的 Windows 執行階段參考文件的唯一方式是藉由直接瀏覽文件。

- <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)>文件說明密切相關的問題：其參數型別會出現不同的語言不同。 若為 C# 和 Visual Basic，參數類型為 <xref:System.String?displayProperty=nameWithType> 和 <xref:System.Uri?displayProperty=nameWithType>。 同樣地，這是因為 .NET Framework 有自己的 `String` 和 `Uri` 類型，而針對這類常用類型，強制 .NET Framework 使用者了解其他執行工作的方式並不合理。 在 IDE 中，.NET Framework 會隱藏對應的 Windows 執行階段型別。

- 在少數情況下，例如<xref:Windows.UI.Xaml.GridLength>結構中，.NET Framework 提供的類型有相同名稱但更多的功能。 例如，建構函式和屬性的主題集與 `GridLength`相關聯，但它們只有適用於 Visual Basic 和 C# 的語法區塊，這是因為成員僅適用於 Managed 程式碼。 在 Windows 執行階段中，結構僅具有欄位。 Windows 執行階段結構需要協助程式類別， <xref:Windows.UI.Xaml.GridLengthHelper>，以提供對等的功能。 您不會在撰寫 Managed 程式碼時，於 IDE 中看到該協助程式類別。

- 在 IDE 中，Windows 執行階段類型似乎衍生自<xref:System.Object?displayProperty=nameWithType>。 它們似乎具有繼承自 <xref:System.Object>，例如 <xref:System.Object.ToString%2A?displayProperty=nameWithType>。 這些成員的運作方式就好似類型真的是繼承自<xref:System.Object>，和 Windows 執行階段類型就可轉換成<xref:System.Object>。 這項功能是.NET Framework 會提供適用於 Windows 執行階段支援的一部分。 不過，如果您的 Windows 執行階段參考文件中檢視的類型，沒有這類成員將會出現。 這些明顯繼承成員的文件由 <xref:System.Object?displayProperty=nameWithType> 參考文件提供。

<a name="DifferencesVisibleInIDE"></a>

### <a name="differences-that-are-visible-in-the-ide"></a>IDE 中可見的差異

在更進階的程式設計案例中的，例如使用 Windows 執行階段元件撰寫C#提供的應用程式邏輯[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]針對使用 JavaScript 的 Windows 建置的應用程式，這類差異會顯示在 IDE 以及中文件。 當您的元件傳回`IDictionary<int, string>`JavaScript，而您在 JavaScript 偵錯工具中查看，您會看到的方法`IMap<int, string>`因為 JavaScript 使用的 Windows 執行階段類型。 下表顯示一些常用的集合類型，其會在兩種語言中以不同的方式出現︰

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

在 Windows 執行階段`IMap<K, V>`及`IMapView<K, V>`來反覆查看使用`IKeyValuePair`。 當您將其傳遞至 Managed 程式碼時，它們會顯示成 `IDictionary<TKey, TValue>` 與 `IReadOnlyDictionary<TKey, TValue>`，以便您使用 `System.Collections.Generic.KeyValuePair<TKey, TValue>` 加以列舉。

介面在 Managed 程式碼中的顯示方式，會影響到實作這些介面之型别的顯示方式。 例如　`PropertySet` 類別會實作 `IMap<K, V>`，而這在 Managed 程式碼中會顯示為 `IDictionary<TKey, TValue>`。 `PropertySet` 會以實作了 `IDictionary<TKey, TValue>` (而不是 `IMap<K, V>`) 的形態出現，因此在 Managed 程式碼中，其看似具有 `Add` 方法 (此方法的行為類似於 .NET Framework 字典上的 `Add` 方法。 它看起來並沒有 `Insert` 方法。

如需使用.NET Framework 建立 Windows 執行階段元件，並示範如何使用這類元件與 JavaScript 的逐步解說的詳細資訊，請參閱[Creating Windows Runtime Components inC#和 Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

### <a name="primitive-types"></a>基本類型

若要啟用的自然使用 managed 程式碼中的 Windows 執行階段，.NET Framework 基本型別出現而不是在程式碼中的 Windows 執行階段基本類型。 在 .NET Framework 中，基本型别 (如 `Int32` 結構) 具有許多有用的屬性和方法，例如 `Int32.TryParse` 方法。 相反地，基本類型和 Windows 執行階段中的結構有只有欄位。 在 Managed 程式碼中使用基本項目時，將會顯示成 .NET Framework 類型，而您可以如常使用這些 .NET Framework 類型的屬性和方法。 下列清單提供摘要︰

- Windows 執行階段基本類型的`Int32`， `Int64`， `Single`， `Double`， `Boolean`， `String` （Unicode 字元的不可變集合）， `Enum`， `UInt32`， `UInt64`，及`Guid`，使用中的相同名稱的型別`System`命名空間。

- 對於 `UInt8`，請使用 `System.Byte`。

- 對於 `Char16`，請使用 `System.Char`。

- 對於 `IInspectable` 介面，請使用 `System.Object`。

- 若為 `HRESULT`，搭配使用結構與一個 `System.Int32` 成員。

為介面類型時，您可能會看到此表示法的辨識項時，才您.NET Framework 的專案是 Windows 執行階段元件，可由[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]使用 JavaScript 建置的應用程式。

其他基本的常用 Windows 執行階段類型出現在 managed 程式碼，因為其.NET Framework 對等項目包含`Windows.Foundation.DateTime`結構，就會出現在 managed 程式碼當做<xref:System.DateTimeOffset?displayProperty=nameWithType>結構，而`Windows.Foundation.TimeSpan`結構，其中會顯示為<xref:System.TimeSpan?displayProperty=nameWithType>結構。

### <a name="other-differences"></a>其他差異

在少數情況下，.NET Framework 類型出現在您的程式碼，而不是 Windows 執行階段類型的事實會需要您採取的動作。 例如，<xref:Windows.Foundation.Uri?displayProperty=nameWithType>類別會顯示為<xref:System.Uri?displayProperty=nameWithType>在.NET Framework 程式碼。 <xref:System.Uri?displayProperty=nameWithType> 可讓相對 URI，但<xref:Windows.Foundation.Uri?displayProperty=nameWithType>需要絕對 URI。 因此，當您將 URI 傳遞給 Windows 執行階段方法時，您必須確認其為絕對。 (請參閱[傳遞 URI 給 Windows 執行階段](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)。)

<a name="WindowsRuntimeComponents"></a>

## <a name="scenarios-for-developing-windows-runtime-components"></a>開發 Windows 執行階段元件的案例

受管理的 Windows 執行階段元件支援的案例取決於下列的一般原則：

- 使用.NET Framework 所建置的 Windows 執行階段元件已經從其他 Windows Runtimelibraries 沒有明顯的差異。 比方說，如果您重新實作原生的 Windows 執行階段元件，使用 managed 程式碼，則兩個元件是外表上難以區分。 使用您元件的程式碼不會察覺到該元件是以 Managed 程式碼撰寫，即使該程式碼本身為 Managed 程式碼亦然。 但在內部中，您的元件是實際的 Managed 程式碼且會在通用語言執行平台 (CLR) 上執行。

- 元件所包含的類型可實作應用程式邏輯、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI 控制項，或同時實作兩者。

  > [!NOTE]
  > 將 UI 項目與應用程式邏輯分開是很好的做法。 此外，您無法在使用 JavaScript 和 HTML 建置且適用於 Windows 的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式中，使用 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI 控制項。

- 元件可以是 Visual Studio 解決方案中適用於 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式的專案，或是可新增至多個解決方案的可重複使用元件。

  > [!NOTE]
  > 如果您的元件將僅能搭配C#或 Visual Basic 中，沒有理由讓 Windows 執行階段元件。 如果您讓一般的.NET Framework 類別庫相反地，您不需要 Windows 執行階段型別限制其公用 API 介面。

- 您可以使用 Windows 執行階段發行版本的可重複使用元件<xref:Windows.Foundation.Metadata.VersionAttribute>中不同版本所加入的屬性，以識別哪些類型 （及哪些類型中的成員）。

- 在您的元件類型可以衍生自 Windows 執行階段類型。 控制項可以從基本的控制項型別中衍生<xref:Windows.UI.Xaml.Controls.Primitives>命名空間或從多個完成的控制項，例如<xref:Windows.UI.Xaml.Controls.Button>。

  > [!IMPORTANT]
  > 從開始[!INCLUDE[win8](../../../includes/win8-md.md)]和.NET Framework 4.5 中，受管理的 Windows 執行階段元件中的所有公用型別都必須密封。 另一個 Windows 執行階段元件中的類型無法從中衍生。 如果您想要在元件中提供多型行為，您可以建立介面並在多型類型中加以實作。

- 您的元件中的公用類型上的所有參數和傳回類型必須都是 Windows 執行階段類型 （包括您元件所定義的 Windows 執行階段類型）。

下列各節提供常見案例的範例。

### <a name="application-logic-for-a-includewin8appnamelongincludeswin8-appname-long-mdmd-app-with-javascript"></a>[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式的應用程式邏輯與 JavaScript

當您使用 JavaScript 為 Windows 開發 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式時，您可能會發現應用程式邏輯的某些部分在 Managed 程式碼中，有較佳的效能或較容易開發。 JavaScript 不能直接使用 .NET Framework 類別庫，但是您可以將類別庫作為 .WinMD 檔案。 在此案例中，Windows 執行階段元件會是應用程式時，不可或缺的一部分，因此並不需要提供版本屬性。

### <a name="reusable-includewin8appnamelongincludeswin8-appname-long-mdmd-ui-controls"></a>可重複使用的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI 控制項

您可以將封裝一組相關的 UI 控制項，可重複使用的 Windows 執行階段元件中。 元件可以自我行銷，或作為您建立之應用程式中的項目。 在此案例中，它可以使用 Windows 執行階段<xref:Windows.Foundation.Metadata.VersionAttribute>屬性來改善相容性。

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>來自現有 .NET Framework 應用程式的可重複使用應用程式邏輯

您可以從您現有的傳統型應用程式封裝 managed 程式碼，做為獨立的 Windows 執行階段元件。 這可讓您將元件用於使用 C++ 或 JavaScrip 所建置的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式，以及使用 C# 或 Visual Basic 所建置的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式。 如果程式碼有多個重複使用的案例，也可選擇進行版本控制。

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----------|-----------------|
|[適用於 Windows 市集應用程式的 .NET 概觀](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|描述.NET Framework 類型和成員，您可以使用它來建立[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式和 Windows RuntimeComponents。 (在 Windows 開發人員中心中。)|
|[使用 C# 或 Visual Basic 的 Windows 市集應用程式的藍圖](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|提供重要資源，協助您使用 C# 或 Visual Basic 開始開發 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式，包括許多快速入門主題、指導方針和最佳做法。 (在 Windows 開發人員中心中。)|
|[如何主題 (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|提供重要資源，協助您使用 C# 或 Visual Basic 開始開發 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式，包括許多快速入門主題、指導方針和最佳做法。 (在 Windows 開發人員中心中。)|
|[在 C++ 和 Visual Basic 中建立 Windows 執行階段元件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|描述如何建立使用.NET Framework 之 Windows 執行階段元件、 說明如何使用它做為一部分[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式針對使用 JavaScript 的 Windows 所建置，並說明如何偵錯使用 Visual Studio 的組合。 (在 Windows 開發人員中心中。)|
|[Windows 執行階段參考](/uwp/api/)|Windows 執行階段參考文件。 (在 Windows 開發人員中心中。)|
|[將 URI 傳遞給 Windows 執行階段](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|當您將 URI 從 managed 程式碼傳遞至 Windows 執行階段，以及如何加以避免，可能會發生的問題進行說明。|
