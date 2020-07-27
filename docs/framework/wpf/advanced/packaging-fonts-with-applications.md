---
title: 將字型與應用程式一起封裝
description: 瞭解如何使用 Windows Presentation Foundation 應用程式封裝字型，包括將字型新增為內容和資源專案，以及字體使用方式的限制。
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
ms.openlocfilehash: 725f05c22eda199d86e5ec5dbb6bdd899ee66a5d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166354"
---
# <a name="packaging-fonts-with-applications"></a><span data-ttu-id="58ce6-103">將字型與應用程式一起封裝</span><span class="sxs-lookup"><span data-stu-id="58ce6-103">Packaging Fonts with Applications</span></span>
<span data-ttu-id="58ce6-104">本主題提供如何使用您的應用程式封裝字型的總覽 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="58ce6-104">This topic provides an overview of how to package fonts with your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58ce6-105">與大部分類型的軟體一樣，字型檔是經由授權而非販售的。</span><span class="sxs-lookup"><span data-stu-id="58ce6-105">As with most types of software, font files are licensed, rather than sold.</span></span> <span data-ttu-id="58ce6-106">控制字型使用方式的授權會因廠商而異，但一般大部分的授權（包括涵蓋 Microsoft 隨附于應用程式和 Windows 的字型）都不允許將字型內嵌在應用程式中或以其他方式轉散發。</span><span class="sxs-lookup"><span data-stu-id="58ce6-106">Licenses that govern the use of fonts vary from vendor to vendor but in general most licenses, including those covering the fonts Microsoft supplies with applications and Windows, do not allow the fonts to be embedded within applications or otherwise redistributed.</span></span> <span data-ttu-id="58ce6-107">因此，身為開發人員，您的職責是確保對於您內嵌在應用程式中或是以其他方式轉散發的任何字型，您必須有必要的授權權限。</span><span class="sxs-lookup"><span data-stu-id="58ce6-107">Therefore, as a developer it is your responsibility to ensure that you have the required license rights for any font you embed within an application or otherwise redistribute.</span></span>  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a><span data-ttu-id="58ce6-108">封裝字型簡介</span><span class="sxs-lookup"><span data-stu-id="58ce6-108">Introduction to Packaging Fonts</span></span>  
 <span data-ttu-id="58ce6-109">您可以輕鬆地將字型封裝為應用程式內的資源， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 以顯示使用者介面文字和其他類型的文字內容。</span><span class="sxs-lookup"><span data-stu-id="58ce6-109">You can easily package fonts as resources within your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications to display user interface text and other types of text based content.</span></span> <span data-ttu-id="58ce6-110">字型可以從應用程式的組件檔中分離出來或內嵌於其中。</span><span class="sxs-lookup"><span data-stu-id="58ce6-110">The fonts can be separate from or embedded within the application's assembly files.</span></span> <span data-ttu-id="58ce6-111">您也可以建立僅含資源的字型庫，以供應用程式參考。</span><span class="sxs-lookup"><span data-stu-id="58ce6-111">You can also create a resource-only font library, which your application can reference.</span></span>  
  
 <span data-ttu-id="58ce6-112">OpenType 和 TrueType®字型包含一種類型旗標 fsType，其表示字型的字型內嵌授權許可權。</span><span class="sxs-lookup"><span data-stu-id="58ce6-112">OpenType and TrueType® fonts contain a type flag, fsType, that indicates font embedding licensing rights for the font.</span></span> <span data-ttu-id="58ce6-113">不過，此類型旗標只會參考儲存於文件中的內嵌字型，而不會參考內嵌於應用程式中的字型。</span><span class="sxs-lookup"><span data-stu-id="58ce6-113">However, this type flag only refers to embedded fonts stored in a document–it does not refer to fonts embedded in an application.</span></span> <span data-ttu-id="58ce6-114">您可以藉由建立 <xref:System.Windows.Media.GlyphTypeface> 物件並參考其屬性，來抓取字型的字型嵌入許可權 <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> 。</span><span class="sxs-lookup"><span data-stu-id="58ce6-114">You can retrieve the font embedding rights for a font by creating a <xref:System.Windows.Media.GlyphTypeface> object and referencing its <xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A> property.</span></span> <span data-ttu-id="58ce6-115">如需 fsType 旗標的詳細資訊，請參閱[OpenType 規格](https://www.microsoft.com/typography/otspec/os2.htm)的「OS/2 和 Windows 計量」一節。</span><span class="sxs-lookup"><span data-stu-id="58ce6-115">Refer to the "OS/2 and Windows Metrics" section of the [OpenType Specification](https://www.microsoft.com/typography/otspec/os2.htm) for more information on the fsType flag.</span></span>  
  
 <span data-ttu-id="58ce6-116">[Microsoft 印刷](https://docs.microsoft.com/typography/)樣式網站包含可協助您找出特定字型廠商或尋找自訂工作之字型廠商的連絡人資訊。</span><span class="sxs-lookup"><span data-stu-id="58ce6-116">The [Microsoft Typography](https://docs.microsoft.com/typography/) Web site includes contact information that can help you locate a particular font vendor or find a font vendor for custom work.</span></span>  
  
<a name="adding_fonts_as_content_items"></a>
## <a name="adding-fonts-as-content-items"></a><span data-ttu-id="58ce6-117">將字型新增為內容項目</span><span class="sxs-lookup"><span data-stu-id="58ce6-117">Adding Fonts as Content Items</span></span>  
 <span data-ttu-id="58ce6-118">您可以將字型新增到您的應用程式，以做為與應用程式組件檔分開的專案內容項目。</span><span class="sxs-lookup"><span data-stu-id="58ce6-118">You can add fonts to your application as project content items that are separate from the application's assembly files.</span></span> <span data-ttu-id="58ce6-119">這表示內容項目不會內嵌為組件中的資源。</span><span class="sxs-lookup"><span data-stu-id="58ce6-119">This means that content items are not embedded as resources within an assembly.</span></span> <span data-ttu-id="58ce6-120">下列專案檔範例示範如何定義內容項目。</span><span class="sxs-lookup"><span data-stu-id="58ce6-120">The following project file example shows how to define content items.</span></span>  
  
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
  
 <span data-ttu-id="58ce6-121">為了確保應用程式可以在執行階段使用字型，必須可在應用程式的部署目錄中存取字型。</span><span class="sxs-lookup"><span data-stu-id="58ce6-121">In order to ensure that the application can use the fonts at run time, the fonts must be accessible in the application's deployment directory.</span></span> <span data-ttu-id="58ce6-122">`<CopyToOutputDirectory>`應用程式專案檔中的元素可讓您在建立程式期間，自動將字型複製到應用程式部署目錄。</span><span class="sxs-lookup"><span data-stu-id="58ce6-122">The `<CopyToOutputDirectory>` element in the application's project file allows you to automatically copy the fonts to the application deployment directory during the build process.</span></span> <span data-ttu-id="58ce6-123">下列專案檔範例示範如何將字型複製到部署目錄。</span><span class="sxs-lookup"><span data-stu-id="58ce6-123">The following project file example shows how to copy fonts to the deployment directory.</span></span>  
  
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
  
 <span data-ttu-id="58ce6-124">下列程式碼範例示範如何參考應用程式的字型以做為內容項目 - 參考的內容項目必須與應用程式的組件檔位於相同的目錄。</span><span class="sxs-lookup"><span data-stu-id="58ce6-124">The following code example shows how to reference the application's font as a content item—the referenced content item must be in the same directory as the application's assembly files.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>
## <a name="adding-fonts-as-resource-items"></a><span data-ttu-id="58ce6-125">將字型新增為資源項目</span><span class="sxs-lookup"><span data-stu-id="58ce6-125">Adding Fonts as Resource Items</span></span>  
 <span data-ttu-id="58ce6-126">您可以將字型新增到您的應用程式，以做為內嵌於您應用程式組件檔中的專案資源項目。</span><span class="sxs-lookup"><span data-stu-id="58ce6-126">You can add fonts to your application as project resource items that are embedded within the application's assembly files.</span></span> <span data-ttu-id="58ce6-127">針對資源使用不同的子目錄，可協助組織應用程式的專案檔。</span><span class="sxs-lookup"><span data-stu-id="58ce6-127">Using a separate subdirectory for resources helps to organize the application's project files.</span></span> <span data-ttu-id="58ce6-128">下列專案檔範例示範如何將字型定義為個別子目錄中的資源項目。</span><span class="sxs-lookup"><span data-stu-id="58ce6-128">The following project file example shows how to define fonts as resource items in a separate subdirectory.</span></span>  
  
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
> <span data-ttu-id="58ce6-129">當您將字型當做資源新增至應用程式時，請確定您正在設定 `<Resource>` 元素，而不是 `<EmbeddedResource>` 應用程式專案檔中的元素。</span><span class="sxs-lookup"><span data-stu-id="58ce6-129">When you add fonts as resources to your application, make sure you are setting the `<Resource>` element, and not the `<EmbeddedResource>` element in your application's project file.</span></span> <span data-ttu-id="58ce6-130">`<EmbeddedResource>`不支援組建動作的元素。</span><span class="sxs-lookup"><span data-stu-id="58ce6-130">The `<EmbeddedResource>` element for the build action is not supported.</span></span>  
  
 <span data-ttu-id="58ce6-131">下列標記範例示範如何參考應用程式的字型資源。</span><span class="sxs-lookup"><span data-stu-id="58ce6-131">The following markup example shows how to reference the application's font resources.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a><span data-ttu-id="58ce6-132">從程式碼參考字型資源項目</span><span class="sxs-lookup"><span data-stu-id="58ce6-132">Referencing Font Resource Items from Code</span></span>  
 <span data-ttu-id="58ce6-133">若要從程式碼參考字型資源專案，您必須提供兩部分的字型資源參考：基底統一資源識別元（URI）;和字型位置參考。</span><span class="sxs-lookup"><span data-stu-id="58ce6-133">In order to reference font resource items from code, you must supply a two-part font resource reference: the base uniform resource identifier (URI); and the font location reference.</span></span> <span data-ttu-id="58ce6-134">這些值會用來做為方法的參數 <xref:System.Windows.Media.FontFamily.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="58ce6-134">These values are used as the parameters for the <xref:System.Windows.Media.FontFamily.%23ctor%2A> method.</span></span> <span data-ttu-id="58ce6-135">下列程式碼範例示範如何在名為的專案子目錄中參考應用程式的字型資源 `resources` 。</span><span class="sxs-lookup"><span data-stu-id="58ce6-135">The following code example shows how to reference the application's font resources in the project subdirectory called `resources`.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 <span data-ttu-id="58ce6-136">基底統一資源識別元（URI）可以包含字型資源所在的應用程式子目錄。</span><span class="sxs-lookup"><span data-stu-id="58ce6-136">The base uniform resource identifier (URI) can include the application subdirectory where the font resource resides.</span></span> <span data-ttu-id="58ce6-137">在此情況下，字型位置參考不需要指定目錄，但必須包含前置的 " `./` "，這表示字型資源是在基底統一資源識別元（URI）所指定的相同目錄中。</span><span class="sxs-lookup"><span data-stu-id="58ce6-137">In this case, the font location reference would not need to specify a directory, but would have to include a leading "`./`", which indicates the font resource is in the same directory specified by the base uniform resource identifier (URI).</span></span> <span data-ttu-id="58ce6-138">下列程式碼範例示範參考字型資源項目的替代方法 - 它相當於上述程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="58ce6-138">The following code example shows an alternate way of referencing the font resource item—it is equivalent to the previous code example.</span></span>  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a><span data-ttu-id="58ce6-139">從相同的應用程式子目錄參考字型</span><span class="sxs-lookup"><span data-stu-id="58ce6-139">Referencing Fonts from the Same Application Subdirectory</span></span>  
 <span data-ttu-id="58ce6-140">您可以將應用程式內容與資源檔置於應用程式專案的同一個使用者定義的子目錄內。</span><span class="sxs-lookup"><span data-stu-id="58ce6-140">You can place both application content and resource files within the same user-defined subdirectory of your application project.</span></span> <span data-ttu-id="58ce6-141">下列專案檔範例示範內容頁面和字型資源定義於相同的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="58ce6-141">The following project file example shows a content page and font resources defined in the same subdirectory.</span></span>  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 <span data-ttu-id="58ce6-142">由於應用程式內容和字型位於相同的子目錄，因此，字型參考會相對於應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="58ce6-142">Since the application content and font are in the same subdirectory, the font reference is relative to the application content.</span></span> <span data-ttu-id="58ce6-143">下列範例示範當字型與應用程式位於相同目錄時，如何參考應用程式的字型資源。</span><span class="sxs-lookup"><span data-stu-id="58ce6-143">The following examples show how to reference the application's font resource when the font is in the same directory as the application.</span></span>  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a><span data-ttu-id="58ce6-144">列舉應用程式中的字型</span><span class="sxs-lookup"><span data-stu-id="58ce6-144">Enumerating Fonts in an Application</span></span>  
 <span data-ttu-id="58ce6-145">若要將字型列舉為應用程式中的資源專案，請使用 <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> 或 <xref:System.Windows.Media.Fonts.GetTypefaces%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="58ce6-145">To enumerate fonts as resource items in your application, use either the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> or <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method.</span></span> <span data-ttu-id="58ce6-146">下列範例顯示如何使用 <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> 方法， <xref:System.Windows.Media.FontFamily> 從應用程式字型位置傳回物件的集合。</span><span class="sxs-lookup"><span data-stu-id="58ce6-146">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetFontFamilies%2A> method to return the collection of <xref:System.Windows.Media.FontFamily> objects from the application font location.</span></span> <span data-ttu-id="58ce6-147">在此案例中，應用程式包含名為 "resources"的子目錄。</span><span class="sxs-lookup"><span data-stu-id="58ce6-147">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <span data-ttu-id="58ce6-148">下列範例顯示如何使用 <xref:System.Windows.Media.Fonts.GetTypefaces%2A> 方法， <xref:System.Windows.Media.Typeface> 從應用程式字型位置傳回物件的集合。</span><span class="sxs-lookup"><span data-stu-id="58ce6-148">The following example shows how to use the <xref:System.Windows.Media.Fonts.GetTypefaces%2A> method to return the collection of <xref:System.Windows.Media.Typeface> objects from the application font location.</span></span> <span data-ttu-id="58ce6-149">在此案例中，應用程式包含名為 "resources"的子目錄。</span><span class="sxs-lookup"><span data-stu-id="58ce6-149">In this case, the application contains a subdirectory named "resources".</span></span>  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>
## <a name="creating-a-font-resource-library"></a><span data-ttu-id="58ce6-150">建立字型資源程式庫</span><span class="sxs-lookup"><span data-stu-id="58ce6-150">Creating a Font Resource Library</span></span>  
 <span data-ttu-id="58ce6-151">您可以建立僅含資源的程式庫 (其中僅包含字型) - 這種類型的程式庫專案不會包含任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="58ce6-151">You can create a resource-only library that contains only fonts—no code is part of this type of library project.</span></span> <span data-ttu-id="58ce6-152">建立僅含資源的程式庫是從使用資源的應用程式程式碼中減少資源的常見技術。</span><span class="sxs-lookup"><span data-stu-id="58ce6-152">Creating a resource-only library is a common technique for decoupling resources from the application code that uses them.</span></span> <span data-ttu-id="58ce6-153">這也可讓程式庫組件包含於多個應用程式專案中。</span><span class="sxs-lookup"><span data-stu-id="58ce6-153">This also allows the library assembly to be included with multiple application projects.</span></span> <span data-ttu-id="58ce6-154">下列專案檔範例顯示僅含資源的程式庫專案的主要部分。</span><span class="sxs-lookup"><span data-stu-id="58ce6-154">The following project file example shows the key portions of a resource-only library project.</span></span>  
  
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
  
### <a name="referencing-a-font-in-a-resource-library"></a><span data-ttu-id="58ce6-155">參考資源程式庫中的字型</span><span class="sxs-lookup"><span data-stu-id="58ce6-155">Referencing a Font in a Resource Library</span></span>  
 <span data-ttu-id="58ce6-156">若要從您的應用程式參考資源程式庫中的字型，您必須在程式庫組件名稱前面加上字型參考。</span><span class="sxs-lookup"><span data-stu-id="58ce6-156">To reference a font in a resource library from your application, you must prefix the font reference with the name of the library assembly.</span></span> <span data-ttu-id="58ce6-157">在此案例中，字型資源組件是 "FontLibrary"。</span><span class="sxs-lookup"><span data-stu-id="58ce6-157">In this case, the font resource assembly is "FontLibrary".</span></span> <span data-ttu-id="58ce6-158">若要將組件內的組件名稱與參考分隔開來，請使用 ';' 字元。</span><span class="sxs-lookup"><span data-stu-id="58ce6-158">To separate the assembly name from the reference within the assembly, use a ';' character.</span></span> <span data-ttu-id="58ce6-159">加入 "Component" 關鍵字，後面緊接著對字型名稱的參考，即可完成對字型程式庫資源的完整參考。</span><span class="sxs-lookup"><span data-stu-id="58ce6-159">Adding the "Component" keyword followed by the reference to the font name completes the full reference to the font library's resource.</span></span> <span data-ttu-id="58ce6-160">下列程式碼範例示範如何參考資源程式庫組件中的字型。</span><span class="sxs-lookup"><span data-stu-id="58ce6-160">The following code example shows how to reference a font in a resource library assembly.</span></span>  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
> <span data-ttu-id="58ce6-161">此 SDK 包含一組您可以搭配應用程式使用的範例 OpenType 字型 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="58ce6-161">This SDK contains a set of sample OpenType fonts that you can use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="58ce6-162">字型定義於僅含資源的程式庫中。</span><span class="sxs-lookup"><span data-stu-id="58ce6-162">The fonts are defined in a resource-only library.</span></span> <span data-ttu-id="58ce6-163">如需詳細資訊，請參閱[範例 OpenType 字型套件](sample-opentype-font-pack.md)。</span><span class="sxs-lookup"><span data-stu-id="58ce6-163">For more information, see [Sample OpenType Font Pack](sample-opentype-font-pack.md).</span></span>  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a><span data-ttu-id="58ce6-164">字型使用限制</span><span class="sxs-lookup"><span data-stu-id="58ce6-164">Limitations on Font Usage</span></span>  
 <span data-ttu-id="58ce6-165">下列清單說明在應用程式中封裝和使用字型的幾項限制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="58ce6-165">The following list describes several limitations on the packaging and use of fonts in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications:</span></span>  
  
- <span data-ttu-id="58ce6-166">**字型內嵌權限位元：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式不會檢查或強制執行任何字型內嵌權限位元。</span><span class="sxs-lookup"><span data-stu-id="58ce6-166">**Font embedding permission bits:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not check or enforce any font embedding permission bits.</span></span> <span data-ttu-id="58ce6-167">如需詳細資訊，請參閱[Introduction_to_Packing](#introduction_to_packaging_fonts)字型一節。</span><span class="sxs-lookup"><span data-stu-id="58ce6-167">See the [Introduction_to_Packing Fonts](#introduction_to_packaging_fonts) section for more information.</span></span>  
  
- <span data-ttu-id="58ce6-168">**原始網站字型：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式不允許使用 HTTP 或 ftp 統一資源識別元（URI）的字型參考。</span><span class="sxs-lookup"><span data-stu-id="58ce6-168">**Site of origin fonts:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow a font reference to an http or ftp uniform resource identifier (URI).</span></span>  
  
- <span data-ttu-id="58ce6-169">**使用 pack： notation 的絕對 URI：** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]應用程式不允許您 <xref:System.Windows.Media.FontFamily> 使用 "pack：" 以程式設計方式建立物件，做為字型的絕對統一資源識別元（URI）參考的一部分。</span><span class="sxs-lookup"><span data-stu-id="58ce6-169">**Absolute URI using the pack: notation:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not allow you to create a <xref:System.Windows.Media.FontFamily> object programmatically using "pack:" as part of the absolute uniform resource identifier (URI) reference to a font.</span></span> <span data-ttu-id="58ce6-170">例如， `"pack://application:,,,/resources/#Pericles Light"` 是不正確字型參考。</span><span class="sxs-lookup"><span data-stu-id="58ce6-170">For example, `"pack://application:,,,/resources/#Pericles Light"` is an invalid font reference.</span></span>  
  
- <span data-ttu-id="58ce6-171">**自動字型內嵌︰** 在設計階段期間，不支援搜尋應用程式所使用的字型，也不支援自動將字型內嵌於應用程式的資源中。</span><span class="sxs-lookup"><span data-stu-id="58ce6-171">**Automatic font embedding:** During design time, there is no support for searching an application's use of fonts and automatically embedding the fonts in the application's resources.</span></span>  
  
- <span data-ttu-id="58ce6-172">**字型子集︰** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 應用程式不支援為非固定文件建立字型子集。</span><span class="sxs-lookup"><span data-stu-id="58ce6-172">**Font subsets:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications do not support the creation of font subsets for non-fixed documents.</span></span>  
  
- <span data-ttu-id="58ce6-173">萬一其中含有不正確的參考，應用程式就會回復以使用可用字型。</span><span class="sxs-lookup"><span data-stu-id="58ce6-173">In cases where there is an incorrect reference, the application falls back to using an available font.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58ce6-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58ce6-174">See also</span></span>

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [<span data-ttu-id="58ce6-175">Microsoft 印刷︰連結、新聞和連絡人 (英文)</span><span class="sxs-lookup"><span data-stu-id="58ce6-175">Microsoft Typography: Links, News, and Contacts</span></span>](https://docs.microsoft.com/typography/)
- [<span data-ttu-id="58ce6-176">OpenType 規格 (英文)</span><span class="sxs-lookup"><span data-stu-id="58ce6-176">OpenType Specification</span></span>](https://www.microsoft.com/typography/otspec/)
- [<span data-ttu-id="58ce6-177">OpenType 字型功能</span><span class="sxs-lookup"><span data-stu-id="58ce6-177">OpenType Font Features</span></span>](opentype-font-features.md)
- [<span data-ttu-id="58ce6-178">範例 OpenType 字型套件</span><span class="sxs-lookup"><span data-stu-id="58ce6-178">Sample OpenType Font Pack</span></span>](sample-opentype-font-pack.md)
