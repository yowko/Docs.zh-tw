---
title: 應用程式資源、內容和資料檔案
description: 瞭解在 Windows Presentation Foundation （WPF）中設定、識別和使用應用程式資料檔案的特殊支援。
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
ms.openlocfilehash: 324b3eb922f0fd1d1d9ad00105a06a7fbdb8effd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622857"
---
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="2ffd5-103">WPF 應用程式資源、內容和資料檔案</span><span class="sxs-lookup"><span data-stu-id="2ffd5-103">WPF Application Resource, Content, and Data Files</span></span>
<span data-ttu-id="2ffd5-104">Microsoft Windows 應用程式通常取決於包含非可執行資料的檔案，例如 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 影像、影片和音訊。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-104">Microsoft Windows applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> <span data-ttu-id="2ffd5-105">Windows Presentation Foundation （WPF）提供設定、識別和使用這些類型的資料檔案（稱為「應用程式資料檔案」）的特殊支援。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-105">Windows Presentation Foundation (WPF) offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="2ffd5-106">這項支援是以一組特定的應用程式資料檔案類型為中心，包括：</span><span class="sxs-lookup"><span data-stu-id="2ffd5-106">This support revolves around a specific set of application data file types, including:</span></span>  
  
- <span data-ttu-id="2ffd5-107">**資源檔**：編譯成可執行檔或程式庫 WPF 元件的資料檔案。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-107">**Resource Files**: Data files that are compiled into either an executable or library WPF assembly.</span></span>  
  
- <span data-ttu-id="2ffd5-108">**內容**檔案：與可執行檔 WPF 元件具有明確關聯的獨立資料檔案。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-108">**Content Files**: Standalone data files that have an explicit association with an executable WPF assembly.</span></span>  
  
- <span data-ttu-id="2ffd5-109">**來源網站**檔案：與可執行檔 WPF 元件沒有關聯的獨立資料檔案。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-109">**Site of Origin Files**: Standalone data files that have no association with an executable WPF assembly.</span></span>  
  
 <span data-ttu-id="2ffd5-110">這三種檔案類型之間的其中一個重要區別是資源檔和內容檔是建置階段的已知檔案；組件並明確知道這兩種檔案。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-110">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="2ffd5-111">不過，對於原始網站檔案而言，元件可能完全不知道它們，或透過 pack 統一資源識別元（URI）參考進行隱含知識;如果是後者，則不保證來源參考的網站確實存在。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-111">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack uniform resource identifier (URI) reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="2ffd5-112">若要參考應用程式資料檔案，Windows Presentation Foundation （WPF）使用 Pack 統一資源識別元（URI）配置，在[WPF 的套件 uri](pack-uris-in-wpf.md)中有詳細說明）。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-112">To reference application data files, Windows Presentation Foundation (WPF) uses the Pack uniform resource identifier (URI) Scheme, which is described in detail in [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="2ffd5-113">本主題描述何設定及使用應用程式資料檔案。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-113">This topic describes how to configure and use application data files.</span></span>  

<a name="Resource_Files"></a>
## <a name="resource-files"></a><span data-ttu-id="2ffd5-114">資源檔</span><span class="sxs-lookup"><span data-stu-id="2ffd5-114">Resource Files</span></span>  
 <span data-ttu-id="2ffd5-115">若應用程式資料檔案必須一律可供應用程式使用，確保可用性的唯一方法是將檔案編譯成應用程式的主要可執行檔組件或是應用程式的其中一個參考組件。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-115">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="2ffd5-116">這種類型的應用程式資料檔案稱為「*資源檔*」。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-116">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="2ffd5-117">應該使用資源檔的時機包括：</span><span class="sxs-lookup"><span data-stu-id="2ffd5-117">You should use resource files when:</span></span>  
  
