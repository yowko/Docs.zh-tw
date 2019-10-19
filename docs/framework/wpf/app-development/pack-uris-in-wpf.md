---
title: WPF 中的 Pack URI
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: 59c72d9ae12a014a8c47cb3b2852b337b173446c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580624"
---
# <a name="pack-uris-in-wpf"></a>WPF 中的 Pack URI

在 Windows Presentation Foundation （WPF）中，統一資源識別項（Uri）是用來以許多方式來識別和載入檔案，包括下列各項：

- 指定要在應用程式第一次啟動時顯示的 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。

- 載入影像。

- 巡覽至頁面。

- 載入不可執行的資料檔案。

此外，Uri 也可以用來從各種不同的位置識別和載入檔案，包括下列各項：

- 目前的組件。

- 所參考的組件。

- 與組件相對的位置。

- 應用程式的來源網站。

為了提供一致的機制，從這些位置識別和載入這些類型的檔案，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 利用*PACK URI 配置*的擴充性。 本主題提供配置的總覽，涵蓋如何為各種案例建立套件 Uri、討論絕對和相對 Uri 和 URI 解析，再顯示如何使用標記和程式碼中的套件 Uri。

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a>套件 URI 配置

套件 URI 配置是由[開放封裝慣例](https://go.microsoft.com/fwlink/?LinkID=71255)（OPC）規格所使用，其描述用於組織和識別內容的模型。 此模型的主要元素是封裝和元件，其中*封裝*是一或多個邏輯*元件*的邏輯容器。 下圖說明這個概念。

![套件和部分圖表](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

為了識別元件，OPC 規格會利用 RFC 2396 （統一資源識別元（URI）：泛型語法）的擴充性來定義 pack URI 配置。

URI 所指定的配置是由其前置詞所定義。HTTP、ftp 和 file 都是已知的範例。 套件 URI 配置會使用 "pack" 作為其配置，並包含兩個元件：授權單位和路徑。 以下是 pack URI 的格式。

pack://*授權*/*路徑*

*授權*單位會指定元件所包含的封裝類型，而*路徑*則會指定元件在封裝內的位置。

下圖說明這個概念︰

![套件、授權和路徑之間的關聯性](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

套件和組件與應用程式和檔案類似，其中應用程式 (套件) 可以包括一或多個檔案 (組件)，包括︰

- 編譯為本機組件的資源檔。

- 編譯為所參考組件的資源檔。

- 編譯為參考組件的資源檔。

- 內容檔。

- 來源網站檔案。

若要存取這些類型的檔，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 支援兩個授權單位： application:///和 siteoforigin:///。 application:/// 授權識別在編譯時期已知的應用程式資料檔，包括資源檔和內容檔。 siteoforigin:/// 授權識別來源網站檔案。 下圖顯示每個授權的範圍。

![封裝 URI 圖表](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> Pack URI 的授權元件是內嵌的 URI，它會指向封裝，而且必須符合 RFC 2396。 此外，"/" 字元必須取代為 "," 字元，而且必須逸出 "%" 和 "?" 這類保留字元。 如需詳細資料，請參閱 OPC。

下列各節說明如何使用這兩個授權單位來建立套件 Uri，並搭配適當的路徑來識別資源、內容和來源網站檔案。

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a>資源檔套件 URI

資源檔會設定為 MSBuild `Resource` 專案，並編譯成元件。 WPF 支援封裝 Uri 的結構，可用來識別編譯成本機組件或編譯成元件（從本機組件參考）的資源檔。

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a>本機組件資源檔

編譯為本機組件之資源檔的 pack URI 會使用下列授權和路徑：

- **授權**：application:///。

- **路徑**︰相對於本機組件專案資料夾根之資源檔的名稱，包括其路徑。

下列範例顯示位於本機組件之專案資料夾根目錄中 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 資源檔的 pack URI。

`pack://application:,,,/ResourceFile.xaml`

下列範例顯示位於本機組件專案資料夾之子資料夾中 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 資源檔的 pack URI。

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a>所參考的組件資源檔

編譯成參考元件之資源檔的 pack URI 會使用下列授權和路徑：

- **授權**：application:///。

- **路徑**：編譯為所參考組件之資源檔的名稱。 路徑必須符合下列格式：

  *AssemblyShortName*{ *;版本*] { *;PublicKey*]; 元件/*路徑*

  - **AssemblyShortName**：所參考組件的簡短名稱。

  - **;Version** [選擇性]：包含資源檔之參考組件的版本。 這是在載入具有相同簡短名稱的兩個以上參考組件時使用。

  - **;PublicKey** [選擇性]：用來簽署參考組件的公開金鑰。 這是在載入具有相同簡短名稱的兩個以上參考組件時使用。

  - **;component**︰指定從本機組件參考所參考的組件。

  - **/Path**︰相對於所參考組件專案資料夾根之資源檔的名稱，包括其路徑。

下列範例顯示位於所參考元件之專案資料夾根目錄中 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 資源檔的 pack URI。

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

下列範例顯示位於所參考元件專案資料夾之子資料夾中 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 資源檔的 pack URI。

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

下列範例顯示的是 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 資源檔的 pack URI，此檔案位於參考的版本特定元件之專案資料夾的根資料夾中。

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

請注意，所參考元件資源檔的 pack URI 語法只能搭配 application:///授權單位使用。 例如，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 不支援下列各項。

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a>內容檔套件 URI

內容檔案的 pack URI 會使用下列授權和路徑：

- **授權**：application:///。

- **路徑**：內容檔的名稱，包括其相對於應用程式主要可執行組件之檔案系統位置的路徑。

下列範例顯示與可執行元件位於相同資料夾中 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 內容檔案的 pack URI。

`pack://application:,,,/ContentFile.xaml`

下列範例顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 內容檔案的 pack URI，此檔案位於與應用程式可執行元件相對的子資料夾中。

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> 無法流覽 HTML 內容檔。 URI 配置只支援流覽至位於來源網站的 HTML 檔案。

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a>來源網站套件 URI

原始網站檔案的 pack URI 會使用下列授權和路徑：

- **授權**：siteoforigin:///。

- **路徑**：來源網站檔案的名稱，包括其相對於從中啟動可執行組件之位置的路徑。

下列範例會顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 來源網站檔案的 pack URI，儲存在可執行檔元件啟動的位置。

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

下列範例顯示的是來源 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 網站檔案的 pack URI，儲存在相對於啟動應用程式可執行元件之位置的子資料夾中。

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a>分頁檔

設定為 MSBuild `Page` 專案的 XAML 檔案，會以與資源檔相同的方式編譯成元件。 因此，可以使用資源檔的 pack Uri 來識別 MSBuild `Page` 專案。

通常設定為 MSBuild `Page` 專案的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案類型具有下列其中一項做為其根項目：

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a>絕對與相對的套件 Uri

完整的 pack URI 包括配置、授權和路徑，而且會被視為絕對套件 URI。 做為開發人員的簡化，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 元素通常可讓您使用相對 pack URI 設定適當的屬性，其中只包含路徑。

例如，請考慮本機組件中資源檔的下列絕對套件 URI。

`pack://application:,,,/ResourceFile.xaml`

參考此資源檔的相對 pack URI 會如下所示。

`/ResourceFile.xaml`

> [!NOTE]
> 由於原始網站檔案不會與元件相關聯，因此只能使用絕對套件 Uri 來參考它們。

根據預設，相對 pack URI 會被視為相對於標記或包含參考之程式碼的位置。 不過，如果使用前導反斜線，則相對的 pack URI 參考會被視為相對於應用程式的根目錄。 例如，請考慮下列專案結構。

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

如果 Page1 包含參考*根*\SUBFOLDER\PAGE2.XAML 的 URI，則參考可以使用下列相對 pack uri。

`Page2.xaml`

如果 Page1 包含參考*根*\PAGE2.XAML 的 URI，則參考可以使用下列相對 pack uri。

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a>套件 URI 解析

Pack Uri 的格式可讓不同類型檔案的套件 Uri 看起來相同。 例如，請考慮下列絕對套件 URI。

`pack://application:,,,/ResourceOrContentFile.xaml`

這個絕對套件 URI 可以參考本機組件或內容檔案中的資源檔。 下列相對 URI 也是如此。

`/ResourceOrContentFile.xaml`

為了判斷 pack URI 所參考的檔案類型，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 使用下列啟發學習法，解析本機組件和內容檔案中資源檔的 Uri：

1. 探查符合 pack URI 之 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 屬性的元件中繼資料。

2. 如果找到 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 屬性，則 pack URI 的路徑會參考內容檔。

3. 如果找不到 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 屬性，請探查編譯到本機組件中的集合資源檔。

4. 如果找到符合 pack URI 路徑的資源檔，則 pack URI 的路徑會參考資源檔。

5. 如果找不到資源，內部建立的 <xref:System.Uri> 將會無效。

URI 解析不適用於參考下列各項的 Uri：

- 參考元件中的內容檔： [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 不支援這些檔案類型。

- 參考元件中的內嵌檔案：識別它們的 Uri 是唯一的，因為它們同時包含參考元件的名稱和 `;component` 尾碼。

- 來源網站檔案：識別這些檔案的 Uri 是唯一的，因為這些檔案是可由包含 siteoforigin:///授權單位的 pack Uri 識別的唯一檔案。

套件 URI 解析的簡化之一，是讓程式碼與資源和內容檔案的位置有些獨立。 例如，如果您在本機組件中的資源檔重新設定為內容檔，則資源的 pack URI 會維持不變，如同使用 pack URI 的程式碼一樣。

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a>使用套件 URI 的程式設計

許多 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 類別會執行可使用 pack Uri 設定的屬性，包括：

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

可以透過標記和程式碼來設定這些屬性。 本節示範兩者的基本建構，並顯示常見案例的範例。

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a>透過標記使用套件 URI

在標記中指定的 pack URI，是藉由設定具有 pack URI 之屬性的元素。 例如:

`<element attribute="pack://application:,,,/File.xaml" />`

[表 1] 說明您可以在標記中指定的各種絕對套件 Uri。

表 1：使用標記的絕對套件 URI

|檔案|絕對套件 URI|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|資源檔 - 本機組件|`"pack://application:,,,/ResourceFile.xaml"`|
|子資料夾中的資源檔 - 本機組件|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|資源檔 - 參考組件|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|參考組件之子資料夾中的資源檔|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|版本化參考組件中的資源檔|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|內容檔|`"pack://application:,,,/ContentFile.xaml"`|
|子資料夾中的內容檔|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|來源網站檔案|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|子資料夾中的來源網站檔案|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

[表 2] 說明您可以在標記中指定的各種相對套件 Uri。

表 2：使用標記的相對套件 URI

|檔案|相對套件 URI|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|本機組件中的資源檔|`"/ResourceFile.xaml"`|
|本機組件子資料夾中的資源檔|`"/Subfolder/ResourceFile.xaml"`|
|參考組件中的資源檔|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|參考組件之子資料夾中的資源檔|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|內容檔|`"/ContentFile.xaml"`|
|子資料夾中的內容檔|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a>透過程式碼使用套件 URI

您可以將 <xref:System.Uri> 類別具現化，並將 pack URI 當做參數傳遞至函式，以在程式碼中指定 pack URI。 這點在下列範例中示範。

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

根據預設，<xref:System.Uri> 類別會將 pack Uri 視為絕對。 因此，當使用相對 pack URI 建立 <xref:System.Uri> 類別的實例時，就會引發例外狀況（exception）。

```csharp
Uri uri = new Uri("/File.xaml");
```

幸運的是，<xref:System.Uri> 類別的 <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> 多載會接受型別 <xref:System.UriKind> 的參數，讓您指定 pack URI 是絕對或相對的。

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

當您確定提供的 pack URI 是其中一個或另一個時，您應該只指定 <xref:System.UriKind.Absolute> 或 <xref:System.UriKind.Relative>。 如果您不知道所使用的 pack URI 類型，例如當使用者在執行時間輸入 pack URI 時，請改用 <xref:System.UriKind.RelativeOrAbsolute>。

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

[表 3] 說明您可以使用 <xref:System.Uri?displayProperty=nameWithType> 在程式碼中指定的各種相對套件 Uri。

表 3：使用程式碼的絕對套件 URI

|檔案|絕對套件 URI|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|資源檔 - 本機組件|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|子資料夾中的資源檔 - 本機組件|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|資源檔 - 參考組件|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|參考組件之子資料夾中的資源檔|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|版本化參考組件中的資源檔|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|內容檔|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|子資料夾中的內容檔|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|來源網站檔案|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|子資料夾中的來源網站檔案|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

[表 4] 說明您可以使用 <xref:System.Uri?displayProperty=nameWithType> 在程式碼中指定的各種相對套件 Uri。

表 4：使用程式碼的相對套件 URI

|檔案|相對套件 URI|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|資源檔 - 本機組件|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|子資料夾中的資源檔 - 本機組件|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|資源檔 - 參考組件|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|子資料夾中的資源檔 - 參考組件|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|內容檔|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|子資料夾中的內容檔|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a>常見套件 URI 案例

前面幾節已討論如何建立套件 Uri，以識別資源、內容和來源網站檔案。 在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，這些結構會以各種不同的方式使用，而下列各節將涵蓋數個常見的用法。

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>指定要在啟動應用程式時顯示的 UI

<xref:System.Windows.Application.StartupUri%2A> 指定啟動 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式時所要顯示的第一個 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 針對獨立應用程式，[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 可以是視窗，如下列範例所示。

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

獨立應用程式和 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 也可以指定頁面做為初始 UI，如下列範例所示。

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

如果應用程式是獨立應用程式，而且已使用 <xref:System.Windows.Application.StartupUri%2A> 來指定頁面，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 就會開啟 <xref:System.Windows.Navigation.NavigationWindow> 來裝載該頁面。 針對 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]，此頁面會顯示在主機瀏覽器中。

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a>巡覽至頁面

下列範例示範如何巡覽至頁面。

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

如需在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中流覽各種方式的詳細資訊，請參閱[導覽總覽](navigation-overview.md)。

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a>指定視窗圖示

下列範例示範如何使用 URI 來指定視窗的圖示。

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

如需詳細資訊，請參閱<xref:System.Windows.Window.Icon%2A>。

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a>載入影像、音訊和視訊檔案

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 允許應用程式使用各種不同的媒體類型，這些都可以用 pack Uri 識別和載入，如下列範例所示。

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

如需使用媒體內容的詳細資訊，請參閱[圖形和多媒體](../graphics-multimedia/index.md)。

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>從來源網站載入資源字典

資源字典（<xref:System.Windows.ResourceDictionary>）可以用來支援應用程式主題。 建立和管理主題的一種方法是將多個主題建立為位在應用程式來源網站的資源字典。 這樣可新增和更新主題，而不需要重新編譯和重新部署應用程式的。 您可以使用套件 Uri 來識別和載入這些資源字典，如下列範例所示。

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

如需 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 主題的總覽，請參閱設定[樣式和範本](../controls/styling-and-templating.md)。

## <a name="see-also"></a>請參閱

- [WPF 應用程式資源、內容和資料檔案](wpf-application-resource-content-and-data-files.md)
