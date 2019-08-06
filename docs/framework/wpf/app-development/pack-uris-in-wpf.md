---
title: WPF 中的 Pack URI
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: f9ea4acfc7ba86d3424bb11af0de685651f99c61
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796750"
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="8cde6-102">WPF 中的 Pack URI</span><span class="sxs-lookup"><span data-stu-id="8cde6-102">Pack URIs in WPF</span></span>

<span data-ttu-id="8cde6-103">在 Windows Presentation Foundation (WPF) 中[!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] , 用來以許多方式識別和載入檔案, 包括下列各項:</span><span class="sxs-lookup"><span data-stu-id="8cde6-103">In Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] are used to identify and load files in many ways, including the following:</span></span>

- <span data-ttu-id="8cde6-104">指定要[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]在應用程式第一次啟動時顯示的。</span><span class="sxs-lookup"><span data-stu-id="8cde6-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>

- <span data-ttu-id="8cde6-105">載入影像。</span><span class="sxs-lookup"><span data-stu-id="8cde6-105">Loading images.</span></span>

- <span data-ttu-id="8cde6-106">巡覽至頁面。</span><span class="sxs-lookup"><span data-stu-id="8cde6-106">Navigating to pages.</span></span>

- <span data-ttu-id="8cde6-107">載入不可執行的資料檔案。</span><span class="sxs-lookup"><span data-stu-id="8cde6-107">Loading non-executable data files.</span></span>

<span data-ttu-id="8cde6-108">此外, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]也可以用來從各種不同的位置識別和載入檔案, 包括下列各項:</span><span class="sxs-lookup"><span data-stu-id="8cde6-108">Furthermore, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] can be used to identify and load files from a variety of locations, including the following:</span></span>

- <span data-ttu-id="8cde6-109">目前的組件。</span><span class="sxs-lookup"><span data-stu-id="8cde6-109">The current assembly.</span></span>

- <span data-ttu-id="8cde6-110">所參考的組件。</span><span class="sxs-lookup"><span data-stu-id="8cde6-110">A referenced assembly.</span></span>

- <span data-ttu-id="8cde6-111">與組件相對的位置。</span><span class="sxs-lookup"><span data-stu-id="8cde6-111">A location relative to an assembly.</span></span>

- <span data-ttu-id="8cde6-112">應用程式的來源網站。</span><span class="sxs-lookup"><span data-stu-id="8cde6-112">The application's site of origin.</span></span>

<span data-ttu-id="8cde6-113">為了提供一致的機制, 從這些位置識別和載入這些類型的檔案, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]會利用*pack URI 配置*的擴充性。</span><span class="sxs-lookup"><span data-stu-id="8cde6-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="8cde6-114">本主題提供配置的總覽, 涵蓋如何針對各種案例建立套件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 、討論絕對和相對[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]和[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]解決方式, 再顯示如何使用這兩個標記的套件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]和程式碼。</span><span class="sxs-lookup"><span data-stu-id="8cde6-114">This topic provides an overview of the scheme, covers how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for a variety of scenarios, discusses absolute and relative [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] and [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution, before showing how to use pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] from both markup and code.</span></span>

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a><span data-ttu-id="8cde6-115">套件 URI 配置</span><span class="sxs-lookup"><span data-stu-id="8cde6-115">The Pack URI Scheme</span></span>

<span data-ttu-id="8cde6-116">套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]配置是由[開放式封裝慣例](https://go.microsoft.com/fwlink/?LinkID=71255)(OPC) 規格所使用, 其描述用於組織和識別內容的模型。</span><span class="sxs-lookup"><span data-stu-id="8cde6-116">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme is used by the [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="8cde6-117">此模型的主要元素是封裝和元件, 其中*封裝*是一或多個邏輯*元件*的邏輯容器。</span><span class="sxs-lookup"><span data-stu-id="8cde6-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="8cde6-118">下圖說明這個概念。</span><span class="sxs-lookup"><span data-stu-id="8cde6-118">The following figure illustrates this concept.</span></span>

![套件和部分圖表](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

<span data-ttu-id="8cde6-120">為了識別元件, OPC 規格會利用 RFC 2396 (統一資源識別項 (URI) 的擴充性:一般語法) 來定義套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]配置。</span><span class="sxs-lookup"><span data-stu-id="8cde6-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme.</span></span>

<span data-ttu-id="8cde6-121">由[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]指定的配置由其前置詞定義; HTTP、ftp 和檔案都是已知的範例。</span><span class="sxs-lookup"><span data-stu-id="8cde6-121">The scheme that is specified by a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="8cde6-122">套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]配置會使用 "pack" 作為其配置, 並包含兩個元件: 授權單位和路徑。</span><span class="sxs-lookup"><span data-stu-id="8cde6-122">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="8cde6-123">以下是套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]的格式。</span><span class="sxs-lookup"><span data-stu-id="8cde6-123">The following is the format for a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

