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
ms.openlocfilehash: cc673f62e38b854745b4c77522f191cc8bf3fbf6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579284"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>適用於 Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 支援多個 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 的軟體開發案例。 這些案例可分成三個類別︰  
  
-   開發[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]XAML 控制項中所述的應用程式[藍圖適用於 Windows 市集應用程式使用 C# 或 Visual Basic](/previous-versions/windows/apps/br229583(v=win.10))，[如何主題 (XAML)](/previous-versions/windows/apps/br229566(v=win.10))，和[適用於 Windows 市集應用程式的概觀](https://msdn.microsoft.com/library/windows/apps/br230302%28v=VS.110%29.aspx).  
  
-   開發類別庫，在使用 .NET Framework 建立的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式中使用。  
  
-   開發於 .WinMD 檔案封裝的 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件，可供任何支援 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 的程式設計語言使用。 例如，請參閱[C# 和 Visual Basic 中建立 Windows 執行階段元件](https://msdn.microsoft.com/library/windows/apps/br230301(v=VS.110).aspx)。  
  
 本主題概述 .NET Framework 為所有三個類別提供的支援，並說明 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件的案例。 第一章節包含 .NET Framework 和 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 之間關聯性的基本資訊，並說明您可能會在 [說明] 系統及 IDE 中遇到的異狀。 [> 一節的第二個](#WindowsRuntimeComponents)討論開發案例[!INCLUDE[wrt](../../../includes/wrt-md.md)]元件。  
  
## <a name="the-basics"></a>基本概念  
 .NET Framework 藉由提供 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]以及支援 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 本身，進而支援先前所列的三種開發案例。  
  
-   [適用於 Windows 市集應用程式](https://msdn.microsoft.com/library/windows/apps/br230232(v=vs.110).aspx)提供.NET Framework 類別庫的精簡的觀點，並只包含類型和成員，可用來建立[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式和[!INCLUDE[wrt](../../../includes/wrt-md.md)]元件。  
  
    -   當您使用 Visual Studio ([!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] 或更新版本) 開發 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式或 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件時，會有一組參考組件確保您僅看到相關的類型和成員。  
  
    -   這個精簡版的 API 集已進一步簡化，方法是移除在 .NET Framework 中重複或可複製 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 功能的功能。 例如，它僅包含集合類型的泛型版本，且 XML 文件物件模型也因 [!INCLUDE[wrt](../../../includes/wrt-md.md)] XML API 集的益處而予以刪除。  
  
    -   僅包裝作業系統 API 的功能也會移除，因為 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 很容易就可從 Managed 程式碼呼叫。  
  
     若要深入了解[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]，請參閱[適用於 Windows 市集應用程式的概觀](https://msdn.microsoft.com/library/windows/apps/br230302(v=VS.110).aspx)。 若要閱讀有關應用程式開發介面選取程序資訊，請參閱[Metro 樣式應用程式的.NET](https://blogs.msdn.microsoft.com/dotnet/2012/04/17/net-for-metro-style-apps/) .NET 部落格中的項目。  
  
-   [Windows 執行階段](/uwp/api/)提供用於建立使用者介面項目[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式，並提供作業系統功能的存取權。 如同 .NET Framework，[!INCLUDE[wrt](../../../includes/wrt-md.md)] 的中繼資料可讓 C# 和 Visual Basic 編譯器使用 [!INCLUDE[wrt](../../../includes/wrt-md.md)]，方式就如同使用 .NET Framework 類別庫一樣。 .NET Framework 可讓您更輕鬆地使用 [!INCLUDE[wrt](../../../includes/wrt-md.md)]，方法是隱藏一些差異︰  
  
    -   .NET Framework 和 [!INCLUDE[wrt](../../../includes/wrt-md.md)]之間的某些程式設計模式差異，例如新增和移除事件處理常式的模式，即會予以隱藏。 您僅需使用 .NET Framework 模式。  
  
    -   常用類型 (例如基本類型和集合) 中的差異，即會予以隱藏。 您只要使用.NET Framework 型別中所述[差異，會顯示在 IDE 中](#DifferencesVisibleInIDE)在本文稍後。  
  
 大部分的情況下，.NET Framework 的 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 支援皆為透明。 下一節討論 Managed 程式碼和 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 之間的某些明顯差異。  
  
<a name="AboutReferenceDocumentation"></a>   
### <a name="the-net-framework-and-the-includewrtincludeswrt-mdmd-reference-documentation"></a>.NET Framework 及 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 參考文件  
 Windows 執行階段和.NET Framework 文件集的不同。 如果您按下 F1 鍵顯示類型或成員的 [說明]，則會顯示適當集合的參考文件。 不過，如果您瀏覽[Windows 執行階段參考](/uwp/api/)可能會遇到看似令人感到困惑的範例：  
  
-   主題，例如<xref:Windows.Foundation.Collections.IIterable%601>介面沒有宣告語法的 Visual Basic 或 C#。 相反地，請注意上方語法區段 (在此情況下，「.NET： 此介面會顯示為 System.collections.generic.ienumerable<\<T >")。 這是因為 .NET Framework 和 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 使用不同的介面提供類似的功能。 此外，還有行為的差異︰`IIterable` 採用 `First` 方法，而不是 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法傳回列舉值。 .NET Framework 透過讓 Managed 程式碼使用您已熟悉的類型，進而支援 [!INCLUDE[wrt](../../../includes/wrt-md.md)]，讓您無須還得了解其他執行一般工作的方式。 您不會在 IDE 中看到 `IIterable` 介面，因此直接瀏覽 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 參考文件是在該文件看見上述介面的唯一方式。  
  
-   <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)>文件說明密切相關的問題： 其參數型別看起來似乎的不同語言而異。 若為 C# 和 Visual Basic，參數類型為 <xref:System.String?displayProperty=nameWithType> 和 <xref:System.Uri?displayProperty=nameWithType>。 同樣地，這是因為 .NET Framework 有自己的 `String` 和 `Uri` 類型，而針對這類常用類型，強制 .NET Framework 使用者了解其他執行工作的方式並不合理。 在 IDE 中，.NET Framework 會隱藏對應的 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 類型。  
  
-   在少數情況下，例如<xref:Windows.UI.Xaml.GridLength>結構中，.NET Framework 提供的類型名稱相同但更多的功能。 例如，建構函式和屬性的主題集與 `GridLength`相關聯，但它們只有適用於 Visual Basic 和 C# 的語法區塊，這是因為成員僅適用於 Managed 程式碼。 在 [!INCLUDE[wrt](../../../includes/wrt-md.md)]，結構僅具有欄位。 [!INCLUDE[wrt](../../../includes/wrt-md.md)]結構需要協助程式類別<xref:Windows.UI.Xaml.GridLengthHelper>，以提供對等的功能。 您不會在撰寫 Managed 程式碼時，於 IDE 中看到該協助程式類別。  
  
-   在 IDE 中，[!INCLUDE[wrt](../../../includes/wrt-md.md)] 類型似乎衍生自 <xref:System.Object?displayProperty=nameWithType>。 它們似乎具有繼承自 <xref:System.Object>，例如 <xref:System.Object.ToString%2A?displayProperty=nameWithType>。 這些成員的運作方式就好似類型真的是繼承自 <xref:System.Object> [!INCLUDE[wrt](../../../includes/wrt-md.md)] 類型可以轉換成 <xref:System.Object>。 此功能是 .NET Framework 針對 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 提供的部分支援。 不過，如果您在 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 參考文件中檢視類型，並不會出現這類成員。 這些明顯繼承成員的文件由 <xref:System.Object?displayProperty=nameWithType> 參考文件提供。  
  
<a name="DifferencesVisibleInIDE"></a>   
### <a name="differences-that-are-visible-in-the-ide"></a>IDE 中可見的差異  
 在更進階的程式設計案例中，例如使用以 C# 撰寫的 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件為使用 JavaScript 針對 Windows 建置的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式提供應用程式邏輯，這類差異會顯示在 IDE 以及文件中。 當您的元件將 `IDictionary<int, string>` 傳回 JavaScript，而您在 JavaScript 偵錯工具中加以查看，您會看到 `IMap<int, string>` 的方法，因為 JavaScript 使用 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 類型。 下表顯示一些常用的集合類型，其會在兩種語言中以不同的方式出現︰  
  
|[!INCLUDE[wrt](../../../includes/wrt-md.md)] 類型|對應的 .NET Framework 類型|  
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
  
 在 [!INCLUDE[wrt](../../../includes/wrt-md.md)]中，`IMap<K, V>` 與 `IMapView<K, V>` 可使用 `IKeyValuePair` 進行反覆執行。 當您將其傳遞至 Managed 程式碼時，它們會顯示成 `IDictionary<TKey, TValue>` 與 `IReadOnlyDictionary<TKey, TValue>`，以便您使用 `System.Collections.Generic.KeyValuePair<TKey, TValue>` 加以列舉。  
  
 介面在 Managed 程式碼中的顯示方式，會影響到實作這些介面之型别的顯示方式。 例如　`PropertySet` 類別會實作 `IMap<K, V>`，而這在 Managed 程式碼中會顯示為 `IDictionary<TKey, TValue>`。 `PropertySet` 會以實作了 `IDictionary<TKey, TValue>` (而不是 `IMap<K, V>`) 的形態出現，因此在 Managed 程式碼中，其看似具有 `Add` 方法 (此方法的行為類似於 .NET Framework 字典上的 `Add` 方法。 它看起來並沒有 `Insert` 方法。  
  
 如需有關使用.NET Framework 建立[!INCLUDE[wrt](../../../includes/wrt-md.md)]元件，以及逐步解說，示範如何使用這類元件與 JavaScript，請參閱[C# 和 Visual Basic 中建立 Windows 執行階段元件](https://msdn.microsoft.com/library/windows/apps/br230301%28v=VS.110%29.aspx)。  
  
### <a name="primitive-types"></a>基本類型  
 為了在 Managed 程式碼中自然地使用 [!INCLUDE[wrt](../../../includes/wrt-md.md)]，您的程式碼中會顯示 NET Framework 基本類型而不是 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 基本類型。 在 .NET Framework 中，基本型别 (如 `Int32` 結構) 具有許多有用的屬性和方法，例如 `Int32.TryParse` 方法。 相對地，[!INCLUDE[wrt](../../../includes/wrt-md.md)] 中的基本類型和結構就只有欄位而已。 在 Managed 程式碼中使用基本項目時，將會顯示成 .NET Framework 類型，而您可以如常使用這些 .NET Framework 類型的屬性和方法。 下列清單提供摘要︰  
  
-   對於 [!INCLUDE[wrt](../../../includes/wrt-md.md)]基本 `Int32`、`Int64`、`Single`、`Double`、`Boolean`、`String` (Unicode 字元的不可變集合)、`Enum`、`UInt32`、`UInt64` 與 `Guid`，在 `System` 命名空間中請使用相同名稱的型别。  
  
-   對於 `UInt8`，請使用 `System.Byte`。  
  
-   對於 `Char16`，請使用 `System.Char`。  
  
-   對於 `IInspectable` 介面，請使用 `System.Object`。  
  
-   若為 `HRESULT`，搭配使用結構與一個 `System.Int32` 成員。  
  
 如同介面類型，您可能只會在 .NET Framework 專案是 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件，且由使用 JavaScript 建置的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式所使用時，才會看到此表示法的辨識項。  
  
 其他作為其 .NET Framework 對等項目在 Managed 程式碼中出現的基本且常用 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 類型會包括 `Windows.Foundation.DateTime` 結構，該結構會作為 <xref:System.DateTimeOffset?displayProperty=nameWithType> 結構出現在 Managed 程式碼，而 `Windows.Foundation.TimeSpan` 結構會作為 <xref:System.TimeSpan?displayProperty=nameWithType> 結構顯示。  
  
### <a name="other-differences"></a>其他差異  
 在少數情況下，需要您採取動作，才能讓 .NET Framework 類型出現在您的程式碼中，而不是 [!INCLUDE[wrt](../../../includes/wrt-md.md)]。 例如，<xref:Windows.Foundation.Uri?displayProperty=nameWithType>類別會顯示為<xref:System.Uri?displayProperty=nameWithType>在.NET Framework 程式碼。 <xref:System.Uri?displayProperty=nameWithType> 允許相對 URI，但<xref:Windows.Foundation.Uri?displayProperty=nameWithType>需要絕對 URI。 因此，當您將 URI 傳遞至 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 方法時，必須確定其為絕對 URI。 (請參閱[傳遞 URI 給 Windows 執行階段](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)。)  
  
<a name="WindowsRuntimeComponents"></a>   
## <a name="scenarios-for-developing-windows-runtime-components"></a>開發 Windows 執行階段元件的案例  
 Managed [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件所支援的案例取決於下列一般原則︰  
  
-   使用 .NET Framework 所建置的 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件與其他 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 程式庫沒有明顯的差異。 例如，如果您使用 Managed 程式碼重新實作原生 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件，兩個元件在外表上難以區分。 使用您元件的程式碼不會察覺到該元件是以 Managed 程式碼撰寫，即使該程式碼本身為 Managed 程式碼亦然。 但在內部中，您的元件是實際的 Managed 程式碼且會在通用語言執行平台 (CLR) 上執行。  
  
-   元件所包含的類型可實作應用程式邏輯、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI 控制項，或同時實作兩者。  
  
    > [!NOTE]
    >  將 UI 項目與應用程式邏輯分開是很好的做法。 此外，您無法在使用 JavaScript 和 HTML 建置且適用於 Windows 的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式中，使用 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI 控制項。  
  
-   元件可以是 Visual Studio 解決方案中適用於 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式的專案，或是可新增至多個解決方案的可重複使用元件。  
  
    > [!NOTE]
    >  如果只會搭配 C# 或 Visual Basic 使用您的元件，就沒有必要將其作為 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件。 如果您選擇將其作為一般的 .NET Framework 類別庫，則不需要將其公用 API 介面限制為 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 類型。  
  
-   您可以使用發行可重複使用元件的版本[!INCLUDE[wrt](../../../includes/wrt-md.md)]<xref:Windows.Foundation.Metadata.VersionAttribute>不同的版本會加入屬性，以識別哪些類型 （和型別中的成員）。  
  
-   您元件中的類型可衍生自 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 類型。 控制項可以衍生自中的基本的控制項類型<xref:Windows.UI.Xaml.Controls.Primitives>命名空間或從多個完成控制項例如<xref:Windows.UI.Xaml.Controls.Button>。  
  
    > [!IMPORTANT]
    >  自 [!INCLUDE[win8](../../../includes/win8-md.md)] 和 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]開始，Managed [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件中的所有公用類型都必須密封。 另一個 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件中的類型無法從中衍生。 如果您想要在元件中提供多型行為，您可以建立介面並在多型類型中加以實作。  
  
-   公用類型上您元件中的所有參數和傳回類型都必須是 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 型類型 (包括您元件所定義的 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 類型)。  
  
 下列各節提供常見案例的範例。  
  
### <a name="application-logic-for-a-includewin8appnamelongincludeswin8-appname-long-mdmd-app-with-javascript"></a>[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式的應用程式邏輯與 JavaScript  
 當您使用 JavaScript 為 Windows 開發 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式時，您可能會發現應用程式邏輯的某些部分在 Managed 程式碼中，有較佳的效能或較容易開發。 JavaScript 不能直接使用 .NET Framework 類別庫，但是您可以將類別庫作為 .WinMD 檔案。 在此案例中，[!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件是應用程式中不可或缺的一部分，因此並不需要提供版本屬性。  
  
### <a name="reusable-includewin8appnamelongincludeswin8-appname-long-mdmd-ui-controls"></a>可重複使用的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] UI 控制項  
 您可在可重複使用的 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件中，封裝一組相關的 UI 控制項。 元件可以自我行銷，或作為您建立之應用程式中的項目。 在此案例中，它使用合理[!INCLUDE[wrt](../../../includes/wrt-md.md)]<xref:Windows.Foundation.Metadata.VersionAttribute>屬性以提高相容性。  
  
### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>來自現有 .NET Framework 應用程式的可重複使用應用程式邏輯  
 您可以從現有的桌面應用程式封裝 Managed 程式碼，作為獨立的 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件。 這可讓您將元件用於使用 C++ 或 JavaScrip 所建置的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式，以及使用 C# 或 Visual Basic 所建置的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式。 如果程式碼有多個重複使用的案例，也可選擇進行版本控制。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[適用於 Windows 市集應用程式的 .NET 概觀](https://msdn.microsoft.com/library/windows/apps/br230302(v=VS.110).aspx)|描述您可以用來建立 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式和 [!INCLUDE[wrt](../../../includes/wrt-md.md)]元件的 .NET Framework 類型和成員。 (在 Windows 開發人員中心中。)|  
|[使用 C# 或 Visual Basic 的 Windows 市集應用程式的藍圖](/previous-versions/windows/apps/br229583(v=win.10))|提供重要資源，協助您使用 C# 或 Visual Basic 開始開發 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式，包括許多快速入門主題、指導方針和最佳做法。 (在 Windows 開發人員中心中。)|  
|[如何主題 (XAML)](/previous-versions/windows/apps/br229566(v=win.10))|提供重要資源，協助您使用 C# 或 Visual Basic 開始開發 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式，包括許多快速入門主題、指導方針和最佳做法。 (在 Windows 開發人員中心中。)|  
|[在 C++ 和 Visual Basic 中建立 Windows 執行階段元件](https://msdn.microsoft.com/library/windows/apps/br230301%28v=VS.110%29.aspx)|描述如何使用 .NET Framework 建立 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件、說明如何將其作為使用 JavaScript 為 Windows 建置的 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式一部分，並說明如何使用 Visual Studio 為該組合偵錯。 (在 Windows 開發人員中心中。)|  
|[Windows 執行階段參考](/uwp/api/)|[!INCLUDE[wrt](../../../includes/wrt-md.md)] 的參考文件。 (在 Windows 開發人員中心中。)|  
|[將 URI 傳遞給 Windows 執行階段](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|描述當您從 Managed 程式碼將 URI 傳遞至 [!INCLUDE[wrt](../../../includes/wrt-md.md)]時可能發生的問題，以及如何加以避免。|
