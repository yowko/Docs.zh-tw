---
title: "WPF 應用程式資源、內容和資料檔案"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], files
- loose resources [WPF]
- content files [WPF]
- Site of Origin files [WPF]
- resource files [WPF]
- remote files [WPF]
- embedded resources [WPF]
- files [WPF]
- referencing application files [WPF]
- application development [WPF], files
- application management [WPF]
ms.assetid: 7ad2943b-3961-41d3-8fc6-1582d43f5d99
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 284c3b6788fd43a10d65cfa8bd6c032e4b1e1cd6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-application-resource-content-and-data-files"></a>WPF 應用程式資源、內容和資料檔案
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]應用程式通常取決於檔案包含非可執行檔的資料，例如[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、 影像、 視訊和音訊。 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 提供設定、識別及使用這些資料檔案類型 (稱為應用程式資料檔案) 的特殊支援。 這項支援是以一組特定的應用程式資料檔案類型為中心，包括：  
  
-   **資源檔**： 資料檔案會編譯到可執行檔或程式庫[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]組件。  
  
-   **內容檔案**： 獨立可執行檔與明確相關聯的資料檔案[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]組件。  
  
-   **來源網站檔**： 獨立與可執行檔沒有關聯的資料檔案[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]組件。  
  
 這三種檔案類型之間的其中一個重要區別是資源檔和內容檔是建置階段的已知檔案；組件並明確知道這兩種檔案。 站台上的來源檔案，不過，組件可能完全不知道它們，或透過組件的隱含知識[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]參考，後者的情況下不保證來源檔案的參照站台確實存在。  
  
 若要參考的應用程式資料檔案，[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]使用組件[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]配置，這會在將詳細說明[WPF 中的組件 Uri](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md))。  
  
 本主題描述何設定及使用應用程式資料檔案。  
  
  
<a name="Resource_Files"></a>   
## <a name="resource-files"></a>資源檔  
 若應用程式資料檔案必須一律可供應用程式使用，確保可用性的唯一方法是將檔案編譯成應用程式的主要可執行檔組件或是應用程式的其中一個參考組件。 這種類型的應用程式資料檔稱為*資源檔*。  
  
 應該使用資源檔的時機包括：  
  
-   您不需要在資源檔編譯成組件之後更新該檔案的內容。  
  
-   您想要透過減少檔案相依性數目的方式，簡化複雜的應用程式發佈程序。  
  
-   必須是可當地語系化應用程式資料檔 (請參閱[WPF 全球化和當地語系化概觀](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md))。  
  