<span data-ttu-id="8cde6-124">pack://*授權*/單位*路徑*</span><span class="sxs-lookup"><span data-stu-id="8cde6-124">pack://*authority*/*path*</span></span>

<span data-ttu-id="8cde6-125">*授權*單位會指定元件所包含的封裝類型, 而*路徑*則會指定元件在封裝內的位置。</span><span class="sxs-lookup"><span data-stu-id="8cde6-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>

<span data-ttu-id="8cde6-126">下圖說明這個概念︰</span><span class="sxs-lookup"><span data-stu-id="8cde6-126">This concept is illustrated by the following figure:</span></span>

![套件、授權和路徑之間的關聯性](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

<span data-ttu-id="8cde6-128">套件和組件與應用程式和檔案類似，其中應用程式 (套件) 可以包括一或多個檔案 (組件)，包括︰</span><span class="sxs-lookup"><span data-stu-id="8cde6-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>

- <span data-ttu-id="8cde6-129">編譯為本機組件的資源檔。</span><span class="sxs-lookup"><span data-stu-id="8cde6-129">Resource files that are compiled into the local assembly.</span></span>

- <span data-ttu-id="8cde6-130">編譯為所參考組件的資源檔。</span><span class="sxs-lookup"><span data-stu-id="8cde6-130">Resource files that are compiled into a referenced assembly.</span></span>

- <span data-ttu-id="8cde6-131">編譯為參考組件的資源檔。</span><span class="sxs-lookup"><span data-stu-id="8cde6-131">Resource files that are compiled into a referencing assembly.</span></span>

- <span data-ttu-id="8cde6-132">內容檔。</span><span class="sxs-lookup"><span data-stu-id="8cde6-132">Content files.</span></span>

- <span data-ttu-id="8cde6-133">來源網站檔案。</span><span class="sxs-lookup"><span data-stu-id="8cde6-133">Site of origin files.</span></span>

<span data-ttu-id="8cde6-134">若要存取這些類型的檔[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , 可支援兩個授權單位: application:///和 siteoforigin:///。</span><span class="sxs-lookup"><span data-stu-id="8cde6-134">To access these types of files, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="8cde6-135">application:/// 授權識別在編譯時期已知的應用程式資料檔，包括資源檔和內容檔。</span><span class="sxs-lookup"><span data-stu-id="8cde6-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="8cde6-136">siteoforigin:/// 授權識別來源網站檔案。</span><span class="sxs-lookup"><span data-stu-id="8cde6-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="8cde6-137">下圖顯示每個授權的範圍。</span><span class="sxs-lookup"><span data-stu-id="8cde6-137">The scope of each authority is shown in the following figure.</span></span>

![封裝 URI 圖表](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> <span data-ttu-id="8cde6-139">套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]的授權元件是內嵌[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]的, 它會指向封裝, 而且必須符合 RFC 2396。</span><span class="sxs-lookup"><span data-stu-id="8cde6-139">The authority component of a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is an embedded [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="8cde6-140">此外，"/" 字元必須取代為 "," 字元，而且必須逸出 "%" 和 "?" 這類保留字元。</span><span class="sxs-lookup"><span data-stu-id="8cde6-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="8cde6-141">如需詳細資料，請參閱 OPC。</span><span class="sxs-lookup"><span data-stu-id="8cde6-141">See the OPC for details.</span></span>

<span data-ttu-id="8cde6-142">下列各節說明如何使用這兩[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]個授權單位來建立套件, 並搭配適當的路徑來識別資源、內容和來源網站檔案。</span><span class="sxs-lookup"><span data-stu-id="8cde6-142">The following sections explain how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a><span data-ttu-id="8cde6-143">資源檔套件 URI</span><span class="sxs-lookup"><span data-stu-id="8cde6-143">Resource File Pack URIs</span></span>

<span data-ttu-id="8cde6-144">資源檔會設定為[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Resource`專案, 並編譯成元件。</span><span class="sxs-lookup"><span data-stu-id="8cde6-144">Resource files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Resource` items and are compiled into assemblies.</span></span> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="8cde6-145">支援套件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]的結構, 可用來識別編譯成本機組件或編譯成元件 (從本機組件參考) 的資源檔。</span><span class="sxs-lookup"><span data-stu-id="8cde6-145">supports the construction of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a><span data-ttu-id="8cde6-146">本機組件資源檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-146">Local Assembly Resource File</span></span>

<span data-ttu-id="8cde6-147">編譯為[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]本機組件之資源檔的套件會使用下列授權和路徑:</span><span class="sxs-lookup"><span data-stu-id="8cde6-147">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>

- <span data-ttu-id="8cde6-148">**授權**：application:///。</span><span class="sxs-lookup"><span data-stu-id="8cde6-148">**Authority**: application:///.</span></span>

- <span data-ttu-id="8cde6-149">**路徑**:資源檔的名稱, 包括其相對於本機組件專案資料夾根目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="8cde6-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>

<span data-ttu-id="8cde6-150">下列範例會顯示位於本機[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]元件之[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]專案資料夾根目錄中的資源檔套件。</span><span class="sxs-lookup"><span data-stu-id="8cde6-150">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="8cde6-151">下列範例會顯示位於本機[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]元件之[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]專案資料夾之子資料夾中的資源檔套件。</span><span class="sxs-lookup"><span data-stu-id="8cde6-151">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="8cde6-152">所參考的組件資源檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-152">Referenced Assembly Resource File</span></span>

<span data-ttu-id="8cde6-153">編譯成[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考元件之資源檔的套件會使用下列授權和路徑:</span><span class="sxs-lookup"><span data-stu-id="8cde6-153">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>

- <span data-ttu-id="8cde6-154">**授權**：application:///。</span><span class="sxs-lookup"><span data-stu-id="8cde6-154">**Authority**: application:///.</span></span>

- <span data-ttu-id="8cde6-155">**路徑**:編譯成參考元件之資源檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="8cde6-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="8cde6-156">路徑必須符合下列格式：</span><span class="sxs-lookup"><span data-stu-id="8cde6-156">The path must conform to the following format:</span></span>

  <span data-ttu-id="8cde6-157">*AssemblyShortName*{ *;版本*] { *;PublicKey*]; 元件/*路徑*</span><span class="sxs-lookup"><span data-stu-id="8cde6-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>

  - <span data-ttu-id="8cde6-158">**AssemblyShortName**：所參考組件的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="8cde6-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>

  - <span data-ttu-id="8cde6-159">**;Version** [選擇性]：包含資源檔之參考組件的版本。</span><span class="sxs-lookup"><span data-stu-id="8cde6-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="8cde6-160">這是在載入具有相同簡短名稱的兩個以上參考組件時使用。</span><span class="sxs-lookup"><span data-stu-id="8cde6-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="8cde6-161">**;PublicKey** [選擇性]：用來簽署參考組件的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="8cde6-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="8cde6-162">這是在載入具有相同簡短名稱的兩個以上參考組件時使用。</span><span class="sxs-lookup"><span data-stu-id="8cde6-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>

  - <span data-ttu-id="8cde6-163">**;component**︰指定從本機組件參考所參考的組件。</span><span class="sxs-lookup"><span data-stu-id="8cde6-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>

  - <span data-ttu-id="8cde6-164">**/Path**︰相對於所參考組件專案資料夾根之資源檔的名稱，包括其路徑。</span><span class="sxs-lookup"><span data-stu-id="8cde6-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>

<span data-ttu-id="8cde6-165">下列範例會顯示位於所[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考元件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]之專案資料夾根目錄中的資源檔套件。</span><span class="sxs-lookup"><span data-stu-id="8cde6-165">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

<span data-ttu-id="8cde6-166">下列範例會顯示位於所[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考元件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]之專案資料夾之子資料夾中的資源檔套件。</span><span class="sxs-lookup"><span data-stu-id="8cde6-166">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

<span data-ttu-id="8cde6-167">下列範例會顯示[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]資源檔的套件, 該檔案位於參考的版本特定元件之專案資料夾的根資料夾中。</span><span class="sxs-lookup"><span data-stu-id="8cde6-167">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

<span data-ttu-id="8cde6-168">請注意, 所[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考元件資源檔的 pack 語法只能搭配 application:///授權單位使用。</span><span class="sxs-lookup"><span data-stu-id="8cde6-168">Note that the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="8cde6-169">例如, 中不支援下列各項[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8cde6-169">For example, the following is not supported in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a><span data-ttu-id="8cde6-170">內容檔套件 URI</span><span class="sxs-lookup"><span data-stu-id="8cde6-170">Content File Pack URIs</span></span>

<span data-ttu-id="8cde6-171">內容檔案[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]的套件會使用下列授權和路徑:</span><span class="sxs-lookup"><span data-stu-id="8cde6-171">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a content file uses the following authority and path:</span></span>

- <span data-ttu-id="8cde6-172">**授權**：application:///。</span><span class="sxs-lookup"><span data-stu-id="8cde6-172">**Authority**: application:///.</span></span>

- <span data-ttu-id="8cde6-173">**路徑**:內容檔案的名稱, 包括其相對於應用程式主要可執行元件之檔案系統位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="8cde6-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>

<span data-ttu-id="8cde6-174">下列範例會顯示[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]內容檔案的套件, 該檔案位於與可執行檔元件相同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="8cde6-174">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>

`pack://application:,,,/ContentFile.xaml`

<span data-ttu-id="8cde6-175">下列範例會顯示[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]內容檔案的套件, 該檔案位於相對於應用程式可執行元件的子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="8cde6-175">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> <span data-ttu-id="8cde6-176">無法流覽 HTML 內容檔。</span><span class="sxs-lookup"><span data-stu-id="8cde6-176">HTML content files cannot be navigated to.</span></span> <span data-ttu-id="8cde6-177">此[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]配置只支援流覽至位於來源網站的 HTML 檔案。</span><span class="sxs-lookup"><span data-stu-id="8cde6-177">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme only supports navigation to HTML files that are located at the site of origin.</span></span>

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="8cde6-178">來源網站套件 URI</span><span class="sxs-lookup"><span data-stu-id="8cde6-178">Site of Origin Pack URIs</span></span>

<span data-ttu-id="8cde6-179">來源網站[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]檔案的套件會使用下列授權和路徑:</span><span class="sxs-lookup"><span data-stu-id="8cde6-179">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a site of origin file uses the following authority and path:</span></span>

- <span data-ttu-id="8cde6-180">**授權**：siteoforigin:///。</span><span class="sxs-lookup"><span data-stu-id="8cde6-180">**Authority**: siteoforigin:///.</span></span>

- <span data-ttu-id="8cde6-181">**路徑**:來源網站檔案的名稱, 包括其相對於啟動可執行檔元件之位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="8cde6-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>

<span data-ttu-id="8cde6-182">下列範例會顯示原始[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]網站檔案的套件, 並儲存在可執行檔元件啟動的位置。</span><span class="sxs-lookup"><span data-stu-id="8cde6-182">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

<span data-ttu-id="8cde6-183">下列範例顯示的是原始[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]網站檔案的套件, 儲存在相對於啟動應用程式可執行元件之位置的子資料夾中。</span><span class="sxs-lookup"><span data-stu-id="8cde6-183">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a><span data-ttu-id="8cde6-184">分頁檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-184">Page Files</span></span>

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="8cde6-185">設定為[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page`專案的檔案會以與資源檔相同的方式編譯成元件。</span><span class="sxs-lookup"><span data-stu-id="8cde6-185">files that are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="8cde6-186">因此, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page`可以使用資源檔的套件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]來識別專案。</span><span class="sxs-lookup"><span data-stu-id="8cde6-186">Consequently, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items can be identified using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files.</span></span>

<span data-ttu-id="8cde6-187">通常設定為[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]專案的檔類型,具有下列其中一項做為其根項目:`Page`</span><span class="sxs-lookup"><span data-stu-id="8cde6-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items have one of the following as their root element:</span></span>

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="8cde6-188">絕對與相對套件 URI</span><span class="sxs-lookup"><span data-stu-id="8cde6-188">Absolute vs. Relative Pack URIs</span></span>

<span data-ttu-id="8cde6-189">完整套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]包含配置、授權和路徑, 而且會被視為絕對套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8cde6-189">A fully qualified pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] includes the scheme, the authority, and the path, and it is considered an absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="8cde6-190">做為開發人員的簡化[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , 元素通常可讓您使用相對套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]設定適當的屬性, 其中只包含路徑。</span><span class="sxs-lookup"><span data-stu-id="8cde6-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], which includes only the path.</span></span>

<span data-ttu-id="8cde6-191">例如, 請考慮本機組件中資源[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]檔的下列絕對套件。</span><span class="sxs-lookup"><span data-stu-id="8cde6-191">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file in the local assembly.</span></span>

`pack://application:,,,/ResourceFile.xaml`

<span data-ttu-id="8cde6-192">參考此資源[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]檔的相對套件如下所示。</span><span class="sxs-lookup"><span data-stu-id="8cde6-192">The relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that refers to this resource file would be the following.</span></span>

`/ResourceFile.xaml`

> [!NOTE]
> <span data-ttu-id="8cde6-193">由於原始網站檔案不會與元件相關聯, 因此只能使用絕對套件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]來參考它們。</span><span class="sxs-lookup"><span data-stu-id="8cde6-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span></span>

<span data-ttu-id="8cde6-194">根據預設, 相對套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]會被視為相對於標記或包含參考之程式碼的位置。</span><span class="sxs-lookup"><span data-stu-id="8cde6-194">By default, a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="8cde6-195">不過, 如果使用前導反斜線, 則會將相對[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]套件參考視為相對於應用程式的根目錄。</span><span class="sxs-lookup"><span data-stu-id="8cde6-195">If a leading backslash is used, however, the relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="8cde6-196">例如，請考慮下列專案結構。</span><span class="sxs-lookup"><span data-stu-id="8cde6-196">For example, consider the following project structure.</span></span>

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

<span data-ttu-id="8cde6-197">如果 Page1 包含[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考*根*\SubFolder\Page2.xaml 的, 則參考可以使用下列相對套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8cde6-197">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`Page2.xaml`

<span data-ttu-id="8cde6-198">如果 Page1 包含[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考*根*\Page2.xaml 的, 則參考可以使用下列相對套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8cde6-198">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a><span data-ttu-id="8cde6-199">套件 URI 解析</span><span class="sxs-lookup"><span data-stu-id="8cde6-199">Pack URI Resolution</span></span>

<span data-ttu-id="8cde6-200">[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] Pack[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]的格式可以讓不同類型的檔案封裝起來相同。</span><span class="sxs-lookup"><span data-stu-id="8cde6-200">The format of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] makes it possible for pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for different types of files to look the same.</span></span> <span data-ttu-id="8cde6-201">例如, 請考慮下列絕對套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8cde6-201">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`pack://application:,,,/ResourceOrContentFile.xaml`

<span data-ttu-id="8cde6-202">這個絕對套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]可以參考本機組件或內容檔案中的資源檔。</span><span class="sxs-lookup"><span data-stu-id="8cde6-202">This absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="8cde6-203">對於下列相對[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]來說也是如此。</span><span class="sxs-lookup"><span data-stu-id="8cde6-203">The same is true for the following relative [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

`/ResourceOrContentFile.xaml`

<span data-ttu-id="8cde6-204">為了判斷套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]所參考的檔案類型, 會使用下列啟發學習法[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]解析本機組件和內容檔案中的資源檔:</span><span class="sxs-lookup"><span data-stu-id="8cde6-204">In order to determine the type of file that a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolves [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files in local assemblies and content files by using the following heuristics:</span></span>

1. <span data-ttu-id="8cde6-205">探查符合套件<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]之屬性的元件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="8cde6-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

2. <span data-ttu-id="8cde6-206">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如果找到<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>屬性, 則套件的路徑會參考內容檔。</span><span class="sxs-lookup"><span data-stu-id="8cde6-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a content file.</span></span>

3. <span data-ttu-id="8cde6-207">如果找<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>不到屬性, 請探查編譯到本機組件中的集合資源檔。</span><span class="sxs-lookup"><span data-stu-id="8cde6-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>

4. <span data-ttu-id="8cde6-208">如果找到符合套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]路徑的資源檔, 則套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]的路徑會參考資源檔。</span><span class="sxs-lookup"><span data-stu-id="8cde6-208">If a resource file that matches the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a resource file.</span></span>

