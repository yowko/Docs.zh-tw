---
title: 將字型與應用程式一起封裝
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], packaging fonts with
- fonts [WPF], packaging with applications
- typography [WPF], packaging fonts with applications
- packaging fonts with applications [WPF]
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
ms.openlocfilehash: fb91d4b413db512021b90f0d4ba3049fe7333601
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123784"
---
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="dce53-102">將字型與應用程式一起封裝</span><span class="sxs-lookup"><span data-stu-id="dce53-102">Packaging Fonts with Applications</span></span>
<span data-ttu-id="dce53-103">本主題提供的概觀與封裝字型您[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="dce53-103">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dce53-104">與大部分類型的軟體一樣，字型檔是經由授權而非販售的。</span><span class="sxs-lookup"><span data-stu-id="dce53-104">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="dce53-105">控制字型使用的授權不同廠商但一般大部分的授權，包括各家[!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)]提供與應用程式和[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]，不允許將字型內嵌在應用程式或功能重新分配。</span><span class="sxs-lookup"><span data-stu-id="dce53-105">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts [!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)] supplies with applications and [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)], do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="dce53-106">因此，身為開發人員，您的職責是確保對於您內嵌在應用程式中或是以其他方式轉散發的任何字型，您必須有必要的授權權限。</span><span class="sxs-lookup"><span data-stu-id="dce53-106">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  

<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="dce53-107">封裝字型簡介</span><span class="sxs-lookup"><span data-stu-id="dce53-107">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="dce53-108">您可以輕鬆地將字型封裝內的資源為您[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式顯示使用者介面文字與其他類型的文字為基礎之內容。</span><span class="sxs-lookup"><span data-stu-id="dce53-108">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="dce53-109">字型可以從應用程式的組件檔中分離出來或內嵌於其中。</span><span class="sxs-lookup"><span data-stu-id="dce53-109">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="dce53-110">您也可以建立僅含資源的字型庫，以供應用程式參考。</span><span class="sxs-lookup"><span data-stu-id="dce53-110">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] <span data-ttu-id="dce53-111">和[!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)]字型包含類型旗標 fsType，表示字型的字型內嵌授權權限。</span><span class="sxs-lookup"><span data-stu-id="dce53-111">and [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="dce53-112">不過，此類型旗標只會參考儲存於文件中的內嵌字型，而不會參考內嵌於應用程式中的字型。</span><span class="sxs-lookup"><span data-stu-id="dce53-112">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="dce53-113">您可以擷取內嵌字型的權限，藉由建立字型<xref:System.Windows.Media.GlyphTypeface>物件，並參考其<xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="dce53-113">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="dce53-114">請參閱 「 OS/2 和 Windows 度量 」 一節[OpenType 規格](https://www.microsoft.com/typography/otspec/os2.htm)如需 fsType 旗標。</span><span class="sxs-lookup"><span data-stu-id="dce53-114">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](https://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="dce53-115">[Microsoft 印刷](https://docs.microsoft.com/typography/)Web 站台都包含可協助您找出特定字型供應商，或尋找自訂工作的字型的供應商的連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="dce53-115">The [Microsoft Typography](https://docs.microsoft.com/typography/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="dce53-116">將字型新增為內容項目</span><span class="sxs-lookup"><span data-stu-id="dce53-116">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="dce53-117">您可以將字型新增到您的應用程式，以做為與應用程式組件檔分開的專案內容項目。</span><span class="sxs-lookup"><span data-stu-id="dce53-117">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="dce53-118">這表示內容項目不會內嵌為組件中的資源。</span><span class="sxs-lookup"><span data-stu-id="dce53-118">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="dce53-119">下列專案檔範例示範如何定義內容項目。</span><span class="sxs-lookup"><span data-stu-id="dce53-119">The following project file example shows how to define content items.</span></span>  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Content Include="Peric.ttf" />  
    <Content Include="Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
 <span data-ttu-id="dce53-120">為了確保應用程式可以在執行階段使用字型，必須可在應用程式的部署目錄中存取字型。</span><span class="sxs-lookup"><span data-stu-id="dce53-120">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="dce53-121">`<CopyToOutputDirectory>`應用程式的專案檔中的項目可讓您自動將字型複製到應用程式部署目錄中，建置程序期間變更。</span><span class="sxs-lookup"><span data-stu-id="dce53-121">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="dce53-122">下列專案檔範例示範如何將字型複製到部署目錄。</span><span class="sxs-lookup"><span data-stu-id="dce53-122">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
```xml  
<ItemGroup>  
  <Content Include="Peric.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
  <Content Include="Pericl.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
</ItemGroup>  
```  
  
 <span data-ttu-id="dce53-123">下列程式碼範例示範如何參考應用程式的字型以做為內容項目 - 參考的內容項目必須與應用程式的組件檔位於相同的目錄。</span><span class="sxs-lookup"><span data-stu-id="dce53-123">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="dce53-124">將字型新增為資源項目</span><span class="sxs-lookup"><span data-stu-id="dce53-124">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="dce53-125">您可以將字型新增到您的應用程式，以做為內嵌於您應用程式組件檔中的專案資源項目。</span><span class="sxs-lookup"><span data-stu-id="dce53-125">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="dce53-126">針對資源使用不同的子目錄，可協助組織應用程式的專案檔。</span><span class="sxs-lookup"><span data-stu-id="dce53-126">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="dce53-127">下列專案檔範例示範如何將字型定義為個別子目錄中的資源項目。</span><span class="sxs-lookup"><span data-stu-id="dce53-127">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Resource Include="resources\Peric.ttf" />  
    <Resource Include="resources\Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
> [!NOTE]
>  <span data-ttu-id="dce53-128">當您將字型當做資源新增您的應用程式時，請確定您要設定`<Resource>`項目，而非`<EmbeddedResource>`您的應用程式專案檔中的項目。</span><span class="sxs-lookup"><span data-stu-id="dce53-128">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="dce53-129">`<EmbeddedResource>`不支援建置動作的項目。</span><span class="sxs-lookup"><span data-stu-id="dce53-129">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="dce53-130">下列標記範例示範如何參考應用程式的字型資源。</span><span class="sxs-lookup"><span data-stu-id="dce53-130">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="dce53-131">從程式碼參考字型資源項目</span><span class="sxs-lookup"><span data-stu-id="dce53-131">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="dce53-132">若要從程式碼參考字型資源項目，您必須提供兩部分的字型資源參考︰ 基底[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; 以及字型位置參考。</span><span class="sxs-lookup"><span data-stu-id="dce53-132">In order to reference font resource items from code, you must supply a two-part font resource reference: the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; and the font location reference.</span></span> <span data-ttu-id="dce53-133">使用這些值做為參數<xref:System.Windows.Media.FontFamily.%23ctor%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="dce53-133">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="dce53-134">下列程式碼範例示範如何參考呼叫的專案子目錄中的應用程式的字型資源`resources`。</span><span class="sxs-lookup"><span data-stu-id="dce53-134">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="dce53-135">基底[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]可以包含字型資源所在的 [application] 子目錄。</span><span class="sxs-lookup"><span data-stu-id="dce53-135">The base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="dce53-136">在此情況下，就不需要指定的目錄中，字型位置參考，但必須包含前置字元 」`./`"，表示字型資源位於相同的目錄指定的基底[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dce53-136">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span> <span data-ttu-id="dce53-137">下列程式碼範例示範參考字型資源項目的替代方法 - 它相當於上述程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="dce53-137">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="dce53-138">從相同的應用程式子目錄參考字型</span><span class="sxs-lookup"><span data-stu-id="dce53-138">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="dce53-139">您可以將應用程式內容與資源檔置於應用程式專案的同一個使用者定義的子目錄內。</span><span class="sxs-lookup"><span data-stu-id="dce53-139">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="dce53-140">下列專案檔範例示範內容頁面和字型資源定義於相同的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="dce53-140">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="dce53-141">由於應用程式內容和字型位於相同的子目錄，因此，字型參考會相對於應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="dce53-141">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="dce53-142">下列範例示範當字型與應用程式位於相同目錄時，如何參考應用程式的字型資源。</span><span class="sxs-lookup"><span data-stu-id="dce53-142">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="dce53-143">列舉應用程式中的字型</span><span class="sxs-lookup"><span data-stu-id="dce53-143">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="dce53-144">若要列舉字型做為應用程式中的資源項目，請使用<xref:System.Windows.Media.Fonts.GetFontFamilies%2A>或<xref:System.Windows.Media.Fonts.GetTypefaces%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="dce53-144">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="dce53-145">下列範例示範如何使用<xref:System.Windows.Media.Fonts.GetFontFamilies%2A>方法傳回的集合<xref:System.Windows.Media.FontFamily>從應用程式字型位置的物件。</span><span class="sxs-lookup"><span data-stu-id="dce53-145">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="dce53-146">在此案例中，應用程式包含名為 "resources"的子目錄。</span><span class="sxs-lookup"><span data-stu-id="dce53-146">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="dce53-147">下列範例示範如何使用<xref:System.Windows.Media.Fonts.GetTypefaces%2A>方法傳回的集合<xref:System.Windows.Media.Typeface>從應用程式字型位置的物件。</span><span class="sxs-lookup"><span data-stu-id="dce53-147">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="dce53-148">在此案例中，應用程式包含名為 "resources"的子目錄。</span><span class="sxs-lookup"><span data-stu-id="dce53-148">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="dce53-149">建立字型資源程式庫</span><span class="sxs-lookup"><span data-stu-id="dce53-149">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="dce53-150">您可以建立僅含資源的程式庫 (其中僅包含字型) - 這種類型的程式庫專案不會包含任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="dce53-150">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="dce53-151">建立僅含資源的程式庫是從使用資源的應用程式程式碼中減少資源的常見技術。</span><span class="sxs-lookup"><span data-stu-id="dce53-151">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="dce53-152">這也可讓程式庫組件包含於多個應用程式專案中。</span><span class="sxs-lookup"><span data-stu-id="dce53-152">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="dce53-153">下列專案檔範例顯示僅含資源的程式庫專案的主要部分。</span><span class="sxs-lookup"><span data-stu-id="dce53-153">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
```xml  
<PropertyGroup>  
  <AssemblyName>FontLibrary</AssemblyName>  
  <OutputType>library</OutputType>  
  ...  
</PropertyGroup>  
...  
<ItemGroup>  
  <Resource Include="Kooten.ttf" />  
  <Resource Include="Pesca.ttf" />  
</ItemGroup  
```  
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="dce53-154">參考資源程式庫中的字型</span><span class="sxs-lookup"><span data-stu-id="dce53-154">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="dce53-155">若要從您的應用程式參考資源程式庫中的字型，您必須在程式庫組件名稱前面加上字型參考。</span><span class="sxs-lookup"><span data-stu-id="dce53-155">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="dce53-156">在此案例中，字型資源組件是 "FontLibrary"。</span><span class="sxs-lookup"><span data-stu-id="dce53-156">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="dce53-157">若要將組件內的組件名稱與參考分隔開來，請使用 ';' 字元。</span><span class="sxs-lookup"><span data-stu-id="dce53-157">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="dce53-158">加入 "Component" 關鍵字，後面緊接著對字型名稱的參考，即可完成對字型程式庫資源的完整參考。</span><span class="sxs-lookup"><span data-stu-id="dce53-158">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="dce53-159">下列程式碼範例示範如何參考資源程式庫組件中的字型。</span><span class="sxs-lookup"><span data-stu-id="dce53-159">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  <span data-ttu-id="dce53-160">此 SDK 包含一組範例[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]您可以搭配使用的字型[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="dce53-160">This SDK contains a set of sample [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="dce53-161">字型定義於僅含資源的程式庫中。</span><span class="sxs-lookup"><span data-stu-id="dce53-161">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="dce53-162">如需詳細資訊，請參閱[範例 OpenType 字型套件](sample-opentype-font-pack.md)。</span><span class="sxs-lookup"><span data-stu-id="dce53-162">For more information, see [Sample OpenType Font Pack](sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a><span data-ttu-id="dce53-163">字型使用限制</span><span class="sxs-lookup"><span data-stu-id="dce53-163">Limitations on Font Usage</span></span>  
 <span data-ttu-id="dce53-164">下列清單描述上的封裝和使用字型中的幾項限制[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式：</span><span class="sxs-lookup"><span data-stu-id="dce53-164">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
-   <span data-ttu-id="dce53-165">**字型內嵌權限位元：**[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式不會檢查或強制執行任何字型內嵌權限位元。</span><span class="sxs-lookup"><span data-stu-id="dce53-165">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="dce53-166">請參閱[封裝字型簡介](#introduction_to_packaging_fonts)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="dce53-166">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
-   <span data-ttu-id="dce53-167">**原始字型的網站：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式不允許 http 或 ftp 的字型參考[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dce53-167">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span>  
  
-   <span data-ttu-id="dce53-168">**使用組件的絕對 URI： 標記法：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式不允許您建立<xref:System.Windows.Media.FontFamily>物件以程式設計方式使用 「 組件:"一部分絕對[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]字型參考。</span><span class="sxs-lookup"><span data-stu-id="dce53-168">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] reference to a font.</span></span> <span data-ttu-id="dce53-169">比方說，`"pack://application:,,,/resources/#Pericles Light"`是無效的字型參考。</span><span class="sxs-lookup"><span data-stu-id="dce53-169">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
-   <span data-ttu-id="dce53-170">**自動字型內嵌：** 在設計階段期間沒有支援搜尋的應用程式使用的字型和自動將字型內嵌在應用程式的資源。</span><span class="sxs-lookup"><span data-stu-id="dce53-170">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
-   <span data-ttu-id="dce53-171">**字型子集︰**[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式不支援為非固定文件建立字型子集。</span><span class="sxs-lookup"><span data-stu-id="dce53-171">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
-   <span data-ttu-id="dce53-172">萬一其中含有不正確的參考，應用程式就會回復以使用可用字型。</span><span class="sxs-lookup"><span data-stu-id="dce53-172">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce53-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dce53-173">See also</span></span>

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [<span data-ttu-id="dce53-174">Microsoft 印刷︰連結、 新聞和連絡人</span><span class="sxs-lookup"><span data-stu-id="dce53-174">Microsoft Typography: Links, News, and Contacts</span></span>](https://docs.microsoft.com/typography/)
- [<span data-ttu-id="dce53-175">OpenType 規格</span><span class="sxs-lookup"><span data-stu-id="dce53-175">OpenType Specification</span></span>](https://www.microsoft.com/typography/otspec/)
- [<span data-ttu-id="dce53-176">OpenType 字型功能</span><span class="sxs-lookup"><span data-stu-id="dce53-176">OpenType Font Features</span></span>](opentype-font-features.md)
- [<span data-ttu-id="dce53-177">範例 OpenType 字型套件</span><span class="sxs-lookup"><span data-stu-id="dce53-177">Sample OpenType Font Pack</span></span>](sample-opentype-font-pack.md)
