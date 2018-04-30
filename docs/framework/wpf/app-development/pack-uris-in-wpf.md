---
title: WPF 中的 Pack URI
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
caps.latest.revision: 35
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d90345f6c6e44bfdd98d2a1313a36372cdfe8b06
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="pack-uris-in-wpf"></a>WPF 中的 Pack URI
在 Windows Presentation Foundation (WPF)，[!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]用來識別及載入檔案，在許多方面，包括下列：  
  
-   指定[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]以顯示應用程式第一次啟動時。  
  
-   載入影像。  
  
-   巡覽至頁面。  
  
-   載入不可執行的資料檔案。  
  
 此外，[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]可用來識別及載入檔案，從各種不同的位置，包括下列：  
  
-   目前的組件。  
  
-   所參考的組件。  
  
-   與組件相對的位置。  
  
-   應用程式的來源網站。  
  
 若要提供一致的機制來識別並從這些位置載入這些檔案類型[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]運用的擴充性*pack URI 配置*。 本主題提供配置的概觀，說明如何建構組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]各種情況中，討論 absolute 和 relative[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]和[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]解析度，顯示如何使用組件之前[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]從這兩個標記與程式碼。  
  
  
<a name="The_Pack_URI_Scheme"></a>   
## <a name="the-pack-uri-scheme"></a>套件 URI 配置  
 組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]使用配置[開放式封裝慣例](http://go.microsoft.com/fwlink/?LinkID=71255)(OPC) 規格，其中描述來組織及識別內容的模型。 索引鍵的項目，此模型會封裝和組件，其中*封裝*是邏輯的容器，其中一個或多個邏輯*部分*。 下圖說明這個概念。  
  
 ![套件和組件圖表](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")  
  
 若要識別組件，OPC 規格會利用 RFC 2396 的擴充性 (統一資源識別項 (URI): 一般語法) 來定義組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]配置。  
  
 所指定的配置[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]定義其前置詞，由 http、 ftp 和檔案是已知的範例。 組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]配置做為其配置中，使用 「 組件 」，以及包含兩個元件： 授權和路徑。 以下是組件的格式[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  
  
 組件: / /*授權*/*路徑*
  
 *授權*指定封裝的一部分，所包含的型別時*路徑*指定組件在封裝內的位置。  
  
 下圖說明這個概念︰  
  
 ![套件、授權和路徑之間的關聯性](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")  
  
 套件和組件與應用程式和檔案類似，其中應用程式 (套件) 可以包括一或多個檔案 (組件)，包括︰  
  
-   編譯為本機組件的資源檔。  
  
-   編譯為所參考組件的資源檔。  
  
-   編譯為參考組件的資源檔。  
  
-   內容檔。  
  
-   來源網站檔案。  
  
 若要存取這些類型的檔案，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]支援兩個授權單位： 應用程式: / / 和 siteoforigin: / /。 application:/// 授權識別在編譯時期已知的應用程式資料檔，包括資源檔和內容檔。 siteoforigin:/// 授權識別來源網站檔案。 下圖顯示每個授權的範圍。  
  
 ![套件 URI 圖表](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")  
  
> [!NOTE]
>  組件的授權元件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]是內嵌[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]，指向封裝，而且必須符合 RFC 2396。 此外，"/" 字元必須取代為 "," 字元，而且必須逸出 "%" 和 "?" 這類保留字元。 如需詳細資料，請參閱 OPC。  
  
 下列各節將說明如何建構組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]識別資源、 內容和來源網站檔搭配適當的路徑中使用這些兩個授權單位。  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## <a name="resource-file-pack-uris"></a>資源檔套件 URI  
 資源檔會設定為[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Resource`項目，並編譯成組件。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 支援的組件建構[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，可以用來識別資源檔編譯為本機的組件或編譯的組件參考的本機組件。  
  
<a name="Local_Assembly_Resource_File"></a>   
### <a name="local-assembly-resource-file"></a>本機組件資源檔  
 組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]資源編譯成本機組件的檔案會使用下列的授權和路徑：  
  
-   **授權**：application:///。  
  
-   **路徑**︰相對於本機組件專案資料夾根之資源檔的名稱，包括其路徑。  
  
 下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]位於本機的組件的專案資料夾的根目錄中的資源檔。  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]位於本機的組件的專案資料夾的子資料夾中的資源檔。  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### <a name="referenced-assembly-resource-file"></a>所參考的組件資源檔  
 組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]資源編譯成參考的組件的檔案會使用下列的授權和路徑：  
  
-   **授權**：application:///。  
  
-   **路徑**：編譯為所參考組件之資源檔的名稱。 路徑必須符合下列格式：  
  
     *AssemblyShortName*{*;版本*] {*;PublicKey*]; component /*路徑*  
  
    -   **AssemblyShortName**：所參考組件的簡短名稱。  
  
    -   **;Version** [選擇性]：包含資源檔之參考組件的版本。 這是在載入具有相同簡短名稱的兩個以上參考組件時使用。  
  
    -   **;PublicKey** [選擇性]：用來簽署參考組件的公開金鑰。 這是在載入具有相同簡短名稱的兩個以上參考組件時使用。  
  
    -   **;component**︰指定從本機組件參考所參考的組件。  
  
    -   **/Path**︰相對於所參考組件專案資料夾根之資源檔的名稱，包括其路徑。  
  
 下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]位於參考組件的專案資料夾的根目錄中的資源檔。  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]位於參考組件的專案資料夾的子資料夾中的資源檔。  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]位於根資料夾的參考、 版本特定組件的專案資料夾中的資源檔。  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 請注意，此組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考的組件資源檔案的語法只能搭配應用程式: / / 授權。 例如，下列不支援[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]。  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## <a name="content-file-pack-uris"></a>內容檔套件 URI  
 組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]內容檔案所使用的下列授權和路徑：  
  
-   **授權**：application:///。  
  
-   **路徑**：內容檔的名稱，包括其相對於應用程式主要可執行組件之檔案系統位置的路徑。  
  
 下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]位於與可執行的組件相同的資料夾中的內容檔案。  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]位於相對於應用程式的可執行組件的子資料夾的內容檔案。  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  無法巡覽至 [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] 內容檔。 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]配置僅支援巡覽至[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]位於來源的站台上的檔案。  
  
<a name="The_siteoforigin_____Authority"></a>   
## <a name="site-of-origin-pack-uris"></a>來源網站套件 URI  
 組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]的來源站台的檔案會使用下列的授權和路徑：  
  
-   **授權**：siteoforigin:///。  
  
-   **路徑**：來源網站檔案的名稱，包括其相對於從中啟動可執行組件之位置的路徑。  
  
 下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]站台的來源檔案，儲存在從中啟動可執行的組件的位置。  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]站台的來源檔案，儲存在啟動應用程式的可執行組件時的位置相對的子資料夾。  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## <a name="page-files"></a>分頁檔  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 設定為檔案[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page`項目做為資源檔相同的方式，會編譯成組件。 因此， [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page`項目可以使用組件識別[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]資源檔。  
  
 類型的[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案通常會設定為[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page`項目具有下列項目當做其根元素的其中一個：  
  
-   <xref:System.Windows.Window?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## <a name="absolute-vs-relative-pack-uris"></a>絕對與相對套件 URI  
 完整的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]包含配置、 授權和路徑，且其被視為絕對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。 為開發人員簡化[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]項目通常可讓您設定適當的屬性與相對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]，其中包括只有路徑。  
  
 例如，請考慮下列絕對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]本機的組件中的資源檔。  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 相對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考這個資源檔會是如下所示。  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  因為站台的來源檔案不是組件相關聯，可以只參考這些絕對 pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]。  
  
 根據預設，相對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]會被視為相對於包含參考的程式碼之標記的位置。 如果使用前置反斜線，不過，相對於組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考則視為相對於應用程式的根目錄。 例如，請考慮下列專案結構。  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 如果包含 Page1.xaml[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考*根*\SubFolder\Page2.xaml，參考可以使用下列相對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  
  
 `Page2.xaml`  
  
 如果包含 Page1.xaml[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考*根*\Page2.xaml，參考可以使用下列相對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## <a name="pack-uri-resolution"></a>套件 URI 解析  
 組件的格式[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]組件可能會讓[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]不同類型的檔案相同的外觀。 例如，請考慮下列絕對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 此絕對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]無法參考本機的組件中的資源檔案或內容檔案。 也適用於下列相對[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  
  
 `/ResourceOrContentFile.xaml`  
  
 若要判斷類型檔案的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]指的是，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]解析[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]本機的組件和使用下列啟發學習法的內容檔案中的資源檔：  
  