5. <span data-ttu-id="8cde6-209">如果找不到資源, 內部建立<xref:System.Uri>的會是不正確。</span><span class="sxs-lookup"><span data-stu-id="8cde6-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>

[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]<span data-ttu-id="8cde6-210">解決方式不適用[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , 其參考如下:</span><span class="sxs-lookup"><span data-stu-id="8cde6-210">resolution does not apply for [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that refer to the following:</span></span>

- <span data-ttu-id="8cde6-211">參考元件中的內容檔: 不支援[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]這些檔案類型。</span><span class="sxs-lookup"><span data-stu-id="8cde6-211">Content files in referenced assemblies: these file types are not supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>

- <span data-ttu-id="8cde6-212">參考元件中的內嵌檔案[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] : 識別它們是唯一的, 因為它們都包含所參考元件的名稱`;component`和尾碼。</span><span class="sxs-lookup"><span data-stu-id="8cde6-212">Embedded files in referenced assemblies: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>

- <span data-ttu-id="8cde6-213">來源網站檔案: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]識別它們是唯一的, 因為它們是可由包含 siteoforigin:///授權單位的套件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]識別的唯一檔案。</span><span class="sxs-lookup"><span data-stu-id="8cde6-213">Site of origin files: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they are the only files that can be identified by pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that contain the siteoforigin:/// authority.</span></span>

<span data-ttu-id="8cde6-214">封裝[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]解析允許的一項簡化, 是讓程式碼與資源和內容檔案的位置有些獨立。</span><span class="sxs-lookup"><span data-stu-id="8cde6-214">One simplification that pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="8cde6-215">例如, 如果您在本機組件中將資源檔重新設定為內容檔, 則該資源的套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]會維持不變, 如同使用套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]的程式碼一樣。</span><span class="sxs-lookup"><span data-stu-id="8cde6-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the resource remains the same, as does the code that uses the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a><span data-ttu-id="8cde6-216">使用套件 URI 的程式設計</span><span class="sxs-lookup"><span data-stu-id="8cde6-216">Programming with Pack URIs</span></span>

