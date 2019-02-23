---
title: WPF 應用程式資源、內容和資料檔案
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
ms.openlocfilehash: 3fed7127624714e67121c388e70b8b833d88d772
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746532"
---
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="16de4-102">WPF 應用程式資源、內容和資料檔案</span><span class="sxs-lookup"><span data-stu-id="16de4-102">WPF Application Resource, Content, and Data Files</span></span>
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] <span data-ttu-id="16de4-103">應用程式經常依賴檔案包含非可執行檔的資料，例如[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、 影像、 視訊和音訊。</span><span class="sxs-lookup"><span data-stu-id="16de4-103">applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> <span data-ttu-id="16de4-104">Windows Presentation Foundation (WPF) 提供設定、 用來識別，以及使用這些類型的資料檔案，稱為應用程式資料檔案的特殊支援。</span><span class="sxs-lookup"><span data-stu-id="16de4-104">Windows Presentation Foundation (WPF) offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="16de4-105">這項支援是以一組特定的應用程式資料檔案類型為中心，包括：</span><span class="sxs-lookup"><span data-stu-id="16de4-105">This support revolves around a specific set of application data file types, including:</span></span>  
  
-   <span data-ttu-id="16de4-106">**資源檔**:資料檔案編譯成可執行檔或程式庫的[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]組件。</span><span class="sxs-lookup"><span data-stu-id="16de4-106">**Resource Files**: Data files that are compiled into either an executable or library [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.</span></span>  
  
-   <span data-ttu-id="16de4-107">**內容檔**:具有明確關聯與可執行檔的獨立資料檔案[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]組件。</span><span class="sxs-lookup"><span data-stu-id="16de4-107">**Content Files**: Standalone data files that have an explicit association with an executable [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.</span></span>  
  
-   <span data-ttu-id="16de4-108">**來源網站檔**:與可執行檔沒有任何關聯的獨立資料檔案[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]組件。</span><span class="sxs-lookup"><span data-stu-id="16de4-108">**Site of Origin Files**: Standalone data files that have no association with an executable [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.</span></span>  
  
 <span data-ttu-id="16de4-109">這三種檔案類型之間的其中一個重要區別是資源檔和內容檔是建置階段的已知檔案；組件並明確知道這兩種檔案。</span><span class="sxs-lookup"><span data-stu-id="16de4-109">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="16de4-110">來源網站檔，不過，組件可能完全不了解它們，或透過組件的隱含知識[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]參考，後者的情況則無法保證參考的來源網站檔確實存在。</span><span class="sxs-lookup"><span data-stu-id="16de4-110">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="16de4-111">若要參考應用程式資料檔案，Windows Presentation Foundation (WPF) 使用 Pack[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]配置，這會在將詳細說明[WPF 中的 Pack Uri](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md))。</span><span class="sxs-lookup"><span data-stu-id="16de4-111">To reference application data files, Windows Presentation Foundation (WPF) uses the Pack [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] Scheme, which is described in detail in [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="16de4-112">本主題描述何設定及使用應用程式資料檔案。</span><span class="sxs-lookup"><span data-stu-id="16de4-112">This topic describes how to configure and use application data files.</span></span>  
  
  
<a name="Resource_Files"></a>   
## <a name="resource-files"></a><span data-ttu-id="16de4-113">資源檔</span><span class="sxs-lookup"><span data-stu-id="16de4-113">Resource Files</span></span>  
 <span data-ttu-id="16de4-114">若應用程式資料檔案必須一律可供應用程式使用，確保可用性的唯一方法是將檔案編譯成應用程式的主要可執行檔組件或是應用程式的其中一個參考組件。</span><span class="sxs-lookup"><span data-stu-id="16de4-114">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="16de4-115">這種類型的應用程式資料檔案稱為*資源檔*。</span><span class="sxs-lookup"><span data-stu-id="16de4-115">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="16de4-116">應該使用資源檔的時機包括：</span><span class="sxs-lookup"><span data-stu-id="16de4-116">You should use resource files when:</span></span>  
  
-   <span data-ttu-id="16de4-117">您不需要在資源檔編譯成組件之後更新該檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="16de4-117">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
-   <span data-ttu-id="16de4-118">您想要透過減少檔案相依性數目的方式，簡化複雜的應用程式發佈程序。</span><span class="sxs-lookup"><span data-stu-id="16de4-118">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
-   <span data-ttu-id="16de4-119">您的應用程式資料檔案必須可以當地語系化 (請參閱[WPF 全球化和當地語系化概觀](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md))。</span><span class="sxs-lookup"><span data-stu-id="16de4-119">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16de4-120">在本節中所述的資源檔案為不同的資源檔中所述[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)也不同於中所述的內嵌或連結資源[管理應用程式資源 (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="16de4-120">The resource files described in this section are different than the resource files described in [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) and different than the embedded or linked resources described in [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="16de4-121">設定資源檔</span><span class="sxs-lookup"><span data-stu-id="16de4-121">Configuring Resource Files</span></span>  
 <span data-ttu-id="16de4-122">在  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，資源檔是包含在檔案[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]專案做為`Resource`項目。</span><span class="sxs-lookup"><span data-stu-id="16de4-122">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], a resource file is a file that is included in an [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] project as a `Resource` item.</span></span>  
  
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
>  <span data-ttu-id="16de4-123">在  [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，您建立的資源檔，將檔案新增至專案，並設定其`Build Action`至`Resource`。</span><span class="sxs-lookup"><span data-stu-id="16de4-123">In [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="16de4-124">建置專案時，[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]會將資源編譯成組件。</span><span class="sxs-lookup"><span data-stu-id="16de4-124">When the project is built, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="16de4-125">使用資源檔</span><span class="sxs-lookup"><span data-stu-id="16de4-125">Using Resource Files</span></span>  
 <span data-ttu-id="16de4-126">若要載入的資源檔，您可以呼叫<xref:System.Windows.Application.GetResourceStream%2A>方法<xref:System.Windows.Application>類別，將組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]來識別所需的資源檔。</span><span class="sxs-lookup"><span data-stu-id="16de4-126">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that identifies the desired resource file.</span></span> <span data-ttu-id="16de4-127"><xref:System.Windows.Application.GetResourceStream%2A> 會傳回<xref:System.Windows.Resources.StreamResourceInfo>物件，它會公開為資源檔<xref:System.IO.Stream>並說明其內容的類型。</span><span class="sxs-lookup"><span data-stu-id="16de4-127"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="16de4-128">例如，下列程式碼示範如何使用<xref:System.Windows.Application.GetResourceStream%2A>載入<xref:System.Windows.Controls.Page>資源檔案，並將它設定為內容<xref:System.Windows.Controls.Frame>(`pageFrame`):</span><span class="sxs-lookup"><span data-stu-id="16de4-128">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="16de4-129">同時呼叫<xref:System.Windows.Application.GetResourceStream%2A>可讓您存取<xref:System.IO.Stream>，您需要執行其他工作，將它轉換成屬性會設定所使用的型別。</span><span class="sxs-lookup"><span data-stu-id="16de4-129">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="16de4-130">相反地，您可以讓[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]負責處理開啟及轉換<xref:System.IO.Stream>藉由直接將資源檔載入類型，使用程式碼的屬性。</span><span class="sxs-lookup"><span data-stu-id="16de4-130">Instead, you can let [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="16de4-131">下列範例示範如何載入<xref:System.Windows.Controls.Page>直接<xref:System.Windows.Controls.Frame>(`pageFrame`) 使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="16de4-131">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="16de4-132">下列範例相當於前一個範例的標記對等用法。</span><span class="sxs-lookup"><span data-stu-id="16de4-132">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="16de4-133">應用程式程式碼檔案作為資源檔</span><span class="sxs-lookup"><span data-stu-id="16de4-133">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="16de4-134">一組特殊[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用程式程式碼檔案可以使用組件參考[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，包括 windows、 頁面、 非固定格式文件，以及資源字典。</span><span class="sxs-lookup"><span data-stu-id="16de4-134">A special set of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application code files can be referenced using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="16de4-135">例如，您可以設定<xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>屬性的 pack[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考視窗或您想要應用程式啟動時載入的頁面。</span><span class="sxs-lookup"><span data-stu-id="16de4-135">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="16de4-136">您可以執行時[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案包含在[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]專案做為`Page`項目。</span><span class="sxs-lookup"><span data-stu-id="16de4-136">You can do this when a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is included in an [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] project as a `Page` item.</span></span>  
  
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
>  <span data-ttu-id="16de4-137">在  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]，您加入新<xref:System.Windows.Window>， <xref:System.Windows.Navigation.NavigationWindow>， <xref:System.Windows.Controls.Page>， <xref:System.Windows.Documents.FlowDocument>，或<xref:System.Windows.ResourceDictionary>至專案時，`Build Action`標記檔案將會預設為`Page`。</span><span class="sxs-lookup"><span data-stu-id="16de4-137">In [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="16de4-138">使用專案時`Page`編譯項目時，[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]項目會轉換為二進位格式，並編譯成相關聯的組件。</span><span class="sxs-lookup"><span data-stu-id="16de4-138">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="16de4-139">因此，這些檔案可以比照一般資源檔的方式來使用。</span><span class="sxs-lookup"><span data-stu-id="16de4-139">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16de4-140">如果[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案設定為`Resource`項目，而且沒有程式碼後置檔案，則原始[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]編譯成組件，而不是原始的二進位版本[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="16de4-140">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a><span data-ttu-id="16de4-141">內容檔</span><span class="sxs-lookup"><span data-stu-id="16de4-141">Content Files</span></span>  
 <span data-ttu-id="16de4-142">A*的內容檔案*以鬆散檔案與可執行組件一起散發。</span><span class="sxs-lookup"><span data-stu-id="16de4-142">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="16de4-143">雖然這種檔案並未編譯成組件，但是編譯組件時使用的中繼資料會建立與每個內容檔的關聯。</span><span class="sxs-lookup"><span data-stu-id="16de4-143">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="16de4-144">如果應用程式需要一組特定的應用程式資料檔案，而您不想在更新這些檔案時重新編譯使用它們的組件，您應該使用內容檔。</span><span class="sxs-lookup"><span data-stu-id="16de4-144">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="16de4-145">設定內容檔</span><span class="sxs-lookup"><span data-stu-id="16de4-145">Configuring Content Files</span></span>  
 <span data-ttu-id="16de4-146">若要將內容檔加入專案中，應用程式資料檔案必須是包含做為`Content`項目。</span><span class="sxs-lookup"><span data-stu-id="16de4-146">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="16de4-147">此外，因為內容檔不直接編譯成組件，您需要設定[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`CopyToOutputDirectory`中繼資料的項目，來指定內容的檔案會複製到建置組件的相對位置。</span><span class="sxs-lookup"><span data-stu-id="16de4-147">Furthermore, because a content file is not compiled directly into the assembly, you need to set the [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="16de4-148">如果您想要複製到組建輸出資料夾每次資源建置專案時，您設定`CopyToOutputDirectory`使用的中繼資料元素`Always`值。</span><span class="sxs-lookup"><span data-stu-id="16de4-148">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="16de4-149">否則，您可以確定只有最新版本的資源複製到組建輸出資料夾，使用`PreserveNewest`值。</span><span class="sxs-lookup"><span data-stu-id="16de4-149">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="16de4-150">以下顯示設定為內容檔的檔案；只有在將新版本的資源新增至專案時，這個內容檔才會複製到建置輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="16de4-150">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
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
>  <span data-ttu-id="16de4-151">在[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]，您建立的內容檔案，將檔案新增至專案，並設定其`Build Action`要`Content`，並設定其`Copy to Output Directory`來`Copy always`(相同`Always`) 和`Copy if newer`(相同`PreserveNewest`)。</span><span class="sxs-lookup"><span data-stu-id="16de4-151">In [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="16de4-152">建置專案時，<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>屬性會編譯成每個內容檔的組件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="16de4-152">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="16de4-153">值<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>表示相對於其位置在專案中的內容檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="16de4-153">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="16de4-154">例如，如果內容的檔案位於專案子資料夾，其他路徑資訊便會併入<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>值。</span><span class="sxs-lookup"><span data-stu-id="16de4-154">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="16de4-155"><xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>值也是建置輸出資料夾中的內容檔案的路徑的值。</span><span class="sxs-lookup"><span data-stu-id="16de4-155">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="16de4-156">使用內容檔</span><span class="sxs-lookup"><span data-stu-id="16de4-156">Using Content Files</span></span>  
 <span data-ttu-id="16de4-157">若要載入的內容檔案，您可以呼叫<xref:System.Windows.Application.GetContentStream%2A>方法<xref:System.Windows.Application>類別，將組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]可識別所需的內容檔案。</span><span class="sxs-lookup"><span data-stu-id="16de4-157">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that identifies the desired content file.</span></span> <span data-ttu-id="16de4-158"><xref:System.Windows.Application.GetContentStream%2A> 會傳回<xref:System.Windows.Resources.StreamResourceInfo>物件，它會為將內容檔公開<xref:System.IO.Stream>並說明其內容的類型。</span><span class="sxs-lookup"><span data-stu-id="16de4-158"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="16de4-159">例如，下列程式碼示範如何使用<xref:System.Windows.Application.GetContentStream%2A>載入<xref:System.Windows.Controls.Page>內容檔案，並將它設定為內容<xref:System.Windows.Controls.Frame>(`pageFrame`)。</span><span class="sxs-lookup"><span data-stu-id="16de4-159">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="16de4-160">同時呼叫<xref:System.Windows.Application.GetContentStream%2A>可讓您存取<xref:System.IO.Stream>，您需要執行其他工作，將它轉換成屬性會設定所使用的型別。</span><span class="sxs-lookup"><span data-stu-id="16de4-160">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="16de4-161">相反地，您可以讓[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]負責處理開啟及轉換<xref:System.IO.Stream>藉由直接將資源檔載入類型，使用程式碼的屬性。</span><span class="sxs-lookup"><span data-stu-id="16de4-161">Instead, you can let [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="16de4-162">下列範例示範如何載入<xref:System.Windows.Controls.Page>直接<xref:System.Windows.Controls.Frame>(`pageFrame`) 使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="16de4-162">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="16de4-163">下列範例相當於前一個範例的標記對等用法。</span><span class="sxs-lookup"><span data-stu-id="16de4-163">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a><span data-ttu-id="16de4-164">來源網站檔</span><span class="sxs-lookup"><span data-stu-id="16de4-164">Site of Origin Files</span></span>  
 <span data-ttu-id="16de4-165">資源檔具有其散發，以及組件的明確關聯性所定義<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>。</span><span class="sxs-lookup"><span data-stu-id="16de4-165">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="16de4-166">但是在某些情況下，您可能想在組件和應用程式資料檔案之間建立隱含或不存在的關聯性，這些情況包括：</span><span class="sxs-lookup"><span data-stu-id="16de4-166">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
-   <span data-ttu-id="16de4-167">檔案不存在在編譯時期。</span><span class="sxs-lookup"><span data-stu-id="16de4-167">A file doesn't exist at compile time.</span></span>  
  
-   <span data-ttu-id="16de4-168">在執行階段之前，您不知道組件需要哪些檔案。</span><span class="sxs-lookup"><span data-stu-id="16de4-168">You don't know what files your assembly will require until run time.</span></span>  
  
-   <span data-ttu-id="16de4-169">您不想在更新檔案時重新編譯其關聯的組件。</span><span class="sxs-lookup"><span data-stu-id="16de4-169">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
-   <span data-ttu-id="16de4-170">應用程式使用大型的資料檔案，例如音訊和視訊，而您只想讓使用者自行選擇是否下載這些檔案。</span><span class="sxs-lookup"><span data-stu-id="16de4-170">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="16de4-171">就能夠載入這些類型的檔案，使用傳統[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]配置，例如 file:/// 和 http:// 配置。</span><span class="sxs-lookup"><span data-stu-id="16de4-171">It is possible to load these types of files by using traditional [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] schemes, such as the file:/// and http:// schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="16de4-172">不過，file:/// 和 http:// 配置要求應用程式必須受到完全信任。</span><span class="sxs-lookup"><span data-stu-id="16de4-172">However, the file:/// and http:// schemes require your application to have full trust.</span></span> <span data-ttu-id="16de4-173">如果您的應用程式是[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]從網際網路或內部網路啟動，而且它會要求只允許從這些位置啟動的應用程式可以只從原點 （應用程式的網站載入鬆散式檔案的權限集啟動位置）。</span><span class="sxs-lookup"><span data-stu-id="16de4-173">If your application is a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="16de4-174">這類檔案稱為*來源網站的*檔案。</span><span class="sxs-lookup"><span data-stu-id="16de4-174">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="16de4-175">來源網站檔是部分信任應用程式的唯一選擇，但並不是只適用於部分信任應用程式。</span><span class="sxs-lookup"><span data-stu-id="16de4-175">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="16de4-176">完全信任應用程式可能還是需要載入它們在建置階段並不知道的應用程式資料檔案；雖然完全信任應用程式可以使用 file:///，但是應用程式資料檔案可能會安裝在應用程式組件的相同資料夾或子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="16de4-176">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="16de4-177">在此情況下，使用來源網站參考比使用 file:/// 簡單，因為使用 file:/// 時，您必須找出檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="16de4-177">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16de4-178">檔案不會快取使用的來源網站的[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]在用戶端電腦上，內容檔案時。</span><span class="sxs-lookup"><span data-stu-id="16de4-178">Site of origin files are not cached with an [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] on a client machine, while content files are.</span></span> <span data-ttu-id="16de4-179">因此，只有在特別要求時，才會下載來源網站檔。</span><span class="sxs-lookup"><span data-stu-id="16de4-179">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="16de4-180">如果[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]應用程式具有大型媒體檔案，設定它們，因為來源網站檔表示初始應用程式啟動速度會更快，並隨只下載檔案。</span><span class="sxs-lookup"><span data-stu-id="16de4-180">If an [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="16de4-181">設定來源網站檔</span><span class="sxs-lookup"><span data-stu-id="16de4-181">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="16de4-182">如果您的來源檔案的網站會在編譯時期為不存在或未知，您需要使用傳統的部署機制，確保所需的檔案可在執行階段，包括使用`XCopy`命令列程式或[!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].</span><span class="sxs-lookup"><span data-stu-id="16de4-182">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].</span></span>  
  
 <span data-ttu-id="16de4-183">如果您知道在編譯時期，您會想要找的來源站台，但仍想要避免產生明確相依性的檔案，您可以新增這些檔案[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]專案做為`None`項目。</span><span class="sxs-lookup"><span data-stu-id="16de4-183">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] project as `None` item.</span></span> <span data-ttu-id="16de4-184">如同內容檔案，您需要設定[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`CopyToOutputDirectory`屬性來指定來源網站檔會複製到相對於已建置的組件，是由指定的位置`Always`值或`PreserveNewest`值。</span><span class="sxs-lookup"><span data-stu-id="16de4-184">As with content files, you need to set the [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
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
>  <span data-ttu-id="16de4-185">在  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]，您建立來源網站檔將檔案新增至專案，並設定其`Build Action`至`None`。</span><span class="sxs-lookup"><span data-stu-id="16de4-185">In [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="16de4-186">建置專案時，[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]將指定的檔案複製到組建輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="16de4-186">When the project is built, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="16de4-187">使用來源網站檔</span><span class="sxs-lookup"><span data-stu-id="16de4-187">Using Site of Origin Files</span></span>  
 <span data-ttu-id="16de4-188">若要載入來源網站檔，您可以呼叫<xref:System.Windows.Application.GetRemoteStream%2A>方法<xref:System.Windows.Application>類別，將組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]可識別所需的站台的來源檔案。</span><span class="sxs-lookup"><span data-stu-id="16de4-188">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that identifies the desired site of origin file.</span></span> <span data-ttu-id="16de4-189"><xref:System.Windows.Application.GetRemoteStream%2A> 會傳回<xref:System.Windows.Resources.StreamResourceInfo>物件，它會公開做為來源檔案的站台<xref:System.IO.Stream>並說明其內容的類型。</span><span class="sxs-lookup"><span data-stu-id="16de4-189"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="16de4-190">例如，下列程式碼示範如何使用<xref:System.Windows.Application.GetRemoteStream%2A>載入<xref:System.Windows.Controls.Page>來源網站上的檔案，並將它設定為內容<xref:System.Windows.Controls.Frame>(`pageFrame`)。</span><span class="sxs-lookup"><span data-stu-id="16de4-190">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="16de4-191">同時呼叫<xref:System.Windows.Application.GetRemoteStream%2A>可讓您存取<xref:System.IO.Stream>，您需要執行其他工作，將它轉換成屬性會設定所使用的型別。</span><span class="sxs-lookup"><span data-stu-id="16de4-191">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="16de4-192">相反地，您可以讓[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]負責處理開啟及轉換<xref:System.IO.Stream>藉由直接將資源檔載入類型，使用程式碼的屬性。</span><span class="sxs-lookup"><span data-stu-id="16de4-192">Instead, you can let [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="16de4-193">下列範例示範如何載入<xref:System.Windows.Controls.Page>直接<xref:System.Windows.Controls.Frame>(`pageFrame`) 使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="16de4-193">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="16de4-194">下列範例相當於前一個範例的標記對等用法。</span><span class="sxs-lookup"><span data-stu-id="16de4-194">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="16de4-195">在變更組建類型之後重建</span><span class="sxs-lookup"><span data-stu-id="16de4-195">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="16de4-196">在變更應用程式資料檔案的組建類型之後，您必須重建整個應用程式，以確認套用這些變更。</span><span class="sxs-lookup"><span data-stu-id="16de4-196">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="16de4-197">若您只建置應用程式，則不會套用變更。</span><span class="sxs-lookup"><span data-stu-id="16de4-197">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16de4-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16de4-198">See also</span></span>
- [<span data-ttu-id="16de4-199">WPF 中的 Pack URI</span><span class="sxs-lookup"><span data-stu-id="16de4-199">Pack URIs in WPF</span></span>](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
