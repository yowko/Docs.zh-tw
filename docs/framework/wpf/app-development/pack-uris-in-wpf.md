---
title: "WPF 中的 Pack URI | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "應用程式管理 [WPF]"
  - "載入內嵌資源"
  - "載入非資源檔"
  - "Pack URI 配置"
  - "統一資源識別元 (URI)"
  - "URI (統一資源識別元)"
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
caps.latest.revision: 35
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 31
---
# WPF 中的 Pack URI
在 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 中，[!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] 可透過許多方式識別及載入檔案，包括：  
  
-   指定應用程式第一次啟動時所顯示的[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。  
  
-   載入影像。  
  
-   巡覽至頁面。  
  
-   載入不可執行的資料檔案。  
  
 此外，[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 也可用來識別及載入來自各種位置的檔案，包括：  
  
-   目前的組件 \(Assembly\)。  
  
-   受參考的組件。  
  
-   相對於組件的位置。  
  
-   應用程式的來源網站。  
  
 為了提供一致的機制，供使用者從這些位置識別及載入這些檔案類型，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 利用了「*Pack URI 配置*」\(Pack URI Scheme\) 的擴充性。  本主題提供這種配置的概觀，內容涵蓋如何針對各種案例建構 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，並討論絕對和相對 [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 以及 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 解析，最後再說明如何從標記和程式碼使用 [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]。  
  
   
  
<a name="The_Pack_URI_Scheme"></a>   
## Pack URI 配置  
 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 配置可供[開放式封裝慣例](http://go.microsoft.com/fwlink/?LinkID=71255) \(OPC\) 規格使用，以描述用來組織及識別內容的模型。  這個模型的主要項目包括封裝 \(Package\) 和組件 \(Part\)，其中「*封裝*」\(Package\) 是一個或多個「*組件*」\(Part\) 的邏輯容器 \(Container\)。  下圖說明這個概念。  
  
 ![套件和部分圖表](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.png "WPFPackURISchemeFigure1")  
  
 為了識別組件，OPC 規格利用 RFC 2396 \(Uniform Resource Identifiers \(URI\): Generic Syntax\) 來定義 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 配置。  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 指定的配置是由其前置字元所定義；http、ftp 和 file 都是已知的範例。  Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 配置使用 "Pack" 做為其配置，其中包含兩個元件：授權和路徑。  Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 的格式如下：  
  
 pack:\/\/*authority*\/*path*  
  
 *authority* \(授權\) 指定包含組件之封裝的類型，而 *path* \(路徑\) 則指定組件在封裝內的位置。  
  
 下圖說明這個概念：  
  
 ![套件、授權和路徑之間的關聯性](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.png "WPFPackURISchemeFigure2")  
  
 封裝和組件類似於應用程式和檔案，而其中應用程式 \(封裝\) 可以包含一個或多個檔案 \(組件\)，包括：  
  
-   編譯成本機組件 \(Assembly\) 的資源檔。  
  
-   編譯成受參考組件 \(Referenced Assembly\) 的資源檔。  
  
-   編譯成參考組件 \(Referencing Assembly\) 的資源檔。  
  
-   內容檔。  
  
-   來源網站檔。  
  
 為了存取這些檔案類型，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 支援兩種授權：application:\/\/\/ 和 siteoforigin:\/\/\/。  application:\/\/\/ 授權可識別編譯時期已知的應用程式資料檔案，包括資源檔和內容檔。  siteoforigin:\/\/\/ 授權可識別來源網站檔。  下圖顯示每個授權的範圍。  
  
 ![封裝 URI 圖表](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")  
  
> [!NOTE]
>  Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 的授權單位元件是內嵌的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]，會指向封裝且必須符合 RFC 2396。  此外，"\/" 字元必須取代為 "," 字元，且保留字元如 "%" 和 "?" 必須逸出。  如需詳細資訊，請參閱 OPC。  
  
 下列各節說明如何使用這兩種授權並結合適當的路徑來建構 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，以用於識別資源檔、內容檔和來源網站檔。  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## 資源檔 Pack URI  
 資源檔會設定為 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource` 項目，並且編譯成組件。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 支援建構可用來識別資源檔的 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，不論該資源檔是編譯成本機組件，還是編譯成從本機組件參考的組件。  
  
<a name="Local_Assembly_Resource_File"></a>   
### 本機組件資源檔  
 編譯成本機組件之資源檔的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 使用下列授權和路徑：  
  
-   **授權**：application:\/\/\/。  
  
-   **路徑**：資源檔的名稱，包括其路徑 \(相對於本機組件專案資料夾根目錄\)。  
  
 下列範例顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 資源檔的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]；其中的資源檔位於本機組件之專案資料夾的根目錄中。  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 下列範例顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 資源檔的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]；其中的資源檔位於本機組件之專案資料夾的子資料夾中。  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### 受參考的組件資源檔  
 編譯成受參考組件之資源檔的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 使用下列授權和路徑：  
  
-   **授權**：application:\/\/\/。  
  
-   **路徑**：編譯成受參考組件之資源檔的名稱。  此路徑必須符合下列格式：  
  
     *AssemblyShortName*\[*;Version*\]\[*;PublicKey*\];component\/*Path*  
  
    -   **AssemblyShortName**：受參考組件的簡短名稱。  
  
    -   **;Version** \[選擇項\]：包含資源檔案的受參考組件版本。  載入兩個以上簡短名稱相同的受參考組件時，就會使用這個項目。  
  
    -   **;PublicKey** \[選擇項\]：用來簽署受參考組件的公開金鑰 \(Public Key\)。  載入兩個以上簡短名稱相同的受參考組件時，就會使用這個項目。  
  
    -   **;component**：指定被參考的組件其參考來源是本機組件。  
  
    -   **\/Path**：資源檔的名稱，包括其路徑 \(相對於受參考組件之專案資料夾根目錄\)。  
  
 下列範例顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 資源檔的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]；其中的資源檔位於受參考組件之專案資料夾的根目錄中。  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 下列範例顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 資源檔的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]；其中的資源檔位於受參考組件之專案資料夾的子資料夾中。  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 下列範例顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 資源檔的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]；其中的資源檔位於受參考之特定版本組件其專案資料夾的根資料夾中。  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 請注意，受參考組件資源檔的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 語法只能與 application:\/\/\/ 授權搭配使用。  例如，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 不支援下列語法。  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## 內容檔 Pack URI  
 內容檔的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 使用下列授權和路徑：  
  
-   **授權**：application:\/\/\/。  
  
-   **路徑**：內容檔的名稱，包括其路徑 \(相對於應用程式主要可執行組件的系統位置\)。  
  
 下列範例顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 內容檔的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]；其中的內容檔位於與可執行組件相同的資料夾中。  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 下列範例顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 內容檔的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]；其中的內容檔位於應用程式之可執行組件的相對子資料夾中。  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  您不能巡覽至 [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] 內容檔。  [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 配置只支援巡覽至位於來源網站的 [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] 檔案。  
  
<a name="The_siteoforigin_____Authority"></a>   
## 來源網站 Pack URI  
 來源網站的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 使用下列授權和路徑：  
  
-   **授權**：siteoforigin:\/\/\/。  
  
-   **路徑**：來源網路檔的名稱，包括其路徑 \(相對於可執行組件的啟動位置\)。  
  
 下列範例顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 來源網站檔的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]；其中的來源網站檔儲存在可執行組件的啟動位置中。  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 下列範例顯示 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 來源網站檔的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]；其中的來源網站檔儲存在應用程式可執行組件啟動位置的相對子資料夾中。  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## 分頁檔  
 設定為 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` 項目的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案編譯成組件的方式與資源檔相同。  因此，[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` 項目可以使用資源檔的 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 來識別。  
  
 通常設定成 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page` 項目的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案具有下列其中一個根項目 \(Root Element\)：  
  
-   <xref:System.Windows.Window?displayProperty=fullName>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=fullName>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=fullName>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=fullName>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=fullName>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=fullName>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## 絕對與相對 Pack URI 的比較  
 完整的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 包括配置、授權和路徑，而且會被視為絕對 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  為了簡化程式開發人員的工作，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 項目通常允許您使用只包含路徑的相對 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 來設定適當的屬性 \(Attribute\)。  
  
 例如，以本機組件中資源檔的下列絕對 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 為例：  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 指向此資源檔的相對 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 如下：  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  因為來源網站檔與組件無關，所以這些檔案只能以絕對 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 來參考。  
  
 根據預設，相對 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 應該與內含參考之標記或程式碼的位置相對。  不過，如果使用前置反斜線，則相對 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 參考則應該是相對於應用程式的根目錄。  例如，以下列專案結構為例：  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 如果 Page1.xaml 包含參考 *Root*\\SubFolder\\Page2.xaml 的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]，則此參考可以使用下列相對 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  
  
 `Page2.xaml`  
  
 如果 Page1.xaml 包含參考 *Root*\\Page2.xaml 的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]，此參考便可使用下列相對 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## Pack URI 解析  
 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 的格式使得不同檔案類型的 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 看起來可能完全相同。  例如，若以下列絕對 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 為例：  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 這個絕對 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 可以參考至本機組件中的資源檔或內容檔。  同樣的情況也適用於下列相對 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]：  
  
 `/ResourceOrContentFile.xaml`  
  
 為了判斷 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 所參考的檔案類型，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 會使用下列啟發方式解析本機組件中資源檔以及內容檔的 [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]：  
  
1.  探查符合 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 之 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 屬性的組件中繼資料 \(Metadata\)。  
  
2.  如果找到 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 屬性，Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 的路徑就會參考到內容檔。  
  
3.  如果找不到 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 屬性，則請探查編譯成本機組件的已設定資源檔。  
  
4.  如果找到符合 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 路徑的資源檔，Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 的路徑就會參考到資源檔。  
  
5.  如果找不到資源，內部建立的 <xref:System.Uri> 便無效。  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 解析不適用於參考下列項目的 [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]：  
  
-   受參考組件中的內容檔：[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 不支援這些檔案類型。  
  
-   受參考組件中的內嵌檔案：識別這些檔案的 [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 是唯一的，因為它們同時包含了受參考組件的名稱和 `;component` 後置字元。  
  
-   來源網站檔：識別這些檔案的 [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 是唯一的，因為它們是包含 siteoforigin:\/\/\/ 授權之 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 唯一可以識別的檔案。  
  
 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 解析可以接受的一種簡化方式是讓程式碼在某種程度上不受資源檔和內容檔的位置影響。  例如，如果您將本機組件中的資源檔重新設定為內容檔，該資源的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 將維持不變，就像使用 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 的程式碼一樣。  
  
<a name="Programming_with_Pack_URIs"></a>   
## 使用 Pack URI 進行程式設計  
 許多 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 類別都實作可以使用 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 設定的屬性，包括：  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=fullName>  
  
 這些屬性都可以從標記和程式碼設定。  本節示範兩者的基本建構，然後再顯示常見案例的範例。  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### 在標記中使用 Pack URI  
 在標記中指定 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 的方式是使用 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 設定屬性的項目。  例如：  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 表 1 說明可以在標記中指定的各種絕對 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]。  
  
 表 1：標記中的絕對 Pack URI  
  
|檔案|絕對 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|--------|--------------------------------------------------------------------------|  
|資源檔 \- 本機組件|`"pack://application:,,,/ResourceFile.xaml"`|  
|子資料夾中的資源檔 \- 本機組件|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|資源檔 \- 參考的組件|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|子資料夾中的資源檔 \- 參考的組件|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|已建立版本之受參考組件中的資源檔|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|內容檔|`"pack://application:,,,/ContentFile.xaml"`|  
|子資料夾中的內容檔|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|來源網站檔|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|子資料夾中的來源網站檔|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 表 2 說明可以在標記中指定的各種相對 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]。  
  
 表 2：標記中的相對 Pack URI  
  
|檔案|相對 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|--------|--------------------------------------------------------------------------|  
|本機組件中的資源檔|`"/ResourceFile.xaml"`|  
|本機組件子資料夾中的資源檔|`"/Subfolder/ResourceFile.xaml"`|  
|受參考組件中的資源檔|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|子資料夾中的資源檔 \- 參考的組件|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|內容檔|`"/ContentFile.xaml"`|  
|子資料夾中的內容檔|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### 在程式碼中使用 Pack URI  
 在程式碼中指定 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 的方式是執行個體化 <xref:System.Uri> 類別，並將 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 當做參數傳遞至建構函式 \(Constructor\)。  這點在下列範例中示範。  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 依預設，<xref:System.Uri> 類別會將 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 視為絕對路徑。  因此，使用相對 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 建立 <xref:System.Uri> 類別的執行個體 \(Instance\) 時，將會引發例外狀況 \(Exception\)。  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 但幸好 <xref:System.Uri> 類別建構函式的 <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> 多載可接受型別 <xref:System.UriKind> 的參數，使您可以指定 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 是絕對還是相對路徑。  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml", UriKind.Relative);  
```  
  
 當您確定提供的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 是絕對或相對路徑時，只能指定 <xref:System.UriKind> 或 <xref:System.UriKind>。  如果您不知道使用的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 類型 \(例如在使用者於執行階段中輸入 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 時\)，請改用 <xref:System.UriKind>。  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 表 3 說明可以使用 <xref:System.Uri?displayProperty=fullName> 在程式碼中指定的各種絕對 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]。  
  
 表 3：程式碼中的絕對 Pack URI  
  
|檔案|絕對 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|--------|--------------------------------------------------------------------------|  
|資源檔 \- 本機組件|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|子資料夾中的資源檔 \- 本機組件|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|資源檔 \- 參考的組件|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|子資料夾中的資源檔 \- 參考的組件|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|已建立版本之受參考組件中的資源檔|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|內容檔|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|子資料夾中的內容檔|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|來源網站檔|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|子資料夾中的來源網站檔|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 表 4 說明可以使用 <xref:System.Uri?displayProperty=fullName> 在程式碼中指定的各種相對 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]。  
  
 表 4：程式碼中的相對 Pack URI  
  
|檔案|相對 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|--------|--------------------------------------------------------------------------|  
|資源檔 \- 本機組件|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|子資料夾中的資源檔 \- 本機組件|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|資源檔 \- 參考的組件|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|子資料夾中的資源檔 \- 受參考的組件|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|內容檔|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|子資料夾中的內容檔|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### 常見的 Pack URI 案例  
 前面各節已經討論如何建構 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 來識別資源、內容和來源網站等檔案。  在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，這些建構有各種不同的使用方式，下列各節僅涵蓋幾個較常見的使用方式。  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### 指定應用程式啟動時所顯示的 UI  
 <xref:System.Windows.Application.StartupUri%2A> 可指定 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式啟動時顯示的第一個 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。  在獨立應用程式中，這個 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 可能是視窗，如下列範例所示。  
  
 [!code-xml[PackURIOverviewSnippets#StartupUriWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 獨立應用程式 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] 也可以指定頁面做為初始 UI，如下列範例所示。  
  
 [!code-xml[PackURIOverviewSnippets#StartupUriPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 如果應用程式是獨立應用程式，而且使用 <xref:System.Windows.Application.StartupUri%2A> 指定了頁面，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 將會開啟 <xref:System.Windows.Navigation.NavigationWindow> 來裝載該頁面。  若為 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]，此頁面會顯示在主瀏覽器中。  
  
<a name="Navigating_to_a_Page"></a>   
#### 巡覽至頁面  
 下列範例示範如何巡覽至頁面。  
  
 [!code-xml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 如需 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中各種巡覽方式的詳細資訊，請參閱[巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。  
  
<a name="Specifying_a_Window_Icon"></a>   
#### 指定視窗圖示  
 下列範例示範如何使用 URI 指定視窗的圖示。  
  
 [!code-xml[WindowIconSnippets#WindowIconSetXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 如需詳細資訊，請參閱 <xref:System.Windows.Window.Icon%2A>。  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### 載入影像、音訊和視訊檔案  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 允許應用程式使用各種媒體類型，而且所有的媒體類型都可以使用 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 識別及載入，如下列各範例所示。  
  
 [!code-xml[MediaPlayerVideoSample#VideoPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xml[MediaPlayerAudioSample#AudioPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xml[ImageSample#ImagePackURIContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 如需使用媒體內容的詳細資訊，請參閱 [圖形和多媒體](../../../../docs/framework/wpf/graphics-multimedia/index.md)。  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### 從來源網站載入資源字典  
 資源字典 \(<xref:System.Windows.ResourceDictionary>\) 可用來支援應用程式佈景主題。  其中一種建立及管理佈景主題的方式是建立多個佈景主題，做為位於網站來源的資源字典，  如此您就可以新增及更新佈景主題，而不需要重新編譯及重新部署應用程式。  這些資源字典都可以使用 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 來識別及載入，如下列範例所示。  
  
 [!code-xml[ResourceDictionarySnippets#ResourceDictionaryPackURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 如需 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中佈景主題的概觀，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。  
  
## 請參閱  
 [WPF 應用程式資源、內容和資料檔案](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)