<span data-ttu-id="8cde6-217">許多[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]類別都會執行可使用 pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]設定的屬性, 包括:</span><span class="sxs-lookup"><span data-stu-id="8cde6-217">Many [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implement properties that can be set with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], including:</span></span>

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

<span data-ttu-id="8cde6-218">可以透過標記和程式碼來設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="8cde6-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="8cde6-219">本節示範兩者的基本建構，並顯示常見案例的範例。</span><span class="sxs-lookup"><span data-stu-id="8cde6-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="8cde6-220">透過標記使用套件 URI</span><span class="sxs-lookup"><span data-stu-id="8cde6-220">Using Pack URIs in Markup</span></span>

<span data-ttu-id="8cde6-221">在標記[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]中指定套件時, 會將屬性的元素設定為套件。 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cde6-221">A pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is specified in markup by setting the element of an attribute with the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="8cde6-222">例如：</span><span class="sxs-lookup"><span data-stu-id="8cde6-222">For example:</span></span>

`<element attribute="pack://application:,,,/File.xaml" />`

<span data-ttu-id="8cde6-223">[表 1] 說明您可以[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]在標記中指定的各種絕對套件。</span><span class="sxs-lookup"><span data-stu-id="8cde6-223">Table 1 illustrates the various absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>

<span data-ttu-id="8cde6-224">表 1:標記中的絕對套件 Uri</span><span class="sxs-lookup"><span data-stu-id="8cde6-224">Table 1: Absolute Pack URIs in Markup</span></span>

