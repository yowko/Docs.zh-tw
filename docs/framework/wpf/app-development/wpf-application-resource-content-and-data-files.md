---
title: 應用程式資源、內容和資料檔案
ms.date: 03/30/2017
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
ms.openlocfilehash: f17898972eeef66447060db32bae5fae377b710e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186195"
---
# <a name="wpf-application-resource-content-and-data-files"></a>WPF 應用程式資源、內容和資料檔案
Microsoft Windows 應用程式通常依賴于包含無法執行資料的檔，例如[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，圖像、視頻和音訊。 Windows 演示基礎 （WPF） 為配置、識別和使用這些類型的資料檔案（稱為應用程式資料檔案）提供特殊支援。 這項支援是以一組特定的應用程式資料檔案類型為中心，包括：  
  
- **資源檔**：編譯為可執行檔或庫 WPF 程式集的資料檔案。  
  
- **內容檔**：與可執行 WPF 程式集具有顯式關聯的獨立資料檔案。  
  
- **原始檔案網站**：與可執行 WPF 程式集沒有關聯的獨立資料檔案。  
  
 這三種檔案類型之間的其中一個重要區別是資源檔和內容檔是建置階段的已知檔案；組件並明確知道這兩種檔案。 但是，對於源網站檔，程式集可能根本不了解它們，或者通過包統一資源識別項 （URI） 引用隱式知識;在後一種情況下，不能保證引用的原始檔案網站確實存在。  
  
 為了引用應用程式資料檔案，Windows 演示基礎 （WPF） 使用包統一資源識別項 （URI） 方案，這在[WPF 中的包 URI 中](pack-uris-in-wpf.md)進行了詳細說明。  
  
 本主題描述何設定及使用應用程式資料檔案。  

<a name="Resource_Files"></a>
## <a name="resource-files"></a>資源檔  
 若應用程式資料檔案必須一律可供應用程式使用，確保可用性的唯一方法是將檔案編譯成應用程式的主要可執行檔組件或是應用程式的其中一個參考組件。 這種類型的應用程式資料檔案稱為*資源檔*。  
  
 應該使用資源檔的時機包括：  
  
- 您不需要在資源檔編譯成組件之後更新該檔案的內容。  
  
- 您想要透過減少檔案相依性數目的方式，簡化複雜的應用程式發佈程序。  
  
- 應用程式資料檔案需要可當地語系化（請參閱[WPF 全球化和當地語系化概述](../advanced/wpf-globalization-and-localization-overview.md)）。  
  
> [!NOTE]
> 本節中描述的資源檔與[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)中描述的資源檔不同，與[管理應用程式資源 （.NET）](/visualstudio/ide/managing-application-resources-dotnet)中描述的嵌入或連結資源不同。  
  
### <a name="configuring-resource-files"></a>設定資源檔  
 在 WPF 中，資源檔是作為`Resource`項包含在 Microsoft 生成引擎 （MSBuild） 專案中的檔。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> 在 Visual Studio 中，您可以通過將檔添加到專案並將其`Build Action`設置為`Resource`來創建資源檔。  
  
 生成專案時，MSBuild 會將資源編譯到程式集中。  
  
### <a name="using-resource-files"></a>使用資源檔  
 要載入資源檔，可以調用<xref:System.Windows.Application.GetResourceStream%2A><xref:System.Windows.Application>類的方法，傳遞標識所需資源檔的包 URI。 <xref:System.Windows.Application.GetResourceStream%2A>返回一<xref:System.Windows.Resources.StreamResourceInfo>個物件，該物件將資源檔公開為<xref:System.IO.Stream>，並描述其內容類型。  
  
 例如，以下代碼演示如何使用<xref:System.Windows.Application.GetResourceStream%2A>來載入<xref:System.Windows.Controls.Page>資源檔並將其設置為<xref:System.Windows.Controls.Frame>（`pageFrame`的內容）：  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 調用<xref:System.Windows.Application.GetResourceStream%2A>時，您需要<xref:System.IO.Stream>執行將之轉換為要使用它設置的屬性類型的其他工作。 相反，您可以通過使用代碼將資源檔直接載入到類型的屬性中來<xref:System.IO.Stream>處理打開和轉換 的 WPF。  
  
 下面的示例演示如何使用代碼直接載入<xref:System.Windows.Controls.Page>到<xref:System.Windows.Controls.Frame>（`pageFrame`） 中。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 下列範例相當於前一個範例的標記對等用法。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>應用程式程式碼檔案作為資源檔  
 可以使用包 URI 引用一組特殊的 WPF 應用程式代碼檔，包括視窗、頁面、流文檔和資源字典。 例如，可以使用引用應用程式啟動時<xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>要載入的視窗或頁面的包 URI 設置屬性。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 當 XAML 檔作為專案包含在 MSBuild 專案中時，`Page`可以執行此操作。  
  
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
> 在 Visual Studio 中，<xref:System.Windows.Window>向<xref:System.Windows.Navigation.NavigationWindow>專案<xref:System.Windows.Controls.Page>添加新<xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.ResourceDictionary> 、、、、`Build Action`標記檔將預設為`Page`。  
  
 編譯具有`Page`項的專案時，這些專案[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]將轉換為二進位格式並編譯到關聯的程式集中。 因此，這些檔案可以比照一般資源檔的方式來使用。  
  
> [!NOTE]
> 如果[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔配置為項`Resource`，並且沒有代碼背後的檔，則原始[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔將編譯為程式集，而不是原始[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的二進位版本。  
  
<a name="Content_Files"></a>
## <a name="content-files"></a>內容檔  
 *內容檔*與可執行程式集一起作為鬆散檔分發。 雖然這種檔案並未編譯成組件，但是編譯組件時使用的中繼資料會建立與每個內容檔的關聯。  
  
 如果應用程式需要一組特定的應用程式資料檔案，而您不想在更新這些檔案時重新編譯使用它們的組件，您應該使用內容檔。  
  
### <a name="configuring-content-files"></a>設定內容檔  
 要將內容檔添加到專案，必須將應用程式資料檔案作為項包含在內`Content`。 此外，由於內容檔未直接編譯到程式集中，因此您需要設置 MSBuild`CopyToOutputDirectory`中繼資料元素以指定將內容檔案複製到相對於生成的程式集的位置。 如果希望在每次生成專案時將資源複製到生成輸出檔案夾，則可以使用`CopyToOutputDirectory``Always`該值設置中繼資料元素。 否則，您可以確保僅使用`PreserveNewest`該值將資源的最新版本複製到生成輸出檔案夾。  
  
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
> 在 Visual Studio 中`Build Action`，通過將檔添加到專案並將其設置為`Content`（`Copy to Output Directory``Copy always`與`Always`） 和`Copy if newer`（與`PreserveNewest`相同） 創建內容檔來創建內容檔。  
  
 生成專案時，將屬性<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>編譯為每個內容檔的組件中繼資料。  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 的值<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>意味著內容檔的路徑相對於其在專案中的位置。 例如，如果內容檔位於專案子資料夾中，則其他路徑資訊將合併到該值中<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>。  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 該<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>值也是生成輸出檔案夾中內容檔的路徑的值。  
  
### <a name="using-content-files"></a>使用內容檔  
 要載入內容檔，可以調用<xref:System.Windows.Application.GetContentStream%2A><xref:System.Windows.Application>類的方法，傳遞標識所需內容檔的包 URI。 <xref:System.Windows.Application.GetContentStream%2A>返回一<xref:System.Windows.Resources.StreamResourceInfo>個物件，該物件將內容檔公開為<xref:System.IO.Stream>，並描述其內容類型。  
  
 例如，以下代碼演示如何使用<xref:System.Windows.Application.GetContentStream%2A>來載入<xref:System.Windows.Controls.Page>內容檔並將其設置為<xref:System.Windows.Controls.Frame>的內容 。`pageFrame`  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 調用<xref:System.Windows.Application.GetContentStream%2A>時，您需要<xref:System.IO.Stream>執行將之轉換為要使用它設置的屬性類型的其他工作。 相反，您可以通過使用代碼將資源檔直接載入到類型的屬性中來<xref:System.IO.Stream>處理打開和轉換 的 WPF。  
  
 下面的示例演示如何使用代碼直接載入<xref:System.Windows.Controls.Page>到<xref:System.Windows.Controls.Frame>（`pageFrame`） 中。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 下列範例相當於前一個範例的標記對等用法。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a>來源網站檔  
 資源檔與它們與它們一起分發的程式集具有顯式關係，由 定義<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>。 但是在某些情況下，您可能想在組件和應用程式資料檔案之間建立隱含或不存在的關聯性，這些情況包括：  
  
- 檔在編譯時不存在。  
  
- 在執行階段之前，您不知道組件需要哪些檔案。  
  
- 您不想在更新檔案時重新編譯其關聯的組件。  
  
- 應用程式使用大型的資料檔案，例如音訊和視訊，而您只想讓使用者自行選擇是否下載這些檔案。  
  
 可以使用傳統的 URI 方案（如file:///和HTTP://方案）載入這些類型的檔。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 不過，file:/// 和 http:// 配置要求應用程式必須受到完全信任。 如果應用程式是從 Internet 或 Intranet 啟動的 XAML 瀏覽器應用程式 （XBAP），並且它僅請求允許從這些位置啟動的應用程式的許可權集，則只能從應用程式的原點（啟動位置）。 此類檔稱為原始檔案*網站*。  
  
 來源網站檔是部分信任應用程式的唯一選擇，但並不是只適用於部分信任應用程式。 完全信任應用程式可能還是需要載入它們在建置階段並不知道的應用程式資料檔案；雖然完全信任應用程式可以使用 file:///，但是應用程式資料檔案可能會安裝在應用程式組件的相同資料夾或子資料夾中。 在此情況下，使用來源網站參考比使用 file:/// 簡單，因為使用 file:/// 時，您必須找出檔案的完整路徑。  
  
> [!NOTE]
> 源網站檔不會在用戶端電腦上使用 XAML 瀏覽器應用程式 （XBAP） 緩存，而內容檔是。 因此，只有在特別要求時，才會下載來源網站檔。 如果 XAML 瀏覽器應用程式 （XBAP） 應用程式具有大型媒體檔案，將它們配置為原始檔案網站意味著初始應用程式啟動速度更快，並且檔僅按需下載。  
  
### <a name="configuring-site-of-origin-files"></a>設定來源網站檔  
 如果源網站檔在編譯時不存在或未知，則需要使用傳統的部署機制來確保所需的檔在運行時可用，包括使用`XCopy`命令列程式或 Microsoft Windows 安裝程式。  
  
 如果在編譯時確實知道要位於原點的檔，但仍希望避免顯式依賴項，則可以將這些檔作為`None`項添加到 MSBuild 專案中。 與內容檔一樣，您需要設置 MSBuild`CopyToOutputDirectory`屬性，通過指定`Always`值或`PreserveNewest`值來指定原點檔案複製到相對於生成的程式集的位置。  
  
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
> 在 Visual Studio 中，您可以通過將檔添加到專案並將其設置為`Build Action``None`來創建源網站檔。  
  
 生成專案時，MSBuild 會將指定的檔案複製到生成輸出檔案夾。  
  
### <a name="using-site-of-origin-files"></a>使用來源網站檔  
 要載入源網站檔，可以調用<xref:System.Windows.Application.GetRemoteStream%2A><xref:System.Windows.Application>類的方法，傳遞一個包 URI 來標識所需的源網站檔。 <xref:System.Windows.Application.GetRemoteStream%2A>返回一<xref:System.Windows.Resources.StreamResourceInfo>個物件，該物件將原始檔案的網站公開為<xref:System.IO.Stream>， 並描述其內容類型。  
  
 例如，<xref:System.Windows.Application.GetRemoteStream%2A>以下代碼演示如何使用 來載入源<xref:System.Windows.Controls.Page>網站檔並將其設置為<xref:System.Windows.Controls.Frame>（`pageFrame`的內容）。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 調用<xref:System.Windows.Application.GetRemoteStream%2A>時，您需要<xref:System.IO.Stream>執行將之轉換為要使用它設置的屬性類型的其他工作。 相反，您可以通過使用代碼將資源檔直接載入到類型的屬性中來<xref:System.IO.Stream>處理打開和轉換 的 WPF。  
  
 下面的示例演示如何使用代碼直接載入<xref:System.Windows.Controls.Page>到<xref:System.Windows.Controls.Frame>（`pageFrame`） 中。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 下列範例相當於前一個範例的標記對等用法。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a>在變更組建類型之後重建  
 在變更應用程式資料檔案的組建類型之後，您必須重建整個應用程式，以確認套用這些變更。 若您只建置應用程式，則不會套用變更。  
  
## <a name="see-also"></a>另請參閱

- [WPF 中的 Pack URI](pack-uris-in-wpf.md)
