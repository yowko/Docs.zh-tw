---
title: "WPF 應用程式資源、內容和資料檔案 | Microsoft Docs"
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
  - "應用程式開發 [WPF], 檔案"
  - "應用程式管理 [WPF]"
  - "內容檔 [WPF]"
  - "內嵌資源 [WPF]"
  - "檔案 [WPF]"
  - "鬆散的資源 [WPF]"
  - "參考應用程式檔案 [WPF]"
  - "遠端檔案 [WPF]"
  - "資源檔 [WPF]"
  - "Site of Origin (SoO) 檔 [WPF]"
  - "WPF 應用程式, 檔案"
ms.assetid: 7ad2943b-3961-41d3-8fc6-1582d43f5d99
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# WPF 應用程式資源、內容和資料檔案
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] 應用程式通常相依於包含非可執行資料的檔案，例如 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、影像、視訊和音訊。  [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 提供設定、識別及使用這些資料檔案類型 \(稱為應用程式資料檔案\) 的特殊支援。  這項支援是以一組特定應用程式資料檔案類型為中心，包括：  
  
-   **資源檔**：編譯成可執行檔或程式庫 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 組件 \(Assembly\) 的資料檔案。  
  
-   **內容檔**：與可執行 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 組件具有明確關聯的獨立資料檔案。  
  
-   **來源網站檔**：與可執行 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 組件沒有關聯的獨立資料檔案。  
  
 這三種檔案類型之間其中一個重要區別是資源檔和內容檔是建置 \(Build\) 階段的已知檔案；組件明確知道這兩種檔案。  不過，組件可能完全不知道來源網站檔，或僅透過[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 參考以隱含方式得知這種檔案；若為後者的情況，則無法保證來源網站檔確實存在。  
  
 為了參考應用程式資料檔案，[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 會使用 Pack [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 配置，這項配置的詳細說明包含在 [WPF 中的 Pack URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md) 中。  
  
 本主題說明如何設定及使用應用程式資料檔案。  
  
   
  
<a name="Resource_Files"></a>   
## 資源檔  
 如果應用程式資料檔案必須永遠可供應用程式使用，確保可用性的唯一方法是將檔案編譯成應用程式的主要可執行組件或是主要可執行組件的一個參考組件。  這種類型的應用程式資料檔案稱為「*資源檔*」\(Resource File\)。  
  
 應該使用資源檔的時機包括：  
  
-   您不需要在資源檔編譯成組件之後更新檔案的內容。  
  
-   您想要透過減少檔案相依項目數目的方式，簡化複雜的應用程式發佈程序。  
  
-   您的應用程式資料檔案必須可以當地語系化 \(請參閱 [WPF 全球化和當地語系化概觀](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)\)。  
  
> [!NOTE]
>  這一節所述的資源檔會與資源檔中所描述的不同[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)不同於所述的內嵌或連結資源和[管理應用程式資源 \(.NET\)](../Topic/Managing%20Application%20Resources%20\(.NET\).md)。  
  
### 設定資源檔  
 在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 中，資源檔是包含在 [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] 專案做為 `Resource` 項目的檔案。  
  
```  
<Project "xmlns=http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  在 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 中建立資源檔的方式是將檔案加入至專案，並將其 `Build Action` 設定為 `Resource`。  
  
 建置專案時，[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] 會將資源編譯為組件。  
  
### 使用資源檔  
 若要載入資源檔，您可以呼叫 <xref:System.Windows.Application> 類別的 <xref:System.Windows.Application.GetResourceStream%2A> 方法，以傳遞識別所需資源檔的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  <xref:System.Windows.Application.GetResourceStream%2A> 會傳回 <xref:System.Windows.Resources.StreamResourceInfo> 物件，此物件會將資源檔公開為 <xref:System.IO.Stream> 並描述其內容類型。  
  
 下列程式碼範例顯示如何使用 <xref:System.Windows.Application.GetResourceStream%2A> 載入 <xref:System.Windows.Controls.Page> 資源檔，並將其設定為 <xref:System.Windows.Controls.Frame> \(`pageFrame`\) 的內容：  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 雖然呼叫 <xref:System.Windows.Application.GetResourceStream%2A> 可以讓您存取 <xref:System.IO.Stream>，但是您還必須執行其他工作，將它轉換成設定時所使用的屬性型別。  您可以使用程式碼將資源檔直接載入至型別的屬性，讓 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 處理開啟和轉換 <xref:System.IO.Stream> 的工作。  
  
 下列範例會示範如何使用程式碼，將 <xref:System.Windows.Controls.Page> 直接載入至 <xref:System.Windows.Controls.Frame> \(`pageFrame`\)。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 下列範例相當於前一個範例的標記對等用法。  
  
 [!code-xml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### 應用程式程式碼做為資源檔  
 您可以使用 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 參考一組特殊的 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 應用程式程式碼檔案，包括視窗、頁面、非固定格式文件和資源字典。  例如，用來設定 <xref:System.Windows.Application.StartupUri%2A?displayProperty=fullName> 屬性的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 可以參考您想在應用程式啟動時載入的視窗或頁面。  
  
 [!code-xml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 您可以在 [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] 專案包含 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案做為 `Page` 項目時執行這項動作。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Page Include="MainWindow.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  在 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 中，您會將新的 <xref:System.Windows.Window>、<xref:System.Windows.Navigation.NavigationWindow>、<xref:System.Windows.Controls.Page>、<xref:System.Windows.Documents.FlowDocument> 或 <xref:System.Windows.ResourceDictionary> 加入至專案，而標記檔案的 `Build Action` 將預設為 `Page`。  
  
 編譯具有 `Page` 項目的專案時，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 項目會轉換為二進位格式並編譯成關聯的組件。  因此，這些檔案可以比照一般資源檔的方式來使用。  
  
> [!NOTE]
>  如果 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 檔案已設定為 `Resource` 項目，而且沒有程式碼後置 \(Code\-Behind\) 的檔案，則原始 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 將會編譯為組件，而非原始 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的二進位版本。  
  
<a name="Content_Files"></a>   
## 內容檔  
 「*內容檔*」\(Content File\) 是以鬆散檔案的形式連同可執行組件一併發佈。  雖然這種檔案並未編譯成組件，但是編譯組件時使用的中繼資料 \(Metadata\) 則會建立與每個內容檔的關聯。  
  
 如果應用程式需要一組特定的應用程式資料檔案，而您不想在更新這些檔案時重新編譯使用它們的組件，您應該使用內容檔。  
  
### 設定內容檔  
 若要將內容檔加入至專案，應用程式資料檔案必須以 `Content` 項目包含其中。  此外，因為內容檔並未直接編譯為組件，所以您也必須設定 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]```CopyToOutputDirectory` 中繼資料項目，指定將內容檔複製到建置組件的相對位置。  如果想在每次建置專案時將資源複製到建置輸出資料夾，請使用 `Always` 值設定 `CopyToOutputDirectory` 中繼資料項目。  另外，您也可以使用 `PreserveNewest` 值，確保系統只會將最新版本的資源複製到建置輸出資料夾。  
  
 以下顯示設定為內容檔的檔案；只有在將新版本的資源加入至專案時，這個內容檔才會複製到建置輸出資料夾。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Content Include="ContentFile.xaml">  
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
    </Content>  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  在 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 中，您可以將檔案加入至專案，並將其 `Build Action` 設定為 `Content`，以建立內容檔，您也可以將內容檔的 `Copy to Output Directory` 設定為 `Copy always` \(與 `Always` 相同\) 和 `Copy if newer` \(與 `PreserveNewest` 相同\)。  
  
 建置專案時，<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 屬性 \(Attribute\) 會編譯為每個內容檔之組件的中繼資料。  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 的值隱含內容檔的路徑，而這個路徑相對於內容檔在專案中的位置。  例如，如果內容檔位於專案子資料夾，額外的路徑資訊便會放入 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 值中。  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 值也是建置輸出資料夾中內容檔的路徑。  
  
### 使用內容檔  
 若要載入內容檔，您可以呼叫 <xref:System.Windows.Application> 類別的 <xref:System.Windows.Application.GetContentStream%2A> 方法，以傳遞識別所需內容檔的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  <xref:System.Windows.Application.GetContentStream%2A> 會傳回 <xref:System.Windows.Resources.StreamResourceInfo> 物件，此物件會將內容檔公開為 <xref:System.IO.Stream> 並描述其內容類型。  
  
 下列程式碼範例顯示如何使用 <xref:System.Windows.Application.GetContentStream%2A> 載入 <xref:System.Windows.Controls.Page> 內容檔，並將其設定為 <xref:System.Windows.Controls.Frame> \(`pageFrame`\) 的內容。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 雖然呼叫 <xref:System.Windows.Application.GetContentStream%2A> 可以讓您存取 <xref:System.IO.Stream>，但是您還必須執行其他工作，將它轉換成設定時所使用的屬性型別。  您可以使用程式碼將資源檔直接載入至型別的屬性，讓 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 處理開啟和轉換 <xref:System.IO.Stream> 的工作。  
  
 下列範例會示範如何使用程式碼，將 <xref:System.Windows.Controls.Page> 直接載入至 <xref:System.Windows.Controls.Frame> \(`pageFrame`\)。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 下列範例相當於前一個範例的標記對等用法。  
  
 [!code-xml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## 來源網站檔  
 資源檔具有與其一併發佈之組件的明確關聯性 \(Relationship\)，如 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 所定義。  但是在某些情況下，您可能想在組件和應用程式資料檔案之間建立隱含或不存在的關聯性，這些情況包括：  
  
-   編譯時期檔案並不存在。  
  
-   在執行階段之前，您不知道組件需要哪些檔案。  
  
-   您不想在更新檔案時重新編譯其關聯的組件。  
  
-   應用程式使用大型的資料檔案，例如音訊和視訊，而您想讓使用者自行選擇是否下載這些檔案。  
  
 您可以使用傳統的 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 配置 \(例如 file:\/\/\/ 和 http:\/\/ 配置\) 來載入這些類型的檔案。  
  
 [!code-xml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 不過，file:\/\/\/ 和 http:\/\/ 配置要求應用程式必須受到完全信任。  如果您的應用程式是從網際網路或內部網路啟動的 [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]，而且它只要求從這些位置啟動之應用程式允許的使用權限集合，鬆散檔案就只能從應用程式的來源網站 \(啟動位置\) 載入。  這類檔案稱為「*來源網站*」\(Site of Origin\) 檔。  
  
 來源網站檔是部分信任應用程式的唯一選擇，但並不是只適用於部分信任應用程式。  完全信任應用程式可能還是需要載入它們在建置階段並不知道的應用程式資料檔案；雖然完全信任應用程式可以使用 file:\/\/\/，但是應用程式資料檔案可能會安裝在應用程式組件的相同資料夾或子資料夾中。  在這種情況下，使用來源網站參考比使用 file:\/\/\/ 簡單，因為使用 file:\/\/\/ 時，您必須找出檔案的路徑。  
  
> [!NOTE]
>  用戶端電腦不會使用 [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] 快取來源網站檔，但會快取內容檔。  因此，只有在特別要求時，才會下載來源網站檔。  如果 [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] 應用程式具有大型的媒體檔案，將這些檔案設定成來源網站檔即表示初始應用程式的啟動速度將會變快，而且只會視需要下載這些檔案。  
  
### 設定來源網站檔  
 如果來源網站檔在編譯時期不存在或未知，您必須使用傳統的部署機制，以確保能夠在執行階段取得需要的檔案，包括使用 `XCopy` 命令列程式或 [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)]。  
  
 如果您在編譯時期並不知道要放在來源網站的檔案，但還是想要避免產生明確相依性，您可以將這些檔案加入至 [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] 專案，做為 `None` 項目。  與內容檔一樣，您必須設定 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` 屬性，透過指定 `Always` 值或 `PreserveNewest` 值，以指定將來源網站檔複製到建置組件的相對位置。  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <None Include="PageSiteOfOriginFile.xaml">  
    <CopyToOutputDirectory>Always</CopyToOutputDirectory>  
  </None>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  在 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 中建立來源網站檔的方式是將檔案加入至專案，並將其 `Build Action` 設定為 `None`。  
  
 建置專案時，[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] 會將指定的檔案複製到建置輸出檔案。  
  
### 使用來源網站檔  
 若要載入來源網站檔案，您可以呼叫 <xref:System.Windows.Application> 類別的 <xref:System.Windows.Application.GetRemoteStream%2A> 方法，以傳遞識別所需來源網站檔案的 Pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。  <xref:System.Windows.Application.GetRemoteStream%2A> 會傳回 <xref:System.Windows.Resources.StreamResourceInfo> 物件，此物件會將來源網站檔案公開為 <xref:System.IO.Stream> 並描述其內容類型。  
  
 下列程式碼範例顯示如何使用 <xref:System.Windows.Application.GetRemoteStream%2A> 載入 <xref:System.Windows.Controls.Page> 來源網站檔，並將其設定為 <xref:System.Windows.Controls.Frame> \(`pageFrame`\) 的內容。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 雖然呼叫 <xref:System.Windows.Application.GetRemoteStream%2A> 可以讓您存取 <xref:System.IO.Stream>，但是您還必須執行其他工作，將它轉換成設定時所使用的屬性型別。  您可以使用程式碼將資源檔直接載入至型別的屬性，讓 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 處理開啟和轉換 <xref:System.IO.Stream> 的工作。  
  
 下列範例會示範如何使用程式碼，將 <xref:System.Windows.Controls.Page> 直接載入至 <xref:System.Windows.Controls.Frame> \(`pageFrame`\)。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 下列範例相當於前一個範例的標記對等用法。  
  
 [!code-xml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## 在變更組建類型之後重建  
 在變更應用程式資料檔案的組建 \(Build\) 類型之後，您必須重建整個應用程式，以確認套用這些變更。  如果您只建置應用程式，將不會套用變更。  
  
## 請參閱  
 [WPF 中的 Pack URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)