|<span data-ttu-id="8cde6-225">檔案</span><span class="sxs-lookup"><span data-stu-id="8cde6-225">File</span></span>|<span data-ttu-id="8cde6-226">絕對套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cde6-226">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="8cde6-227">資源檔 - 本機組件</span><span class="sxs-lookup"><span data-stu-id="8cde6-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|
|<span data-ttu-id="8cde6-228">子資料夾中的資源檔 - 本機組件</span><span class="sxs-lookup"><span data-stu-id="8cde6-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="8cde6-229">資源檔 - 參考組件</span><span class="sxs-lookup"><span data-stu-id="8cde6-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="8cde6-230">參考組件之子資料夾中的資源檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="8cde6-231">版本化參考組件中的資源檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|<span data-ttu-id="8cde6-232">內容檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|
|<span data-ttu-id="8cde6-233">子資料夾中的內容檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|<span data-ttu-id="8cde6-234">來源網站檔案</span><span class="sxs-lookup"><span data-stu-id="8cde6-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|<span data-ttu-id="8cde6-235">子資料夾中的來源網站檔案</span><span class="sxs-lookup"><span data-stu-id="8cde6-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

<span data-ttu-id="8cde6-236">[表 2] 說明您可以[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]在標記中指定的各種相對套件。</span><span class="sxs-lookup"><span data-stu-id="8cde6-236">Table 2 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>

