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
ms.openlocfilehash: cef2ae26ec4fccd25ca193ba7d441969f36b25a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187082"
---
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="a6440-102">將字型與應用程式一起封裝</span><span class="sxs-lookup"><span data-stu-id="a6440-102">Packaging Fonts with Applications</span></span>
<span data-ttu-id="a6440-103">本主題概述了如何向[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]應用程式打包字體。</span><span class="sxs-lookup"><span data-stu-id="a6440-103">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6440-104">與大部分類型的軟體一樣，字型檔是經由授權而非販售的。</span><span class="sxs-lookup"><span data-stu-id="a6440-104">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="a6440-105">管理字體使用的許可證因供應商而異，但一般來說，大多數許可證（包括涵蓋 Microsoft 提供的應用程式和 Windows 的字體的許可證）不允許將字型內嵌到應用程式中或以其他方式重新分發。</span><span class="sxs-lookup"><span data-stu-id="a6440-105">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts Microsoft supplies with applications and Windows, do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="a6440-106">因此，身為開發人員，您的職責是確保對於您內嵌在應用程式中或是以其他方式轉散發的任何字型，您必須有必要的授權權限。</span><span class="sxs-lookup"><span data-stu-id="a6440-106">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="a6440-107">封裝字型簡介</span><span class="sxs-lookup"><span data-stu-id="a6440-107">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="a6440-108">您可以輕鬆地將字體打包為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中的資源，以顯示使用者介面文本和其他類型的基於文本的內容。</span><span class="sxs-lookup"><span data-stu-id="a6440-108">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="a6440-109">字型可以從應用程式的組件檔中分離出來或內嵌於其中。</span><span class="sxs-lookup"><span data-stu-id="a6440-109">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="a6440-110">您也可以建立僅含資源的字型庫，以供應用程式參考。</span><span class="sxs-lookup"><span data-stu-id="a6440-110">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 <span data-ttu-id="a6440-111">OpenType 和 TrueType® 字體包含一個類型標誌 fsType，指示字型內嵌許可許可權。</span><span class="sxs-lookup"><span data-stu-id="a6440-111">OpenType and TrueType® fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="a6440-112">不過，此類型旗標只會參考儲存於文件中的內嵌字型，而不會參考內嵌於應用程式中的字型。</span><span class="sxs-lookup"><span data-stu-id="a6440-112">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="a6440-113">您可以通過創建<xref:System.Windows.Media.GlyphTypeface>物件並引用其<xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A>屬性來檢索字體的字型內嵌許可權。</span><span class="sxs-lookup"><span data-stu-id="a6440-113">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="a6440-114">有關 fsType 標誌的詳細資訊，請參閱[OpenType 規範](https://www.microsoft.com/typography/otspec/os2.htm)的"OS/2 和 Windows 指標"部分。</span><span class="sxs-lookup"><span data-stu-id="a6440-114">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](https://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="a6440-115">[Microsoft 排版](https://docs.microsoft.com/typography/)網站包含聯繫資訊，可説明您查找特定字體供應商或查找用於自訂工作的字體供應商。</span><span class="sxs-lookup"><span data-stu-id="a6440-115">The [Microsoft Typography](https://docs.microsoft.com/typography/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="a6440-116">將字型新增為內容項目</span><span class="sxs-lookup"><span data-stu-id="a6440-116">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="a6440-117">您可以將字型新增到您的應用程式，以做為與應用程式組件檔分開的專案內容項目。</span><span class="sxs-lookup"><span data-stu-id="a6440-117">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="a6440-118">這表示內容項目不會內嵌為組件中的資源。</span><span class="sxs-lookup"><span data-stu-id="a6440-118">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="a6440-119">下列專案檔範例示範如何定義內容項目。</span><span class="sxs-lookup"><span data-stu-id="a6440-119">The following project file example shows how to define content items.</span></span>  
  
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
  
 <span data-ttu-id="a6440-120">為了確保應用程式可以在執行階段使用字型，必須可在應用程式的部署目錄中存取字型。</span><span class="sxs-lookup"><span data-stu-id="a6440-120">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="a6440-121">應用程式`<CopyToOutputDirectory>`專案檔案中的元素允許您在生成過程中自動將字體複製到應用程式部署目錄。</span><span class="sxs-lookup"><span data-stu-id="a6440-121">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="a6440-122">下列專案檔範例示範如何將字型複製到部署目錄。</span><span class="sxs-lookup"><span data-stu-id="a6440-122">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
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
  
 <span data-ttu-id="a6440-123">下列程式碼範例示範如何參考應用程式的字型以做為內容項目 - 參考的內容項目必須與應用程式的組件檔位於相同的目錄。</span><span class="sxs-lookup"><span data-stu-id="a6440-123">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="a6440-124">將字型新增為資源項目</span><span class="sxs-lookup"><span data-stu-id="a6440-124">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="a6440-125">您可以將字型新增到您的應用程式，以做為內嵌於您應用程式組件檔中的專案資源項目。</span><span class="sxs-lookup"><span data-stu-id="a6440-125">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="a6440-126">針對資源使用不同的子目錄，可協助組織應用程式的專案檔。</span><span class="sxs-lookup"><span data-stu-id="a6440-126">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="a6440-127">下列專案檔範例示範如何將字型定義為個別子目錄中的資源項目。</span><span class="sxs-lookup"><span data-stu-id="a6440-127">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
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
> <span data-ttu-id="a6440-128">將字體作為資源添加到應用程式時，請確保設置`<Resource>`元素，而不是應用程式專案檔案中`<EmbeddedResource>`的元素。</span><span class="sxs-lookup"><span data-stu-id="a6440-128">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="a6440-129">不支援`<EmbeddedResource>`生成操作的元素。</span><span class="sxs-lookup"><span data-stu-id="a6440-129">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="a6440-130">下列標記範例示範如何參考應用程式的字型資源。</span><span class="sxs-lookup"><span data-stu-id="a6440-130">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="a6440-131">從程式碼參考字型資源項目</span><span class="sxs-lookup"><span data-stu-id="a6440-131">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="a6440-132">為了從代碼中引用字體資源項，必須提供由兩部分組成的字體資源引用：基本統一資源識別項 （URI）;和字體位置引用。</span><span class="sxs-lookup"><span data-stu-id="a6440-132">In order to reference font resource items from code, you must supply a two-part font resource reference: the base uniform resource identifier (URI); and the font location reference.</span></span> <span data-ttu-id="a6440-133">這些值用作方法的<xref:System.Windows.Media.FontFamily.%23ctor%2A>參數。</span><span class="sxs-lookup"><span data-stu-id="a6440-133">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="a6440-134">以下代碼示例演示如何在稱為`resources`的專案子目錄中引用應用程式的字體資源。</span><span class="sxs-lookup"><span data-stu-id="a6440-134">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="a6440-135">基本統一資源識別項 （URI） 可以包括字體資源所在的應用程式子目錄。</span><span class="sxs-lookup"><span data-stu-id="a6440-135">The base uniform resource identifier (URI) can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="a6440-136">在這種情況下，字體位置引用不需要指定目錄，但必須包含一個前導""，`./`該表示字體資源位於基本統一資源識別項 （URI） 指定的同一目錄中。</span><span class="sxs-lookup"><span data-stu-id="a6440-136">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base uniform resource identifier (URI).</span></span> <span data-ttu-id="a6440-137">下列程式碼範例示範參考字型資源項目的替代方法 - 它相當於上述程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="a6440-137">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="a6440-138">從相同的應用程式子目錄參考字型</span><span class="sxs-lookup"><span data-stu-id="a6440-138">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="a6440-139">您可以將應用程式內容與資源檔置於應用程式專案的同一個使用者定義的子目錄內。</span><span class="sxs-lookup"><span data-stu-id="a6440-139">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="a6440-140">下列專案檔範例示範內容頁面和字型資源定義於相同的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="a6440-140">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="a6440-141">由於應用程式內容和字型位於相同的子目錄，因此，字型參考會相對於應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="a6440-141">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="a6440-142">下列範例示範當字型與應用程式位於相同目錄時，如何參考應用程式的字型資源。</span><span class="sxs-lookup"><span data-stu-id="a6440-142">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="a6440-143">列舉應用程式中的字型</span><span class="sxs-lookup"><span data-stu-id="a6440-143">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="a6440-144">要將字體枚舉為應用程式中的資源項，請使用 或<xref:System.Windows.Media.Fonts.GetFontFamilies%2A><xref:System.Windows.Media.Fonts.GetTypefaces%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="a6440-144">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="a6440-145">下面的示例演示如何使用 方法<xref:System.Windows.Media.Fonts.GetFontFamilies%2A>從應用程式字體位置返回<xref:System.Windows.Media.FontFamily>物件集合。</span><span class="sxs-lookup"><span data-stu-id="a6440-145">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="a6440-146">在此案例中，應用程式包含名為 "resources"的子目錄。</span><span class="sxs-lookup"><span data-stu-id="a6440-146">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="a6440-147">下面的示例演示如何使用 方法<xref:System.Windows.Media.Fonts.GetTypefaces%2A>從應用程式字體位置返回<xref:System.Windows.Media.Typeface>物件集合。</span><span class="sxs-lookup"><span data-stu-id="a6440-147">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="a6440-148">在此案例中，應用程式包含名為 "resources"的子目錄。</span><span class="sxs-lookup"><span data-stu-id="a6440-148">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="a6440-149">建立字型資源程式庫</span><span class="sxs-lookup"><span data-stu-id="a6440-149">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="a6440-150">您可以建立僅含資源的程式庫 (其中僅包含字型) - 這種類型的程式庫專案不會包含任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="a6440-150">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="a6440-151">建立僅含資源的程式庫是從使用資源的應用程式程式碼中減少資源的常見技術。</span><span class="sxs-lookup"><span data-stu-id="a6440-151">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="a6440-152">這也可讓程式庫組件包含於多個應用程式專案中。</span><span class="sxs-lookup"><span data-stu-id="a6440-152">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="a6440-153">下列專案檔範例顯示僅含資源的程式庫專案的主要部分。</span><span class="sxs-lookup"><span data-stu-id="a6440-153">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="a6440-154">參考資源程式庫中的字型</span><span class="sxs-lookup"><span data-stu-id="a6440-154">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="a6440-155">若要從您的應用程式參考資源程式庫中的字型，您必須在程式庫組件名稱前面加上字型參考。</span><span class="sxs-lookup"><span data-stu-id="a6440-155">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="a6440-156">在此案例中，字型資源組件是 "FontLibrary"。</span><span class="sxs-lookup"><span data-stu-id="a6440-156">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="a6440-157">若要將組件內的組件名稱與參考分隔開來，請使用 ';' 字元。</span><span class="sxs-lookup"><span data-stu-id="a6440-157">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="a6440-158">加入 "Component" 關鍵字，後面緊接著對字型名稱的參考，即可完成對字型程式庫資源的完整參考。</span><span class="sxs-lookup"><span data-stu-id="a6440-158">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="a6440-159">下列程式碼範例示範如何參考資源程式庫組件中的字型。</span><span class="sxs-lookup"><span data-stu-id="a6440-159">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> <span data-ttu-id="a6440-160">此 SDK 包含一組可用於[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式的示例 OpenType 字型。</span><span class="sxs-lookup"><span data-stu-id="a6440-160">This SDK contains a set of sample OpenType fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="a6440-161">字型定義於僅含資源的程式庫中。</span><span class="sxs-lookup"><span data-stu-id="a6440-161">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="a6440-162">有關詳細資訊，請參閱[示例打開字體包](sample-opentype-font-pack.md)。</span><span class="sxs-lookup"><span data-stu-id="a6440-162">For more information, see [Sample OpenType Font Pack](sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a><span data-ttu-id="a6440-163">字型使用限制</span><span class="sxs-lookup"><span data-stu-id="a6440-163">Limitations on Font Usage</span></span>  
 <span data-ttu-id="a6440-164">下面的清單描述了在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式中字體的打包和使用的幾個限制：</span><span class="sxs-lookup"><span data-stu-id="a6440-164">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
- <span data-ttu-id="a6440-165">**字型內嵌權限位元：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式不會檢查或強制執行任何字型內嵌權限位元。</span><span class="sxs-lookup"><span data-stu-id="a6440-165">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="a6440-166">有關詳細資訊，請參閱[Introduction_to_Packing字體](#introduction_to_packaging_fonts)部分。</span><span class="sxs-lookup"><span data-stu-id="a6440-166">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
- <span data-ttu-id="a6440-167">**源地字體：**[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式不允許字體引用 HTTP 或 ftp 統一資源識別項 （URI）。</span><span class="sxs-lookup"><span data-stu-id="a6440-167">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp uniform resource identifier (URI).</span></span>  
  
- <span data-ttu-id="a6440-168">**使用包的絕對 URI：標記法：**[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式不允許使用"pack："以程式設計<xref:System.Windows.Media.FontFamily>方式創建物件，作為對字體的絕對統一資源識別項 （URI） 引用的一部分。</span><span class="sxs-lookup"><span data-stu-id="a6440-168">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute uniform resource identifier (URI) reference to a font.</span></span> <span data-ttu-id="a6440-169">例如，`"pack://application:,,,/resources/#Pericles Light"`不正確字體引用。</span><span class="sxs-lookup"><span data-stu-id="a6440-169">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
- <span data-ttu-id="a6440-170">**自動字型內嵌︰** 在設計階段期間，不支援搜尋應用程式所使用的字型，也不支援自動將字型內嵌於應用程式的資源中。</span><span class="sxs-lookup"><span data-stu-id="a6440-170">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
- <span data-ttu-id="a6440-171">**字型子集︰** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式不支援為非固定文件建立字型子集。</span><span class="sxs-lookup"><span data-stu-id="a6440-171">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
- <span data-ttu-id="a6440-172">萬一其中含有不正確的參考，應用程式就會回復以使用可用字型。</span><span class="sxs-lookup"><span data-stu-id="a6440-172">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6440-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6440-173">See also</span></span>

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [<span data-ttu-id="a6440-174">Microsoft 印刷︰連結、新聞和連絡人 (英文)</span><span class="sxs-lookup"><span data-stu-id="a6440-174">Microsoft Typography: Links, News, and Contacts</span></span>](https://docs.microsoft.com/typography/)
- [<span data-ttu-id="a6440-175">OpenType 規格 (英文)</span><span class="sxs-lookup"><span data-stu-id="a6440-175">OpenType Specification</span></span>](https://www.microsoft.com/typography/otspec/)
- [<span data-ttu-id="a6440-176">OpenType 字型功能</span><span class="sxs-lookup"><span data-stu-id="a6440-176">OpenType Font Features</span></span>](opentype-font-features.md)
- [<span data-ttu-id="a6440-177">範例 OpenType 字型套件</span><span class="sxs-lookup"><span data-stu-id="a6440-177">Sample OpenType Font Pack</span></span>](sample-opentype-font-pack.md)