- <span data-ttu-id="2ffd5-118">您不需要在資源檔編譯成組件之後更新該檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-118">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
- <span data-ttu-id="2ffd5-119">您想要透過減少檔案相依性數目的方式，簡化複雜的應用程式發佈程序。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-119">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
- <span data-ttu-id="2ffd5-120">您的應用程式資料檔案必須是可當地語系化的（請參閱[WPF 全球化和當地語系化總覽](../advanced/wpf-globalization-and-localization-overview.md)）。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-120">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ffd5-121">本節所述的資源檔與[XAML 資源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)中所述的資源檔不同，而且不同于[管理應用程式資源（.net）](/visualstudio/ide/managing-application-resources-dotnet)中所述的內嵌或連結的資源。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-121">The resource files described in this section are different than the resource files described in [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) and different than the embedded or linked resources described in [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="2ffd5-122">設定資源檔</span><span class="sxs-lookup"><span data-stu-id="2ffd5-122">Configuring Resource Files</span></span>  
 <span data-ttu-id="2ffd5-123">在 WPF 中，資源檔是包含在 Microsoft build engine （MSBuild）專案中做為專案的檔案 `Resource` 。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-123">In WPF, a resource file is a file that is included in an Microsoft build engine (MSBuild) project as a `Resource` item.</span></span>  
  
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
> <span data-ttu-id="2ffd5-124">在 Visual Studio 中，您可以藉由將檔案新增至專案，並將其設定為，來建立資源檔 `Build Action` `Resource` 。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-124">In Visual Studio, you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="2ffd5-125">建立專案時，MSBuild 會將資源編譯成元件。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-125">When the project is built, MSBuild compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="2ffd5-126">使用資源檔</span><span class="sxs-lookup"><span data-stu-id="2ffd5-126">Using Resource Files</span></span>  
 <span data-ttu-id="2ffd5-127">若要載入資源檔，您可以呼叫 <xref:System.Windows.Application.GetResourceStream%2A> 類別的方法 <xref:System.Windows.Application> ，並傳遞識別所需資源檔的 pack URI。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-127">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired resource file.</span></span> <span data-ttu-id="2ffd5-128"><xref:System.Windows.Application.GetResourceStream%2A>傳回 <xref:System.Windows.Resources.StreamResourceInfo> 物件，它會將資源檔公開為 <xref:System.IO.Stream> ，並描述其內容類型。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-128"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="2ffd5-129">例如，下列程式碼會示範如何使用 <xref:System.Windows.Application.GetResourceStream%2A> 載入 <xref:System.Windows.Controls.Page> 資源檔，並將它設定為 <xref:System.Windows.Controls.Frame> （）的內容 `pageFrame` ：</span><span class="sxs-lookup"><span data-stu-id="2ffd5-129">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="2ffd5-130">當呼叫可 <xref:System.Windows.Application.GetResourceStream%2A> 讓您存取時 <xref:System.IO.Stream> ，您必須執行其他工作，將它轉換成您將設定它的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-130">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="2ffd5-131">相反地，您可以讓 WPF <xref:System.IO.Stream> 使用程式碼，將資源檔直接載入至型別的屬性，以處理開啟和轉換。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-131">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="2ffd5-132">下列範例顯示如何使用程式碼，將 <xref:System.Windows.Controls.Page> 直接載入 <xref:System.Windows.Controls.Frame> （ `pageFrame` ）。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-132">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="2ffd5-133">下列範例相當於前一個範例的標記對等用法。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-133">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="2ffd5-134">應用程式程式碼檔案作為資源檔</span><span class="sxs-lookup"><span data-stu-id="2ffd5-134">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="2ffd5-135">您可以使用套件 Uri 來參考一組特殊的 WPF 應用程式程式碼檔案，包括視窗、頁面、非固定格式檔和資源字典。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-135">A special set of WPF application code files can be referenced using pack URIs, including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="2ffd5-136">例如，您可以 <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> 使用一個 PACK URI 來設定屬性，該元件會參考您想要在應用程式啟動時載入的視窗或頁面。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-136">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack URI that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="2ffd5-137">當 MSBuild 專案中包含 XAML 檔案做為專案時，您可以執行此動作 `Page` 。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-137">You can do this when a XAML file is included in an MSBuild project as a `Page` item.</span></span>  
  
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
> <span data-ttu-id="2ffd5-138">在 Visual Studio 中，您會在專案中加入新的 <xref:System.Windows.Window> 、、 <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Page> 、 <xref:System.Windows.Documents.FlowDocument> 或 <xref:System.Windows.ResourceDictionary> ，而標記檔案的 `Build Action` 預設值為 `Page` 。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-138">In Visual Studio, you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="2ffd5-139">編譯具有專案的專案時 `Page` ，會將 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 專案轉換成二進位格式，並編譯成相關聯的元件。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-139">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="2ffd5-140">因此，這些檔案可以比照一般資源檔的方式來使用。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-140">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ffd5-141">如果檔案 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 設定為 `Resource` 專案，而且沒有程式碼後置檔案，則會將原始 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 編譯成元件，而不是原始的二進位版本 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-141">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>
## <a name="content-files"></a><span data-ttu-id="2ffd5-142">內容檔</span><span class="sxs-lookup"><span data-stu-id="2ffd5-142">Content Files</span></span>  
 <span data-ttu-id="2ffd5-143">*內容*檔案會與可執行檔元件一起散發為鬆散檔案。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-143">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="2ffd5-144">雖然這種檔案並未編譯成組件，但是編譯組件時使用的中繼資料會建立與每個內容檔的關聯。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-144">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="2ffd5-145">如果應用程式需要一組特定的應用程式資料檔案，而您不想在更新這些檔案時重新編譯使用它們的組件，您應該使用內容檔。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-145">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="2ffd5-146">設定內容檔</span><span class="sxs-lookup"><span data-stu-id="2ffd5-146">Configuring Content Files</span></span>  
 <span data-ttu-id="2ffd5-147">若要將內容檔案加入至專案，必須將應用程式資料檔案包含為 `Content` 專案。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-147">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="2ffd5-148">此外，由於內容檔案不會直接編譯到元件中，因此您必須設定 MSBuild `CopyToOutputDirectory` 中繼資料專案，以指定將內容檔案複製到與建立元件相對的位置。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-148">Furthermore, because a content file is not compiled directly into the assembly, you need to set the MSBuild `CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="2ffd5-149">如果您想要在每次建立專案時，將資源複製到組建輸出檔案夾，您可以 `CopyToOutputDirectory` 使用值來設定中繼資料 `Always` 元素。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-149">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="2ffd5-150">否則，您可以使用值，確保只有最新版本的資源會複製到組建輸出檔案夾 `PreserveNewest` 。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-150">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="2ffd5-151">以下顯示設定為內容檔的檔案；只有在將新版本的資源新增至專案時，這個內容檔才會複製到建置輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-151">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
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
> <span data-ttu-id="2ffd5-152">在 Visual Studio 中，您可以藉由將檔案新增至專案並將其設定為，來建立內容檔案 `Build Action` `Content` ，並將其設定 `Copy to Output Directory` 為 `Copy always` （與相同 `Always` ）和 `Copy if newer` （與相同 `PreserveNewest` ）。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-152">In Visual Studio, you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="2ffd5-153">建立專案時， <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 會將屬性編譯成每個內容檔案之元件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-153">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="2ffd5-154">的值 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 表示內容檔相對於專案中位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-154">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="2ffd5-155">例如，如果內容檔案位於專案子資料夾中，則會將其他路徑資訊併入 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 值中。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-155">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="2ffd5-156">此 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 值也是 [組建輸出] 資料夾中內容檔案的路徑值。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-156">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="2ffd5-157">使用內容檔</span><span class="sxs-lookup"><span data-stu-id="2ffd5-157">Using Content Files</span></span>  
 <span data-ttu-id="2ffd5-158">若要載入內容檔案，您可以呼叫 <xref:System.Windows.Application.GetContentStream%2A> 類別的方法 <xref:System.Windows.Application> ，並傳遞可識別所需內容檔案的 pack URI。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-158">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired content file.</span></span> <span data-ttu-id="2ffd5-159"><xref:System.Windows.Application.GetContentStream%2A>傳回 <xref:System.Windows.Resources.StreamResourceInfo> 物件，它會將內容檔公開為 <xref:System.IO.Stream> ，並描述其內容類型。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-159"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="2ffd5-160">例如，下列程式碼會示範如何使用 <xref:System.Windows.Application.GetContentStream%2A> 載入 <xref:System.Windows.Controls.Page> 內容檔案，並將它設定為 <xref:System.Windows.Controls.Frame> （）的內容 `pageFrame` 。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-160">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="2ffd5-161">當呼叫可 <xref:System.Windows.Application.GetContentStream%2A> 讓您存取時 <xref:System.IO.Stream> ，您必須執行其他工作，將它轉換成您將設定它的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-161">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="2ffd5-162">相反地，您可以讓 WPF <xref:System.IO.Stream> 使用程式碼，將資源檔直接載入至型別的屬性，以處理開啟和轉換。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-162">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="2ffd5-163">下列範例顯示如何使用程式碼，將 <xref:System.Windows.Controls.Page> 直接載入 <xref:System.Windows.Controls.Frame> （ `pageFrame` ）。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-163">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="2ffd5-164">下列範例相當於前一個範例的標記對等用法。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-164">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a><span data-ttu-id="2ffd5-165">來源網站檔</span><span class="sxs-lookup"><span data-stu-id="2ffd5-165">Site of Origin Files</span></span>  
 <span data-ttu-id="2ffd5-166">資源檔與一起散發的元件具有明確的關聯性，如所定義 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-166">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="2ffd5-167">但是在某些情況下，您可能想在組件和應用程式資料檔案之間建立隱含或不存在的關聯性，這些情況包括：</span><span class="sxs-lookup"><span data-stu-id="2ffd5-167">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
- <span data-ttu-id="2ffd5-168">在編譯時期，檔案不存在。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-168">A file doesn't exist at compile time.</span></span>  
  
- <span data-ttu-id="2ffd5-169">在執行階段之前，您不知道組件需要哪些檔案。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-169">You don't know what files your assembly will require until run time.</span></span>  
  
- <span data-ttu-id="2ffd5-170">您不想在更新檔案時重新編譯其關聯的組件。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-170">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
- <span data-ttu-id="2ffd5-171">應用程式使用大型的資料檔案，例如音訊和視訊，而您只想讓使用者自行選擇是否下載這些檔案。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-171">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="2ffd5-172">您可以使用傳統的 URI 配置（例如和架構）來載入這些類型的檔案 `file:///` `http://` 。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-172">It is possible to load these types of files by using traditional URI schemes, such as the `file:///` and `http://` schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="2ffd5-173">不過， `file:///` 和配置 `http://` 需要您的應用程式具有完全信任。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-173">However, the `file:///` and `http://` schemes require your application to have full trust.</span></span> <span data-ttu-id="2ffd5-174">如果您的應用程式是從網際網路或內部網路啟動的 XAML 瀏覽器應用程式（XBAP），而且它只會要求從那些位置啟動之應用程式所允許的許可權集，就只能從應用程式的來源網站（啟動位置）載入鬆散檔案。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-174">If your application is a XAML browser application (XBAP) that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="2ffd5-175">這類檔案稱為「*來源網站*」檔案。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-175">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="2ffd5-176">來源網站檔是部分信任應用程式的唯一選擇，但並不是只適用於部分信任應用程式。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-176">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="2ffd5-177">完全信任應用程式可能還是需要載入它們在建置階段並不知道的應用程式資料檔案；雖然完全信任應用程式可以使用 file:///，但是應用程式資料檔案可能會安裝在應用程式組件的相同資料夾或子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-177">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="2ffd5-178">在此情況下，使用來源網站參考比使用 file:/// 簡單，因為使用 file:/// 時，您必須找出檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-178">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ffd5-179">來源網站檔案不會使用用戶端電腦上的 XAML 瀏覽器應用程式（XBAP）進行快取，而內容檔案則是。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-179">Site of origin files are not cached with an XAML browser application (XBAP) on a client machine, while content files are.</span></span> <span data-ttu-id="2ffd5-180">因此，只有在特別要求時，才會下載來源網站檔。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-180">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="2ffd5-181">如果 XAML 瀏覽器應用程式（XBAP）應用程式有大型媒體檔案，將它們設定為「原始網站」檔案，表示初始應用程式啟動速度會更快，而且只會視需要下載檔案。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-181">If an XAML browser application (XBAP) application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="2ffd5-182">設定來源網站檔</span><span class="sxs-lookup"><span data-stu-id="2ffd5-182">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="2ffd5-183">如果您的原始網站檔案在編譯時期不存在或不明，您必須使用傳統部署機制，以確保在執行時間可使用所需的檔案，包括使用 `XCopy` 命令列程式或 Microsoft Windows Installer。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-183">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the Microsoft Windows Installer.</span></span>  
  
 <span data-ttu-id="2ffd5-184">如果您在編譯時期知道您想要在來源網站上找到的檔案，但仍想要避免明確的相依性，您可以將這些檔案新增至 MSBuild 專案做為 `None` 專案。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-184">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an MSBuild project as `None` item.</span></span> <span data-ttu-id="2ffd5-185">如同內容檔案，您必須設定 MSBuild `CopyToOutputDirectory` 屬性，以指定將來源網站檔案複製到相對於所建立元件的位置，方法是指定 `Always` 值或 `PreserveNewest` 值。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-185">As with content files, you need to set the MSBuild `CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
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
> <span data-ttu-id="2ffd5-186">在 Visual Studio 中，您可以藉由將檔案新增至專案，並將其設定為，來建立來源網站檔案 `Build Action` `None` 。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-186">In Visual Studio, you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="2ffd5-187">建立專案時，MSBuild 會將指定的檔案複製到組建輸出檔案夾。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-187">When the project is built, MSBuild copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="2ffd5-188">使用來源網站檔</span><span class="sxs-lookup"><span data-stu-id="2ffd5-188">Using Site of Origin Files</span></span>  
 <span data-ttu-id="2ffd5-189">若要載入原始網站檔案，您可以呼叫類別的 <xref:System.Windows.Application.GetRemoteStream%2A> 方法 <xref:System.Windows.Application> ，並傳遞識別所需來源網站檔案的 pack URI。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-189">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired site of origin file.</span></span> <span data-ttu-id="2ffd5-190"><xref:System.Windows.Application.GetRemoteStream%2A>傳回 <xref:System.Windows.Resources.StreamResourceInfo> 物件，它會將來源網站檔案公開為 <xref:System.IO.Stream> ，並描述其內容類型。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-190"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="2ffd5-191">例如，下列程式碼會示範如何使用 <xref:System.Windows.Application.GetRemoteStream%2A> 載入 <xref:System.Windows.Controls.Page> 原始網站檔案，並將它設定為 <xref:System.Windows.Controls.Frame> （）的內容 `pageFrame` 。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-191">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="2ffd5-192">當呼叫可 <xref:System.Windows.Application.GetRemoteStream%2A> 讓您存取時 <xref:System.IO.Stream> ，您必須執行其他工作，將它轉換成您將設定它的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-192">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="2ffd5-193">相反地，您可以讓 WPF <xref:System.IO.Stream> 使用程式碼，將資源檔直接載入至型別的屬性，以處理開啟和轉換。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-193">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="2ffd5-194">下列範例顯示如何使用程式碼，將 <xref:System.Windows.Controls.Page> 直接載入 <xref:System.Windows.Controls.Frame> （ `pageFrame` ）。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-194">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="2ffd5-195">下列範例相當於前一個範例的標記對等用法。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-195">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="2ffd5-196">在變更組建類型之後重建</span><span class="sxs-lookup"><span data-stu-id="2ffd5-196">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="2ffd5-197">在變更應用程式資料檔案的組建類型之後，您必須重建整個應用程式，以確認套用這些變更。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-197">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="2ffd5-198">若您只建置應用程式，則不會套用變更。</span><span class="sxs-lookup"><span data-stu-id="2ffd5-198">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ffd5-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ffd5-199">See also</span></span>

- [<span data-ttu-id="2ffd5-200">WPF 中的 Pack URI</span><span class="sxs-lookup"><span data-stu-id="2ffd5-200">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