<span data-ttu-id="8cde6-237">表 2:標記中的相對套件 Uri</span><span class="sxs-lookup"><span data-stu-id="8cde6-237">Table 2: Relative Pack URIs in Markup</span></span>

|<span data-ttu-id="8cde6-238">檔案</span><span class="sxs-lookup"><span data-stu-id="8cde6-238">File</span></span>|<span data-ttu-id="8cde6-239">相對套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cde6-239">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="8cde6-240">本機組件中的資源檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|
|<span data-ttu-id="8cde6-241">本機組件子資料夾中的資源檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="8cde6-242">參考組件中的資源檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|<span data-ttu-id="8cde6-243">參考組件之子資料夾中的資源檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|<span data-ttu-id="8cde6-244">內容檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-244">Content file</span></span>|`"/ContentFile.xaml"`|
|<span data-ttu-id="8cde6-245">子資料夾中的內容檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a><span data-ttu-id="8cde6-246">透過程式碼使用套件 URI</span><span class="sxs-lookup"><span data-stu-id="8cde6-246">Using Pack URIs in Code</span></span>

<span data-ttu-id="8cde6-247">您可以藉由[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]具現<xref:System.Uri>化類別, 並將套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]當做參數傳遞至函式, 以在程式碼中指定套件。</span><span class="sxs-lookup"><span data-stu-id="8cde6-247">You specify a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] in code by instantiating the <xref:System.Uri> class and passing the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] as a parameter to the constructor.</span></span> <span data-ttu-id="8cde6-248">這點在下列範例中示範。</span><span class="sxs-lookup"><span data-stu-id="8cde6-248">This is demonstrated in the following example.</span></span>

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

<span data-ttu-id="8cde6-249">根據預設, <xref:System.Uri>類別會將 pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]視為絕對。</span><span class="sxs-lookup"><span data-stu-id="8cde6-249">By default, the <xref:System.Uri> class considers pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to be absolute.</span></span> <span data-ttu-id="8cde6-250">因此, 當使用相對套件<xref:System.Uri> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]建立類別的實例時, 就會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8cde6-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>