> [!NOTE]
>  本節中所述的資源檔案為不同的資源檔中所述[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)不同於中所述的內嵌或連結的資源和[管理應用程式資源 (.NET)](http://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).  
  
### <a name="configuring-resource-files"></a>設定資源檔  
 在[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，資源檔是包含在檔案[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]專案做為`Resource`項目。  
  
```xml  
<Project "xmlns=http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  在[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，您建立資源檔加入檔案加入專案，並設定其`Build Action`至`Resource`。  
  
 建立專案時，[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]將資源編譯成組件。  
  
### <a name="using-resource-files"></a>使用資源檔  
 若要載入的資源檔，您可以呼叫<xref:System.Windows.Application.GetResourceStream%2A>方法<xref:System.Windows.Application>類別，傳遞到組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]可識別所需的資源檔。 <xref:System.Windows.Application.GetResourceStream%2A>傳回<xref:System.Windows.Resources.StreamResourceInfo>物件，它會公開資源檔案儲存為<xref:System.IO.Stream>並描述其內容的型別。  
  
 例如，下列程式碼會示範如何使用<xref:System.Windows.Application.GetResourceStream%2A>載入<xref:System.Windows.Controls.Page>資源檔案，並將它設為內容的<xref:System.Windows.Controls.Frame>(`pageFrame`):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 呼叫<xref:System.Windows.Application.GetResourceStream%2A>可讓您存取<xref:System.IO.Stream>，您必須執行將它轉換成您要設定其與屬性類型的其他工作。 相反地，您可以讓[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]小心開啟，並將轉換<xref:System.IO.Stream>由直接將資源檔載入使用程式碼類型的屬性。  
  
 下列範例示範如何載入<xref:System.Windows.Controls.Page>直接<xref:System.Windows.Controls.Frame>(`pageFrame`) 使用程式碼。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 下列範例相當於前一個範例的標記對等用法。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>應用程式程式碼檔案作為資源檔  
 特殊設定的[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式程式碼檔案可以使用組件參考[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，包括 windows、 頁面、 固定格式文件，以及資源字典。 例如，您可以設定<xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>與組件屬性[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]視窗或您想要應用程式啟動時載入的頁面參考。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 您可以執行時[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案是否併入[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]專案做為`Page`項目。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Page Include="MainWindow.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  在[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]，您將新<xref:System.Windows.Window>， <xref:System.Windows.Navigation.NavigationWindow>， <xref:System.Windows.Controls.Page>， <xref:System.Windows.Documents.FlowDocument>，或<xref:System.Windows.ResourceDictionary>加入專案，`Build Action`標記檔案將會預設為`Page`。  
  
 當在專案中使用`Page`編譯項目時，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]項目會轉換成二進位格式，並編譯為相關聯的組件。 因此，這些檔案可以比照一般資源檔的方式來使用。  
  
> [!NOTE]
>  如果[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案設定為`Resource`項目，而且沒有程式碼後置檔案，原始[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]編譯成組件，而不是未經處理的二進位版本[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>內容檔  
 A*內容檔*分散式成為鬆散以及可執行組件檔案。 雖然這種檔案並未編譯成組件，但是編譯組件時使用的中繼資料會建立與每個內容檔的關聯。  
  
 如果應用程式需要一組特定的應用程式資料檔案，而您不想在更新這些檔案時重新編譯使用它們的組件，您應該使用內容檔。  
  
### <a name="configuring-content-files"></a>設定內容檔  
 若要將內容檔案加入專案中，應用程式資料檔必須是包含為`Content`項目。 此外，因為內容檔無法直接編譯成組件，您需要設定[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`CopyToOutputDirectory`中繼資料元素來指定，將內容檔案會複製到建置的組件的相對位置。 如果您想要複製到組建輸出資料夾每次資源建置專案時，您將設定`CopyToOutputDirectory`中繼資料元素與`Always`值。 否則，您可以確定資源的最新版本複製到組建輸出資料夾，使用`PreserveNewest`值。  
  
 以下顯示設定為內容檔的檔案；只有在將新版本的資源新增至專案時，這個內容檔才會複製到建置輸出資料夾。  
  
```xml  
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
>  在[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]，您建立的內容檔案，將檔案新增至專案並設定其`Build Action`來`Content`，並設定其`Copy to Output Directory`至`Copy always`(相同`Always`) 和`Copy if newer`(相同`PreserveNewest`)。  
  
 建立專案時，<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>屬性會先編譯成組件的每個內容檔案的中繼資料。  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 值<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>表示相對於其位置在專案中的內容檔案的路徑。 例如，如果內容的檔案位於專案的子資料夾中的其他路徑資訊會併入<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>值。  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>值也是組建輸出資料夾中的內容檔案的路徑的值。  
  
### <a name="using-content-files"></a>使用內容檔  
 若要載入的內容檔案，您可以呼叫<xref:System.Windows.Application.GetContentStream%2A>方法<xref:System.Windows.Application>類別，傳遞到組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]可識別所需的內容檔案。 <xref:System.Windows.Application.GetContentStream%2A>傳回<xref:System.Windows.Resources.StreamResourceInfo>物件，它會公開內容的檔案做為<xref:System.IO.Stream>並描述其內容的型別。  
  
 例如，下列程式碼會示範如何使用<xref:System.Windows.Application.GetContentStream%2A>載入<xref:System.Windows.Controls.Page>內容檔案，並將它設為內容的<xref:System.Windows.Controls.Frame>(`pageFrame`)。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 呼叫<xref:System.Windows.Application.GetContentStream%2A>可讓您存取<xref:System.IO.Stream>，您必須執行將它轉換成您要設定其與屬性類型的其他工作。 相反地，您可以讓[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]小心開啟，並將轉換<xref:System.IO.Stream>由直接將資源檔載入使用程式碼類型的屬性。  
  
 下列範例示範如何載入<xref:System.Windows.Controls.Page>直接<xref:System.Windows.Controls.Frame>(`pageFrame`) 使用程式碼。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 下列範例相當於前一個範例的標記對等用法。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>來源網站檔  
 資源檔具有明確的關聯性的方式分配旁邊，組件所定義<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>。 但是在某些情況下，您可能想在組件和應用程式資料檔案之間建立隱含或不存在的關聯性，這些情況包括：  
  
-   編譯時期檔案並不存在。  
  
-   在執行階段之前，您不知道組件需要哪些檔案。  
  
-   您不想在更新檔案時重新編譯其關聯的組件。  
  
-   應用程式使用大型的資料檔案，例如音訊和視訊，而您只想讓使用者自行選擇是否下載這些檔案。  
  
 可以載入這些類型的檔案，使用傳統[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]配置，例如 file:/// 和 http:// 配置。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 不過，file:/// 和 http:// 配置要求應用程式必須受到完全信任。 如果您的應用程式是[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]，從網際網路或內部網路，已啟動，它會要求只允許從這些位置中，啟動應用程式只能從原點 （應用程式的網站載入鬆散檔案的權限集啟動位置）。 這類檔案也稱為*來源網站的*檔案。  
  
 來源網站檔是部分信任應用程式的唯一選擇，但並不是只適用於部分信任應用程式。 完全信任應用程式可能還是需要載入它們在建置階段並不知道的應用程式資料檔案；雖然完全信任應用程式可以使用 file:///，但是應用程式資料檔案可能會安裝在應用程式組件的相同資料夾或子資料夾中。 在此情況下，使用來源網站參考比使用 file:/// 簡單，因為使用 file:/// 時，您必須找出檔案的完整路徑。  
  
> [!NOTE]
>  來源檔案不會快取與網站[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]用戶端的電腦上的內容檔案時。 因此，只有在特別要求時，才會下載來源網站檔。 如果[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]應用程式有大型的媒體檔案，為來源網站檔表示初始應用程式啟動會更快，而且檔案只會視需要下載可對它們進行設定。  
  
### <a name="configuring-site-of-origin-files"></a>設定來源網站檔  
 如果您的網站的來源檔案不存在或無法辨識在編譯時期，您需要使用傳統部署機制，可確保所需的檔案可在執行階段，包括使用`XCopy`命令列程式或[!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].  
  
 如果您知道在編譯時期的檔案，您會想要找的來源站台，但仍想要避免明確的相依性，您可以加入至這些檔案[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]專案做為`None`項目。 為內容檔案時，您需要設定[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`CopyToOutputDirectory`屬性來指定來源檔案的站台，會複製到的位置相對於建置的組件，藉由指定`Always`值或`PreserveNewest`值。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <None Include="PageSiteOfOriginFile.xaml">  
    <CopyToOutputDirectory>Always</CopyToOutputDirectory>  
  </None>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  在[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]，您建立的站台來源檔案將檔案新增至專案並設定其`Build Action`至`None`。  
  
 建立專案時，[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]將指定的檔案複製到組建輸出資料夾。  
  
### <a name="using-site-of-origin-files"></a>使用來源網站檔  
 若要載入的來源檔案的網站，您可以呼叫<xref:System.Windows.Application.GetRemoteStream%2A>方法<xref:System.Windows.Application>類別，傳遞到組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]識別的來源檔案所要的網站。 <xref:System.Windows.Application.GetRemoteStream%2A>傳回<xref:System.Windows.Resources.StreamResourceInfo>物件，它會公開做為來源檔案的站台<xref:System.IO.Stream>並描述其內容的型別。  
  
 例如，下列程式碼會示範如何使用<xref:System.Windows.Application.GetRemoteStream%2A>載入<xref:System.Windows.Controls.Page>來源網站的檔案，並將它設為內容的<xref:System.Windows.Controls.Frame>(`pageFrame`)。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 呼叫<xref:System.Windows.Application.GetRemoteStream%2A>可讓您存取<xref:System.IO.Stream>，您必須執行將它轉換成您要設定其與屬性類型的其他工作。 相反地，您可以讓[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]小心開啟，並將轉換<xref:System.IO.Stream>由直接將資源檔載入使用程式碼類型的屬性。  
  
 下列範例示範如何載入<xref:System.Windows.Controls.Page>直接<xref:System.Windows.Controls.Frame>(`pageFrame`) 使用程式碼。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 下列範例相當於前一個範例的標記對等用法。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>在變更組建類型之後重建  
 在變更應用程式資料檔案的組建類型之後，您必須重建整個應用程式，以確認套用這些變更。 若您只建置應用程式，則不會套用變更。  
  
## <a name="see-also"></a>請參閱  
 [WPF 中的 Pack URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