1.  探查的組件中繼資料<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>符合組件的屬性[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  
  
2.  如果<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>發現屬性時，組件的路徑[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]所參考的內容檔案。  
  
3.  如果<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>找不到屬性、 探查組資源檔編譯成本機組件。  
  
4.  如果符合的組件路徑的資源檔案[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]為找到的組件的路徑[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]指的是資源檔。  
  
5.  如果資源找不到，在內部建立<xref:System.Uri>無效。  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 解析不適用於[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，請參考下列：  
  
-   內容中參考的組件檔案： 這些檔案類型不支援[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]。  
  
-   參考組件中內嵌檔案： [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] ，識別這些是唯一的因為它們包含參考的組件名稱和`;component`後置詞。  
  
-   站台的來源檔案： [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] ，識別這些是唯一的因為它們是可以由組件的唯一檔案[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]包含 siteoforigin: / / 授權。  
  
 組件的一個簡化[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]解析可讓適用於程式碼稍微獨立的資源和內容檔案的位置。 例如，如果您有會重新設定為內容檔，將組件的本機組件中的資源檔[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]資源維持不變，如同使用組件的程式碼的[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  
  
<a name="Programming_with_Pack_URIs"></a>   
## <a name="programming-with-pack-uris"></a>使用套件 URI 的程式設計  
 許多[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]類別會實作可設定與組件屬性[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，包括：  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>  
  
 可以透過標記和程式碼來設定這些屬性。 本節示範兩者的基本建構，並顯示常見案例的範例。  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### <a name="using-pack-uris-in-markup"></a>透過標記使用套件 URI  
 組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]設定具有組件之屬性的項目，來指定在標記中[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。 例如:   
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 表 1 說明各種絕對的組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，您可以指定在標記中。  
  
 表 1：使用標記的絕對套件 URI  
  
|檔案|絕對的組件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
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
  
 表 2 說明各種相對的組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，您可以指定在標記中。  
  
 表 2：使用標記的相對套件 URI  
  
|檔案|相對的組件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|本機組件中的資源檔|`"/ResourceFile.xaml"`|  
|本機組件子資料夾中的資源檔|`"/Subfolder/ResourceFile.xaml"`|  
|參考組件中的資源檔|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|參考組件之子資料夾中的資源檔|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|內容檔|`"/ContentFile.xaml"`|  
|子資料夾中的內容檔|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### <a name="using-pack-uris-in-code"></a>透過程式碼使用套件 URI  
 指定的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]藉由執行個體化的程式碼中<xref:System.Uri>類別，並傳遞此組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]做為參數的建構函式。 這點在下列範例中示範。  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 根據預設，<xref:System.Uri>類別會考慮的組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]為絕對。 因此，發生例外狀況時的執行個體<xref:System.Uri>類別建立與相對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 幸運的是，<xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29>多載<xref:System.Uri>類別建構函式接受類型的參數<xref:System.UriKind>可讓您指定是否將組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]是絕對或相對。  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml",   
                        UriKind.Relative);  