```csharp
Uri uri = new Uri("/File.xaml");
```

<span data-ttu-id="8cde6-251">幸運的是<xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> , <xref:System.Uri>類別函式的多載會接受型<xref:System.UriKind>別為的參數, 讓您指定[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]套件為絕對或相對的。</span><span class="sxs-lookup"><span data-stu-id="8cde6-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is either absolute or relative.</span></span>

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

<span data-ttu-id="8cde6-252">只有在您確定<xref:System.UriKind.Absolute>提供<xref:System.UriKind.Relative>的套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]是其中一種時, 才應該指定或。</span><span class="sxs-lookup"><span data-stu-id="8cde6-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is one or the other.</span></span> <span data-ttu-id="8cde6-253">如果您不知道所使用的套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]類型, 例如當使用者<xref:System.UriKind.RelativeOrAbsolute>在執行時間輸入套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]時, 請改用。</span><span class="sxs-lookup"><span data-stu-id="8cde6-253">If you don't know the type of pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that is used, such as when a user enters a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

<span data-ttu-id="8cde6-254">[表 3] 說明您可以[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]在程式碼中使用<xref:System.Uri?displayProperty=nameWithType>指定的各種相對套件。</span><span class="sxs-lookup"><span data-stu-id="8cde6-254">Table 3 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="8cde6-255">表 3:程式碼中的絕對套件 Uri</span><span class="sxs-lookup"><span data-stu-id="8cde6-255">Table 3: Absolute Pack URIs in Code</span></span>

|<span data-ttu-id="8cde6-256">檔案</span><span class="sxs-lookup"><span data-stu-id="8cde6-256">File</span></span>|<span data-ttu-id="8cde6-257">絕對套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cde6-257">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="8cde6-258">資源檔 - 本機組件</span><span class="sxs-lookup"><span data-stu-id="8cde6-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="8cde6-259">子資料夾中的資源檔 - 本機組件</span><span class="sxs-lookup"><span data-stu-id="8cde6-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="8cde6-260">資源檔 - 參考組件</span><span class="sxs-lookup"><span data-stu-id="8cde6-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="8cde6-261">參考組件之子資料夾中的資源檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="8cde6-262">版本化參考組件中的資源檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="8cde6-263">內容檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="8cde6-264">子資料夾中的內容檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="8cde6-265">來源網站檔案</span><span class="sxs-lookup"><span data-stu-id="8cde6-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|<span data-ttu-id="8cde6-266">子資料夾中的來源網站檔案</span><span class="sxs-lookup"><span data-stu-id="8cde6-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

<span data-ttu-id="8cde6-267">[表 4] 說明您可以[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]在程式碼中使用<xref:System.Uri?displayProperty=nameWithType>指定的各種相對套件。</span><span class="sxs-lookup"><span data-stu-id="8cde6-267">Table 4 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="8cde6-268">表 4:程式碼中的相對套件 Uri</span><span class="sxs-lookup"><span data-stu-id="8cde6-268">Table 4: Relative Pack URIs in Code</span></span>

|<span data-ttu-id="8cde6-269">檔案</span><span class="sxs-lookup"><span data-stu-id="8cde6-269">File</span></span>|<span data-ttu-id="8cde6-270">相對套件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cde6-270">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="8cde6-271">資源檔 - 本機組件</span><span class="sxs-lookup"><span data-stu-id="8cde6-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="8cde6-272">子資料夾中的資源檔 - 本機組件</span><span class="sxs-lookup"><span data-stu-id="8cde6-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="8cde6-273">資源檔 - 參考組件</span><span class="sxs-lookup"><span data-stu-id="8cde6-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="8cde6-274">子資料夾中的資源檔 - 參考組件</span><span class="sxs-lookup"><span data-stu-id="8cde6-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="8cde6-275">內容檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|<span data-ttu-id="8cde6-276">子資料夾中的內容檔</span><span class="sxs-lookup"><span data-stu-id="8cde6-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="8cde6-277">常見套件 URI 案例</span><span class="sxs-lookup"><span data-stu-id="8cde6-277">Common Pack URI Scenarios</span></span>

<span data-ttu-id="8cde6-278">前面幾節已討論如何建立套件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] , 以識別資源、內容和來源網站檔案。</span><span class="sxs-lookup"><span data-stu-id="8cde6-278">The preceding sections have discussed how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="8cde6-279">在[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]中, 這些結構會以各種不同的方式使用, 而下列各節將涵蓋數個常見的用法。</span><span class="sxs-lookup"><span data-stu-id="8cde6-279">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="8cde6-280">指定要在啟動應用程式時顯示的 UI</span><span class="sxs-lookup"><span data-stu-id="8cde6-280">Specifying the UI to Show When an Application Starts</span></span>