```  
  
 您應該只指定<xref:System.UriKind.Absolute>或<xref:System.UriKind.Relative>會確認提供的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]是其中一個。 如果您不知道組件的型別[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]用，例如當使用者輸入組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]執行階段使用<xref:System.UriKind.RelativeOrAbsolute>改為。  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 表 3 說明各種相對的組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，您可以指定在程式碼中使用<xref:System.Uri?displayProperty=nameWithType>。  
  
 表 3：使用程式碼的絕對套件 URI  
  
|檔案|絕對的組件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
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
  
 表 4 說明各種相對的組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，您可以指定在程式碼中使用<xref:System.Uri?displayProperty=nameWithType>。  
  
 表 4：使用程式碼的相對套件 URI  
  
|檔案|相對的組件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|資源檔 - 本機組件|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|子資料夾中的資源檔 - 本機組件|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|資源檔 - 參考組件|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|子資料夾中的資源檔 - 參考組件|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|內容檔|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|子資料夾中的內容檔|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### <a name="common-pack-uri-scenarios"></a>常見套件 URI 案例  
 如前幾節討論了如何建構組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]來識別資源、 內容和來源檔案的站台。 在[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、 這些語法結構用於各種不同的方式，以及下列各節涵蓋數個常見的使用方式。  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>指定要在啟動應用程式時顯示的 UI  
 <xref:System.Windows.Application.StartupUri%2A> 指定第一個[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]以顯示[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]啟動應用程式。 對於獨立應用程式，[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]可以是一個視窗中，如下列範例所示。  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 獨立應用程式和[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]也可以指定頁面做為初始的 UI 中，如下列範例所示。  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 如果應用程式是一個獨立應用程式，並指定頁面<xref:System.Windows.Application.StartupUri%2A>，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]開啟<xref:System.Windows.Navigation.NavigationWindow>裝載的網頁。 如[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]，網頁會顯示主機瀏覽器中。  
  
<a name="Navigating_to_a_Page"></a>   
#### <a name="navigating-to-a-page"></a>巡覽至頁面  
 下列範例示範如何巡覽至頁面。  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 如需詳細資訊，以各種方式來巡覽程式[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，請參閱[巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。  
  
<a name="Specifying_a_Window_Icon"></a>   
#### <a name="specifying-a-window-icon"></a>指定視窗圖示  
 下列範例示範如何使用 URI 來指定視窗的圖示。  
  
 [!code-xaml[WindowIconSnippets#WindowIconSetXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 如需詳細資訊，請參閱<xref:System.Windows.Window.Icon%2A>。  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### <a name="loading-image-audio-and-video-files"></a>載入影像、音訊和視訊檔案  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 可讓應用程式中使用各種不同的媒體類型，其中可以識別和使用組件載入[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，如下列範例所示。  
  
 [!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xaml[ImageSample#ImagePackURIContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 如需使用媒體內容的詳細資訊，請參閱[圖形和多媒體](../../../../docs/framework/wpf/graphics-multimedia/index.md)。  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>從來源網站載入資源字典  
 資源字典 (<xref:System.Windows.ResourceDictionary>) 可以用來支援應用程式佈景主題。 建立和管理主題的一種方法是將多個主題建立為位在應用程式來源網站的資源字典。 這樣可新增和更新主題，而不需要重新編譯和重新部署應用程式的。 這些資源字典可以識別，並且使用組件載入[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，這下列範例所示。  
  
 [!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 如需在佈景主題的概觀[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
## <a name="see-also"></a>另請參閱  
 [WPF 應用程式資源、內容和資料檔案](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