<span data-ttu-id="8cde6-281"><xref:System.Windows.Application.StartupUri%2A>指定啟動[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]應用[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]程式時要顯示的第一個。</span><span class="sxs-lookup"><span data-stu-id="8cde6-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application is launched.</span></span> <span data-ttu-id="8cde6-282">若是獨立應用程式, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]可以是視窗, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8cde6-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

<span data-ttu-id="8cde6-283">獨立應用程式[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]也可以指定頁面做為初始 UI, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8cde6-283">Standalone applications and [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] can also specify a page as the initial UI, as shown in the following example.</span></span>

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

<span data-ttu-id="8cde6-284">如果應用程式是獨立應用程式, 而且已使用<xref:System.Windows.Application.StartupUri%2A>指定頁面, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]則會開啟<xref:System.Windows.Navigation.NavigationWindow>來裝載頁面。</span><span class="sxs-lookup"><span data-stu-id="8cde6-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="8cde6-285">若[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]為, 則頁面會顯示在主機瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="8cde6-285">For [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], the page is shown in the host browser.</span></span>

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a><span data-ttu-id="8cde6-286">巡覽至頁面</span><span class="sxs-lookup"><span data-stu-id="8cde6-286">Navigating to a Page</span></span>

<span data-ttu-id="8cde6-287">下列範例示範如何巡覽至頁面。</span><span class="sxs-lookup"><span data-stu-id="8cde6-287">The following example shows how to navigate to a page.</span></span>

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

<span data-ttu-id="8cde6-288">如需各種流覽[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]方式的詳細資訊, 請參閱[導覽總覽](navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="8cde6-288">For more information on the various ways to navigate in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Navigation Overview](navigation-overview.md).</span></span>

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a><span data-ttu-id="8cde6-289">指定視窗圖示</span><span class="sxs-lookup"><span data-stu-id="8cde6-289">Specifying a Window Icon</span></span>

<span data-ttu-id="8cde6-290">下列範例示範如何使用 URI 來指定視窗的圖示。</span><span class="sxs-lookup"><span data-stu-id="8cde6-290">The following example shows how to use a URI to specify a window's icon.</span></span>

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

<span data-ttu-id="8cde6-291">如需詳細資訊，請參閱 <xref:System.Windows.Window.Icon%2A>。</span><span class="sxs-lookup"><span data-stu-id="8cde6-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="8cde6-292">載入影像、音訊和視訊檔案</span><span class="sxs-lookup"><span data-stu-id="8cde6-292">Loading Image, Audio, and Video Files</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="8cde6-293">可讓應用程式使用各種不同的媒體類型, 其中全部都可以使用套件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]來識別及載入, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8cde6-293">allows applications to use a wide variety of media types, all of which can be identified and loaded with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], as shown in the following examples.</span></span>

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

<span data-ttu-id="8cde6-294">如需使用媒體內容的詳細資訊, 請參閱[圖形和多媒體](../graphics-multimedia/index.md)。</span><span class="sxs-lookup"><span data-stu-id="8cde6-294">For more information on working with media content, see [Graphics and Multimedia](../graphics-multimedia/index.md).</span></span>

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="8cde6-295">從來源網站載入資源字典</span><span class="sxs-lookup"><span data-stu-id="8cde6-295">Loading a Resource Dictionary from the Site of Origin</span></span>

<span data-ttu-id="8cde6-296">資源字典 (<xref:System.Windows.ResourceDictionary>) 可以用來支援應用程式主題。</span><span class="sxs-lookup"><span data-stu-id="8cde6-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="8cde6-297">建立和管理主題的一種方法是將多個主題建立為位在應用程式來源網站的資源字典。</span><span class="sxs-lookup"><span data-stu-id="8cde6-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="8cde6-298">這樣可新增和更新主題，而不需要重新編譯和重新部署應用程式的。</span><span class="sxs-lookup"><span data-stu-id="8cde6-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="8cde6-299">您可以使用套件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]來識別和載入這些資源字典, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="8cde6-299">These resource dictionaries can be identified and loaded using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], which is shown in the following example.</span></span>

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

<span data-ttu-id="8cde6-300">如需主題[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]的總覽, 請參閱設定[樣式和範本](../controls/styling-and-templating.md)。</span><span class="sxs-lookup"><span data-stu-id="8cde6-300">For an overview of themes in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Styling and Templating](../controls/styling-and-templating.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8cde6-301">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cde6-301">See also</span></span>

- [<span data-ttu-id="8cde6-302">WPF 應用程式資源、內容和資料檔案</span><span class="sxs-lookup"><span data-stu-id="8cde6-302">WPF Application Resource, Content, and Data Files</span></span>](wpf-application-resource-content-and-data-files.md)
