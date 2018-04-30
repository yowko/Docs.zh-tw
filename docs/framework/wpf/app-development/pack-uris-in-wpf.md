---
title: WPF 中的 Pack URI
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
caps.latest.revision: 35
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d90345f6c6e44bfdd98d2a1313a36372cdfe8b06
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="pack-uris-in-wpf"></a><span data-ttu-id="b02fe-102">WPF 中的 Pack URI</span><span class="sxs-lookup"><span data-stu-id="b02fe-102">Pack URIs in WPF</span></span>
<span data-ttu-id="b02fe-103">在 Windows Presentation Foundation (WPF)，[!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]用來識別及載入檔案，在許多方面，包括下列：</span><span class="sxs-lookup"><span data-stu-id="b02fe-103">In Windows Presentation Foundation (WPF), [!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] are used to identify and load files in many ways, including the following:</span></span>  
  
-   <span data-ttu-id="b02fe-104">指定[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]以顯示應用程式第一次啟動時。</span><span class="sxs-lookup"><span data-stu-id="b02fe-104">Specifying the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] to show when an application first starts.</span></span>  
  
-   <span data-ttu-id="b02fe-105">載入影像。</span><span class="sxs-lookup"><span data-stu-id="b02fe-105">Loading images.</span></span>  
  
-   <span data-ttu-id="b02fe-106">巡覽至頁面。</span><span class="sxs-lookup"><span data-stu-id="b02fe-106">Navigating to pages.</span></span>  
  
-   <span data-ttu-id="b02fe-107">載入不可執行的資料檔案。</span><span class="sxs-lookup"><span data-stu-id="b02fe-107">Loading non-executable data files.</span></span>  
  
 <span data-ttu-id="b02fe-108">此外，[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]可用來識別及載入檔案，從各種不同的位置，包括下列：</span><span class="sxs-lookup"><span data-stu-id="b02fe-108">Furthermore, [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] can be used to identify and load files from a variety of locations, including the following:</span></span>  
  
-   <span data-ttu-id="b02fe-109">目前的組件。</span><span class="sxs-lookup"><span data-stu-id="b02fe-109">The current assembly.</span></span>  
  
-   <span data-ttu-id="b02fe-110">所參考的組件。</span><span class="sxs-lookup"><span data-stu-id="b02fe-110">A referenced assembly.</span></span>  
  
-   <span data-ttu-id="b02fe-111">與組件相對的位置。</span><span class="sxs-lookup"><span data-stu-id="b02fe-111">A location relative to an assembly.</span></span>  
  
-   <span data-ttu-id="b02fe-112">應用程式的來源網站。</span><span class="sxs-lookup"><span data-stu-id="b02fe-112">The application's site of origin.</span></span>  
  
 <span data-ttu-id="b02fe-113">若要提供一致的機制來識別並從這些位置載入這些檔案類型[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]運用的擴充性*pack URI 配置*。</span><span class="sxs-lookup"><span data-stu-id="b02fe-113">To provide a consistent mechanism for identifying and loading these types of files from these locations, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] leverages the extensibility of the *pack URI scheme*.</span></span> <span data-ttu-id="b02fe-114">本主題提供配置的概觀，說明如何建構組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]各種情況中，討論 absolute 和 relative[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]和[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]解析度，顯示如何使用組件之前[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]從這兩個標記與程式碼。</span><span class="sxs-lookup"><span data-stu-id="b02fe-114">This topic provides an overview of the scheme, covers how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for a variety of scenarios, discusses absolute and relative [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] and [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution, before showing how to use pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] from both markup and code.</span></span>  
  
  
<a name="The_Pack_URI_Scheme"></a>   
## <a name="the-pack-uri-scheme"></a><span data-ttu-id="b02fe-115">套件 URI 配置</span><span class="sxs-lookup"><span data-stu-id="b02fe-115">The Pack URI Scheme</span></span>  
 <span data-ttu-id="b02fe-116">組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]使用配置[開放式封裝慣例](http://go.microsoft.com/fwlink/?LinkID=71255)(OPC) 規格，其中描述來組織及識別內容的模型。</span><span class="sxs-lookup"><span data-stu-id="b02fe-116">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme is used by the [Open Packaging Conventions](http://go.microsoft.com/fwlink/?LinkID=71255) (OPC) specification, which describes a model for organizing and identifying content.</span></span> <span data-ttu-id="b02fe-117">索引鍵的項目，此模型會封裝和組件，其中*封裝*是邏輯的容器，其中一個或多個邏輯*部分*。</span><span class="sxs-lookup"><span data-stu-id="b02fe-117">The key elements of this model are packages and parts, where a *package* is a logical container for one or more logical *parts*.</span></span> <span data-ttu-id="b02fe-118">下圖說明這個概念。</span><span class="sxs-lookup"><span data-stu-id="b02fe-118">The following figure illustrates this concept.</span></span>  
  
 <span data-ttu-id="b02fe-119">![套件和組件圖表](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")</span><span class="sxs-lookup"><span data-stu-id="b02fe-119">![Package and Parts diagram](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")</span></span>  
  
 <span data-ttu-id="b02fe-120">若要識別組件，OPC 規格會利用 RFC 2396 的擴充性 (統一資源識別項 (URI): 一般語法) 來定義組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]配置。</span><span class="sxs-lookup"><span data-stu-id="b02fe-120">To identify parts, the OPC specification leverages the extensibility of RFC 2396 (Uniform Resource Identifiers (URI): Generic Syntax) to define the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme.</span></span>  
  
 <span data-ttu-id="b02fe-121">所指定的配置[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]定義其前置詞，由 http、 ftp 和檔案是已知的範例。</span><span class="sxs-lookup"><span data-stu-id="b02fe-121">The scheme that is specified by a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is defined by its prefix; http, ftp, and file are well-known examples.</span></span> <span data-ttu-id="b02fe-122">組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]配置做為其配置中，使用 「 組件 」，以及包含兩個元件： 授權和路徑。</span><span class="sxs-lookup"><span data-stu-id="b02fe-122">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme uses "pack" as its scheme, and contains two components: authority and path.</span></span> <span data-ttu-id="b02fe-123">以下是組件的格式[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b02fe-123">The following is the format for a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 <span data-ttu-id="b02fe-124">組件: / /*授權*/*路徑*</span><span class="sxs-lookup"><span data-stu-id="b02fe-124">pack://*authority*/*path*</span></span>
  
 <span data-ttu-id="b02fe-125">*授權*指定封裝的一部分，所包含的型別時*路徑*指定組件在封裝內的位置。</span><span class="sxs-lookup"><span data-stu-id="b02fe-125">The *authority* specifies the type of package that a part is contained by, while the *path* specifies the location of a part within a package.</span></span>  
  
 <span data-ttu-id="b02fe-126">下圖說明這個概念︰</span><span class="sxs-lookup"><span data-stu-id="b02fe-126">This concept is illustrated by the following figure:</span></span>  
  
 <span data-ttu-id="b02fe-127">![套件、授權和路徑之間的關聯性](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")</span><span class="sxs-lookup"><span data-stu-id="b02fe-127">![Relationship among package, authority, and path](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")</span></span>  
  
 <span data-ttu-id="b02fe-128">套件和組件與應用程式和檔案類似，其中應用程式 (套件) 可以包括一或多個檔案 (組件)，包括︰</span><span class="sxs-lookup"><span data-stu-id="b02fe-128">Packages and parts are analogous to applications and files, where an application (package) can include one or more files (parts), including:</span></span>  
  
-   <span data-ttu-id="b02fe-129">編譯為本機組件的資源檔。</span><span class="sxs-lookup"><span data-stu-id="b02fe-129">Resource files that are compiled into the local assembly.</span></span>  
  
-   <span data-ttu-id="b02fe-130">編譯為所參考組件的資源檔。</span><span class="sxs-lookup"><span data-stu-id="b02fe-130">Resource files that are compiled into a referenced assembly.</span></span>  
  
-   <span data-ttu-id="b02fe-131">編譯為參考組件的資源檔。</span><span class="sxs-lookup"><span data-stu-id="b02fe-131">Resource files that are compiled into a referencing assembly.</span></span>  
  
-   <span data-ttu-id="b02fe-132">內容檔。</span><span class="sxs-lookup"><span data-stu-id="b02fe-132">Content files.</span></span>  
  
-   <span data-ttu-id="b02fe-133">來源網站檔案。</span><span class="sxs-lookup"><span data-stu-id="b02fe-133">Site of origin files.</span></span>  
  
 <span data-ttu-id="b02fe-134">若要存取這些類型的檔案，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]支援兩個授權單位： 應用程式: / / 和 siteoforigin: / /。</span><span class="sxs-lookup"><span data-stu-id="b02fe-134">To access these types of files, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] supports two authorities: application:/// and siteoforigin:///.</span></span> <span data-ttu-id="b02fe-135">application:/// 授權識別在編譯時期已知的應用程式資料檔，包括資源檔和內容檔。</span><span class="sxs-lookup"><span data-stu-id="b02fe-135">The application:/// authority identifies application data files that are known at compile time, including resource and content files.</span></span> <span data-ttu-id="b02fe-136">siteoforigin:/// 授權識別來源網站檔案。</span><span class="sxs-lookup"><span data-stu-id="b02fe-136">The siteoforigin:/// authority identifies site of origin files.</span></span> <span data-ttu-id="b02fe-137">下圖顯示每個授權的範圍。</span><span class="sxs-lookup"><span data-stu-id="b02fe-137">The scope of each authority is shown in the following figure.</span></span>  
  
 <span data-ttu-id="b02fe-138">![套件 URI 圖表](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")</span><span class="sxs-lookup"><span data-stu-id="b02fe-138">![Pack URI diagram](../../../../docs/framework/wpf/app-development/media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b02fe-139">組件的授權元件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]是內嵌[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]，指向封裝，而且必須符合 RFC 2396。</span><span class="sxs-lookup"><span data-stu-id="b02fe-139">The authority component of a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is an embedded [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that points to a package and must conform to RFC 2396.</span></span> <span data-ttu-id="b02fe-140">此外，"/" 字元必須取代為 "," 字元，而且必須逸出 "%" 和 "?" 這類保留字元。</span><span class="sxs-lookup"><span data-stu-id="b02fe-140">Additionally, the "/" character must be replaced with the "," character, and reserved characters such as "%" and "?" must be escaped.</span></span> <span data-ttu-id="b02fe-141">如需詳細資料，請參閱 OPC。</span><span class="sxs-lookup"><span data-stu-id="b02fe-141">See the OPC for details.</span></span>  
  
 <span data-ttu-id="b02fe-142">下列各節將說明如何建構組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]識別資源、 內容和來源網站檔搭配適當的路徑中使用這些兩個授權單位。</span><span class="sxs-lookup"><span data-stu-id="b02fe-142">The following sections explain how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] using these two authorities in conjunction with the appropriate paths for identifying resource, content, and site of origin files.</span></span>  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## <a name="resource-file-pack-uris"></a><span data-ttu-id="b02fe-143">資源檔套件 URI</span><span class="sxs-lookup"><span data-stu-id="b02fe-143">Resource File Pack URIs</span></span>  
 <span data-ttu-id="b02fe-144">資源檔會設定為[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Resource`項目，並編譯成組件。</span><span class="sxs-lookup"><span data-stu-id="b02fe-144">Resource files are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Resource` items and are compiled into assemblies.</span></span> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="b02fe-145"> 支援的組件建構[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，可以用來識別資源檔編譯為本機的組件或編譯的組件參考的本機組件。</span><span class="sxs-lookup"><span data-stu-id="b02fe-145"> supports the construction of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that can be used to identify resource files that are either compiled into the local assembly or compiled into an assembly that is referenced from the local assembly.</span></span>  
  
<a name="Local_Assembly_Resource_File"></a>   
### <a name="local-assembly-resource-file"></a><span data-ttu-id="b02fe-146">本機組件資源檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-146">Local Assembly Resource File</span></span>  
 <span data-ttu-id="b02fe-147">組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]資源編譯成本機組件的檔案會使用下列的授權和路徑：</span><span class="sxs-lookup"><span data-stu-id="b02fe-147">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into the local assembly uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="b02fe-148">**授權**：application:///。</span><span class="sxs-lookup"><span data-stu-id="b02fe-148">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="b02fe-149">**路徑**︰相對於本機組件專案資料夾根之資源檔的名稱，包括其路徑。</span><span class="sxs-lookup"><span data-stu-id="b02fe-149">**Path**: The name of the resource file, including its path, relative to the local assembly project folder root.</span></span>  
  
 <span data-ttu-id="b02fe-150">下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]位於本機的組件的專案資料夾的根目錄中的資源檔。</span><span class="sxs-lookup"><span data-stu-id="b02fe-150">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the local assembly's project folder.</span></span>  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 <span data-ttu-id="b02fe-151">下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]位於本機的組件的專案資料夾的子資料夾中的資源檔。</span><span class="sxs-lookup"><span data-stu-id="b02fe-151">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the local assembly's project folder.</span></span>  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### <a name="referenced-assembly-resource-file"></a><span data-ttu-id="b02fe-152">所參考的組件資源檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-152">Referenced Assembly Resource File</span></span>  
 <span data-ttu-id="b02fe-153">組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]資源編譯成參考的組件的檔案會使用下列的授權和路徑：</span><span class="sxs-lookup"><span data-stu-id="b02fe-153">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file that is compiled into a referenced assembly uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="b02fe-154">**授權**：application:///。</span><span class="sxs-lookup"><span data-stu-id="b02fe-154">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="b02fe-155">**路徑**：編譯為所參考組件之資源檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="b02fe-155">**Path**: The name of a resource file that is compiled into a referenced assembly.</span></span> <span data-ttu-id="b02fe-156">路徑必須符合下列格式：</span><span class="sxs-lookup"><span data-stu-id="b02fe-156">The path must conform to the following format:</span></span>  
  
     <span data-ttu-id="b02fe-157">*AssemblyShortName*{*;版本*] {*;PublicKey*]; component /*路徑*</span><span class="sxs-lookup"><span data-stu-id="b02fe-157">*AssemblyShortName*{*;Version*]{*;PublicKey*];component/*Path*</span></span>  
  
    -   <span data-ttu-id="b02fe-158">**AssemblyShortName**：所參考組件的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="b02fe-158">**AssemblyShortName**: the short name for the referenced assembly.</span></span>  
  
    -   <span data-ttu-id="b02fe-159">**;Version** [選擇性]：包含資源檔之參考組件的版本。</span><span class="sxs-lookup"><span data-stu-id="b02fe-159">**;Version** [optional]: the version of the referenced assembly that contains the resource file.</span></span> <span data-ttu-id="b02fe-160">這是在載入具有相同簡短名稱的兩個以上參考組件時使用。</span><span class="sxs-lookup"><span data-stu-id="b02fe-160">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>  
  
    -   <span data-ttu-id="b02fe-161">**;PublicKey** [選擇性]：用來簽署參考組件的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="b02fe-161">**;PublicKey** [optional]: the public key that was used to sign the referenced assembly.</span></span> <span data-ttu-id="b02fe-162">這是在載入具有相同簡短名稱的兩個以上參考組件時使用。</span><span class="sxs-lookup"><span data-stu-id="b02fe-162">This is used when two or more referenced assemblies with the same short name are loaded.</span></span>  
  
    -   <span data-ttu-id="b02fe-163">**;component**︰指定從本機組件參考所參考的組件。</span><span class="sxs-lookup"><span data-stu-id="b02fe-163">**;component**: specifies that the assembly being referred to is referenced from the local assembly.</span></span>  
  
    -   <span data-ttu-id="b02fe-164">**/Path**︰相對於所參考組件專案資料夾根之資源檔的名稱，包括其路徑。</span><span class="sxs-lookup"><span data-stu-id="b02fe-164">**/Path**: the name of the resource file, including its path, relative to the root of the referenced assembly's project folder.</span></span>  
  
 <span data-ttu-id="b02fe-165">下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]位於參考組件的專案資料夾的根目錄中的資源檔。</span><span class="sxs-lookup"><span data-stu-id="b02fe-165">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root of the referenced assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 <span data-ttu-id="b02fe-166">下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]位於參考組件的專案資料夾的子資料夾中的資源檔。</span><span class="sxs-lookup"><span data-stu-id="b02fe-166">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in a subfolder of the referenced assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 <span data-ttu-id="b02fe-167">下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]位於根資料夾的參考、 版本特定組件的專案資料夾中的資源檔。</span><span class="sxs-lookup"><span data-stu-id="b02fe-167">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] resource file that is located in the root folder of a referenced, version-specific assembly's project folder.</span></span>  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 <span data-ttu-id="b02fe-168">請注意，此組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考的組件資源檔案的語法只能搭配應用程式: / / 授權。</span><span class="sxs-lookup"><span data-stu-id="b02fe-168">Note that the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] syntax for referenced assembly resource files can be used only with the application:/// authority.</span></span> <span data-ttu-id="b02fe-169">例如，下列不支援[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b02fe-169">For example, the following is not supported in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## <a name="content-file-pack-uris"></a><span data-ttu-id="b02fe-170">內容檔套件 URI</span><span class="sxs-lookup"><span data-stu-id="b02fe-170">Content File Pack URIs</span></span>  
 <span data-ttu-id="b02fe-171">組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]內容檔案所使用的下列授權和路徑：</span><span class="sxs-lookup"><span data-stu-id="b02fe-171">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a content file uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="b02fe-172">**授權**：application:///。</span><span class="sxs-lookup"><span data-stu-id="b02fe-172">**Authority**: application:///.</span></span>  
  
-   <span data-ttu-id="b02fe-173">**路徑**：內容檔的名稱，包括其相對於應用程式主要可執行組件之檔案系統位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="b02fe-173">**Path**: The name of the content file, including its path relative to the file system location of the application's main executable assembly.</span></span>  
  
 <span data-ttu-id="b02fe-174">下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]位於與可執行的組件相同的資料夾中的內容檔案。</span><span class="sxs-lookup"><span data-stu-id="b02fe-174">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in the same folder as the executable assembly.</span></span>  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 <span data-ttu-id="b02fe-175">下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]位於相對於應用程式的可執行組件的子資料夾的內容檔案。</span><span class="sxs-lookup"><span data-stu-id="b02fe-175">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] content file, located in a subfolder that is relative to the application's executable assembly.</span></span>  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  <span data-ttu-id="b02fe-176">無法巡覽至 [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] 內容檔。</span><span class="sxs-lookup"><span data-stu-id="b02fe-176">[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] content files cannot be navigated to.</span></span> <span data-ttu-id="b02fe-177">[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]配置僅支援巡覽至[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]位於來源的站台上的檔案。</span><span class="sxs-lookup"><span data-stu-id="b02fe-177">The [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] scheme only supports navigation to [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] files that are located at the site of origin.</span></span>  
  
<a name="The_siteoforigin_____Authority"></a>   
## <a name="site-of-origin-pack-uris"></a><span data-ttu-id="b02fe-178">來源網站套件 URI</span><span class="sxs-lookup"><span data-stu-id="b02fe-178">Site of Origin Pack URIs</span></span>  
 <span data-ttu-id="b02fe-179">組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]的來源站台的檔案會使用下列的授權和路徑：</span><span class="sxs-lookup"><span data-stu-id="b02fe-179">The pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a site of origin file uses the following authority and path:</span></span>  
  
-   <span data-ttu-id="b02fe-180">**授權**：siteoforigin:///。</span><span class="sxs-lookup"><span data-stu-id="b02fe-180">**Authority**: siteoforigin:///.</span></span>  
  
-   <span data-ttu-id="b02fe-181">**路徑**：來源網站檔案的名稱，包括其相對於從中啟動可執行組件之位置的路徑。</span><span class="sxs-lookup"><span data-stu-id="b02fe-181">**Path**: The name of the site of origin file, including its path relative to the location from which the executable assembly was launched.</span></span>  
  
 <span data-ttu-id="b02fe-182">下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]站台的來源檔案，儲存在從中啟動可執行的組件的位置。</span><span class="sxs-lookup"><span data-stu-id="b02fe-182">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in the location from which the executable assembly is launched.</span></span>  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 <span data-ttu-id="b02fe-183">下列範例顯示的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]如[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]站台的來源檔案，儲存在啟動應用程式的可執行組件時的位置相對的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="b02fe-183">The following example shows the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] site of origin file, stored in subfolder that is relative to the location from which the application's executable assembly is launched.</span></span>  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## <a name="page-files"></a><span data-ttu-id="b02fe-184">分頁檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-184">Page Files</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="b02fe-185"> 設定為檔案[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page`項目做為資源檔相同的方式，會編譯成組件。</span><span class="sxs-lookup"><span data-stu-id="b02fe-185"> files that are configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items are compiled into assemblies in the same way as resource files.</span></span> <span data-ttu-id="b02fe-186">因此， [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page`項目可以使用組件識別[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]資源檔。</span><span class="sxs-lookup"><span data-stu-id="b02fe-186">Consequently, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items can be identified using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files.</span></span>  
  
 <span data-ttu-id="b02fe-187">類型的[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]檔案通常會設定為[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page`項目具有下列項目當做其根元素的其中一個：</span><span class="sxs-lookup"><span data-stu-id="b02fe-187">The types of [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files that are commonly configured as [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page` items have one of the following as their root element:</span></span>  
  
-   <xref:System.Windows.Window?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## <a name="absolute-vs-relative-pack-uris"></a><span data-ttu-id="b02fe-188">絕對與相對套件 URI</span><span class="sxs-lookup"><span data-stu-id="b02fe-188">Absolute vs. Relative Pack URIs</span></span>  
 <span data-ttu-id="b02fe-189">完整的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]包含配置、 授權和路徑，且其被視為絕對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b02fe-189">A fully qualified pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] includes the scheme, the authority, and the path, and it is considered an absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="b02fe-190">為開發人員簡化[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]項目通常可讓您設定適當的屬性與相對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]，其中包括只有路徑。</span><span class="sxs-lookup"><span data-stu-id="b02fe-190">As a simplification for developers, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements typically allow you to set appropriate attributes with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)], which includes only the path.</span></span>  
  
 <span data-ttu-id="b02fe-191">例如，請考慮下列絕對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]本機的組件中的資源檔。</span><span class="sxs-lookup"><span data-stu-id="b02fe-191">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for a resource file in the local assembly.</span></span>  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 <span data-ttu-id="b02fe-192">相對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考這個資源檔會是如下所示。</span><span class="sxs-lookup"><span data-stu-id="b02fe-192">The relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that refers to this resource file would be the following.</span></span>  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  <span data-ttu-id="b02fe-193">因為站台的來源檔案不是組件相關聯，可以只參考這些絕對 pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b02fe-193">Because site of origin files are not associated with assemblies, they can only be referred to with absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)].</span></span>  
  
 <span data-ttu-id="b02fe-194">根據預設，相對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]會被視為相對於包含參考的程式碼之標記的位置。</span><span class="sxs-lookup"><span data-stu-id="b02fe-194">By default, a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is considered relative to the location of the markup or code that contains the reference.</span></span> <span data-ttu-id="b02fe-195">如果使用前置反斜線，不過，相對於組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考則視為相對於應用程式的根目錄。</span><span class="sxs-lookup"><span data-stu-id="b02fe-195">If a leading backslash is used, however, the relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] reference is then considered relative to the root of the application.</span></span> <span data-ttu-id="b02fe-196">例如，請考慮下列專案結構。</span><span class="sxs-lookup"><span data-stu-id="b02fe-196">For example, consider the following project structure.</span></span>  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 <span data-ttu-id="b02fe-197">如果包含 Page1.xaml[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考*根*\SubFolder\Page2.xaml，參考可以使用下列相對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b02fe-197">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\SubFolder\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `Page2.xaml`  
  
 <span data-ttu-id="b02fe-198">如果包含 Page1.xaml[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]參考*根*\Page2.xaml，參考可以使用下列相對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b02fe-198">If Page1.xaml contains a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that references *Root*\Page2.xaml, the reference can use the following relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## <a name="pack-uri-resolution"></a><span data-ttu-id="b02fe-199">套件 URI 解析</span><span class="sxs-lookup"><span data-stu-id="b02fe-199">Pack URI Resolution</span></span>  
 <span data-ttu-id="b02fe-200">組件的格式[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]組件可能會讓[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]不同類型的檔案相同的外觀。</span><span class="sxs-lookup"><span data-stu-id="b02fe-200">The format of pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] makes it is possible for pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for different types of files to look the same.</span></span> <span data-ttu-id="b02fe-201">例如，請考慮下列絕對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b02fe-201">For example, consider the following absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 <span data-ttu-id="b02fe-202">此絕對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]無法參考本機的組件中的資源檔案或內容檔案。</span><span class="sxs-lookup"><span data-stu-id="b02fe-202">This absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] could refer to either a resource file in the local assembly or a content file.</span></span> <span data-ttu-id="b02fe-203">也適用於下列相對[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b02fe-203">The same is true for the following relative [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
 `/ResourceOrContentFile.xaml`  
  
 <span data-ttu-id="b02fe-204">若要判斷類型檔案的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]指的是，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]解析[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]本機的組件和使用下列啟發學習法的內容檔案中的資源檔：</span><span class="sxs-lookup"><span data-stu-id="b02fe-204">In order to determine the type of file that a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] resolves [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] for resource files in local assemblies and content files by using the following heuristics:</span></span>  
  
1.  <span data-ttu-id="b02fe-205">探查的組件中繼資料<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>符合組件的屬性[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b02fe-205">Probe the assembly metadata for an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute that matches the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
2.  <span data-ttu-id="b02fe-206">如果<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>發現屬性時，組件的路徑[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]所參考的內容檔案。</span><span class="sxs-lookup"><span data-stu-id="b02fe-206">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a content file.</span></span>  
  
3.  <span data-ttu-id="b02fe-207">如果<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>找不到屬性、 探查組資源檔編譯成本機組件。</span><span class="sxs-lookup"><span data-stu-id="b02fe-207">If the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is not found, probe the set resource files that are compiled into the local assembly.</span></span>  
  
4.  <span data-ttu-id="b02fe-208">如果符合的組件路徑的資源檔案[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]為找到的組件的路徑[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]指的是資源檔。</span><span class="sxs-lookup"><span data-stu-id="b02fe-208">If a resource file that matches the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is found, the path of the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] refers to a resource file.</span></span>  
  
5.  <span data-ttu-id="b02fe-209">如果資源找不到，在內部建立<xref:System.Uri>無效。</span><span class="sxs-lookup"><span data-stu-id="b02fe-209">If the resource is not found, the internally created <xref:System.Uri> is invalid.</span></span>  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]<span data-ttu-id="b02fe-210"> 解析不適用於[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，請參考下列：</span><span class="sxs-lookup"><span data-stu-id="b02fe-210"> resolution does not apply for [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that refer to the following:</span></span>  
  
-   <span data-ttu-id="b02fe-211">內容中參考的組件檔案： 這些檔案類型不支援[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b02fe-211">Content files in referenced assemblies: these file types are not supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span></span>  
  
-   <span data-ttu-id="b02fe-212">參考組件中內嵌檔案： [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] ，識別這些是唯一的因為它們包含參考的組件名稱和`;component`後置詞。</span><span class="sxs-lookup"><span data-stu-id="b02fe-212">Embedded files in referenced assemblies: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they include both the name of the referenced assembly and the `;component` suffix.</span></span>  
  
-   <span data-ttu-id="b02fe-213">站台的來源檔案： [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] ，識別這些是唯一的因為它們是可以由組件的唯一檔案[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]包含 siteoforigin: / / 授權。</span><span class="sxs-lookup"><span data-stu-id="b02fe-213">Site of origin files: [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that identify them are unique because they are the only files that can be identified by pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that contain the siteoforigin:/// authority.</span></span>  
  
 <span data-ttu-id="b02fe-214">組件的一個簡化[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]解析可讓適用於程式碼稍微獨立的資源和內容檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="b02fe-214">One simplification that pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] resolution allows is for code to be somewhat independent of the locations of resource and content files.</span></span> <span data-ttu-id="b02fe-215">例如，如果您有會重新設定為內容檔，將組件的本機組件中的資源檔[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]資源維持不變，如同使用組件的程式碼的[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b02fe-215">For example, if you have a resource file in the local assembly that is reconfigured to be a content file, the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] for the resource remains the same, as does the code that uses the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
<a name="Programming_with_Pack_URIs"></a>   
## <a name="programming-with-pack-uris"></a><span data-ttu-id="b02fe-216">使用套件 URI 的程式設計</span><span class="sxs-lookup"><span data-stu-id="b02fe-216">Programming with Pack URIs</span></span>  
 <span data-ttu-id="b02fe-217">許多[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]類別會實作可設定與組件屬性[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，包括：</span><span class="sxs-lookup"><span data-stu-id="b02fe-217">Many [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] classes implement properties that can be set with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], including:</span></span>  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="b02fe-218">可以透過標記和程式碼來設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="b02fe-218">These properties can be set from both markup and code.</span></span> <span data-ttu-id="b02fe-219">本節示範兩者的基本建構，並顯示常見案例的範例。</span><span class="sxs-lookup"><span data-stu-id="b02fe-219">This section demonstrates the basic constructions for both and then shows examples of common scenarios.</span></span>  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### <a name="using-pack-uris-in-markup"></a><span data-ttu-id="b02fe-220">透過標記使用套件 URI</span><span class="sxs-lookup"><span data-stu-id="b02fe-220">Using Pack URIs in Markup</span></span>  
 <span data-ttu-id="b02fe-221">組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]設定具有組件之屬性的項目，來指定在標記中[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b02fe-221">A pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is specified in markup by setting the element of an attribute with the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span> <span data-ttu-id="b02fe-222">例如: </span><span class="sxs-lookup"><span data-stu-id="b02fe-222">For example:</span></span>  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 <span data-ttu-id="b02fe-223">表 1 說明各種絕對的組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，您可以指定在標記中。</span><span class="sxs-lookup"><span data-stu-id="b02fe-223">Table 1 illustrates the various absolute pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>  
  
 <span data-ttu-id="b02fe-224">表 1：使用標記的絕對套件 URI</span><span class="sxs-lookup"><span data-stu-id="b02fe-224">Table 1: Absolute Pack URIs in Markup</span></span>  
  
|<span data-ttu-id="b02fe-225">檔案</span><span class="sxs-lookup"><span data-stu-id="b02fe-225">File</span></span>|<span data-ttu-id="b02fe-226">絕對的組件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b02fe-226">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="b02fe-227">資源檔 - 本機組件</span><span class="sxs-lookup"><span data-stu-id="b02fe-227">Resource file - local assembly</span></span>|`"pack://application:,,,/ResourceFile.xaml"`|  
|<span data-ttu-id="b02fe-228">子資料夾中的資源檔 - 本機組件</span><span class="sxs-lookup"><span data-stu-id="b02fe-228">Resource file in subfolder - local assembly</span></span>|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="b02fe-229">資源檔 - 參考組件</span><span class="sxs-lookup"><span data-stu-id="b02fe-229">Resource file - referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|  
|<span data-ttu-id="b02fe-230">參考組件之子資料夾中的資源檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-230">Resource file in subfolder of referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="b02fe-231">版本化參考組件中的資源檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-231">Resource file in versioned referenced assembly</span></span>|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|  
|<span data-ttu-id="b02fe-232">內容檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-232">Content file</span></span>|`"pack://application:,,,/ContentFile.xaml"`|  
|<span data-ttu-id="b02fe-233">子資料夾中的內容檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-233">Content file in subfolder</span></span>|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|  
|<span data-ttu-id="b02fe-234">來源網站檔案</span><span class="sxs-lookup"><span data-stu-id="b02fe-234">Site of origin file</span></span>|`"pack://siteoforigin:,,,/SOOFile.xaml"`|  
|<span data-ttu-id="b02fe-235">子資料夾中的來源網站檔案</span><span class="sxs-lookup"><span data-stu-id="b02fe-235">Site of origin file in subfolder</span></span>|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|  
  
 <span data-ttu-id="b02fe-236">表 2 說明各種相對的組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，您可以指定在標記中。</span><span class="sxs-lookup"><span data-stu-id="b02fe-236">Table 2 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in markup.</span></span>  
  
 <span data-ttu-id="b02fe-237">表 2：使用標記的相對套件 URI</span><span class="sxs-lookup"><span data-stu-id="b02fe-237">Table 2: Relative Pack URIs in Markup</span></span>  
  
|<span data-ttu-id="b02fe-238">檔案</span><span class="sxs-lookup"><span data-stu-id="b02fe-238">File</span></span>|<span data-ttu-id="b02fe-239">相對的組件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b02fe-239">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="b02fe-240">本機組件中的資源檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-240">Resource file in local assembly</span></span>|`"/ResourceFile.xaml"`|  
|<span data-ttu-id="b02fe-241">本機組件子資料夾中的資源檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-241">Resource file in subfolder of local assembly</span></span>|`"/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="b02fe-242">參考組件中的資源檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-242">Resource file in referenced assembly</span></span>|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|<span data-ttu-id="b02fe-243">參考組件之子資料夾中的資源檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-243">Resource file in subfolder of referenced assembly</span></span>|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|<span data-ttu-id="b02fe-244">內容檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-244">Content file</span></span>|`"/ContentFile.xaml"`|  
|<span data-ttu-id="b02fe-245">子資料夾中的內容檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-245">Content file in subfolder</span></span>|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### <a name="using-pack-uris-in-code"></a><span data-ttu-id="b02fe-246">透過程式碼使用套件 URI</span><span class="sxs-lookup"><span data-stu-id="b02fe-246">Using Pack URIs in Code</span></span>  
 <span data-ttu-id="b02fe-247">指定的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]藉由執行個體化的程式碼中<xref:System.Uri>類別，並傳遞此組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]做為參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="b02fe-247">You specify a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] in code by instantiating the <xref:System.Uri> class and passing the pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] as a parameter to the constructor.</span></span> <span data-ttu-id="b02fe-248">這點在下列範例中示範。</span><span class="sxs-lookup"><span data-stu-id="b02fe-248">This is demonstrated in the following example.</span></span>  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 <span data-ttu-id="b02fe-249">根據預設，<xref:System.Uri>類別會考慮的組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]為絕對。</span><span class="sxs-lookup"><span data-stu-id="b02fe-249">By default, the <xref:System.Uri> class considers pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to be absolute.</span></span> <span data-ttu-id="b02fe-250">因此，發生例外狀況時的執行個體<xref:System.Uri>類別建立與相對的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b02fe-250">Consequently, an exception is raised when an instance of the <xref:System.Uri> class is created with a relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 <span data-ttu-id="b02fe-251">幸運的是，<xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29>多載<xref:System.Uri>類別建構函式接受類型的參數<xref:System.UriKind>可讓您指定是否將組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]是絕對或相對。</span><span class="sxs-lookup"><span data-stu-id="b02fe-251">Fortunately, the <xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> overload of the <xref:System.Uri> class constructor accepts a parameter of type <xref:System.UriKind> to allow you to specify whether a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is either absolute or relative.</span></span>  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml",   
                        UriKind.Relative);  
```  
  
 <span data-ttu-id="b02fe-252">您應該只指定<xref:System.UriKind.Absolute>或<xref:System.UriKind.Relative>會確認提供的組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]是其中一個。</span><span class="sxs-lookup"><span data-stu-id="b02fe-252">You should specify only <xref:System.UriKind.Absolute> or <xref:System.UriKind.Relative> when you are certain that the provided pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] is one or the other.</span></span> <span data-ttu-id="b02fe-253">如果您不知道組件的型別[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]用，例如當使用者輸入組件[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]執行階段使用<xref:System.UriKind.RelativeOrAbsolute>改為。</span><span class="sxs-lookup"><span data-stu-id="b02fe-253">If you don't know the type of pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] that is used, such as when a user enters a pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] at run time, use <xref:System.UriKind.RelativeOrAbsolute> instead.</span></span>  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 <span data-ttu-id="b02fe-254">表 3 說明各種相對的組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，您可以指定在程式碼中使用<xref:System.Uri?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b02fe-254">Table 3 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code by using <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="b02fe-255">表 3：使用程式碼的絕對套件 URI</span><span class="sxs-lookup"><span data-stu-id="b02fe-255">Table 3: Absolute Pack URIs in Code</span></span>  
  
|<span data-ttu-id="b02fe-256">檔案</span><span class="sxs-lookup"><span data-stu-id="b02fe-256">File</span></span>|<span data-ttu-id="b02fe-257">絕對的組件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b02fe-257">Absolute pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="b02fe-258">資源檔 - 本機組件</span><span class="sxs-lookup"><span data-stu-id="b02fe-258">Resource file - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="b02fe-259">子資料夾中的資源檔 - 本機組件</span><span class="sxs-lookup"><span data-stu-id="b02fe-259">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="b02fe-260">資源檔 - 參考組件</span><span class="sxs-lookup"><span data-stu-id="b02fe-260">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="b02fe-261">參考組件之子資料夾中的資源檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-261">Resource file in subfolder of referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="b02fe-262">版本化參考組件中的資源檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-262">Resource file in versioned referenced assembly</span></span>|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="b02fe-263">內容檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-263">Content file</span></span>|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="b02fe-264">子資料夾中的內容檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-264">Content file in subfolder</span></span>|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="b02fe-265">來源網站檔案</span><span class="sxs-lookup"><span data-stu-id="b02fe-265">Site of origin file</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|  
|<span data-ttu-id="b02fe-266">子資料夾中的來源網站檔案</span><span class="sxs-lookup"><span data-stu-id="b02fe-266">Site of origin file in subfolder</span></span>|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|  
  
 <span data-ttu-id="b02fe-267">表 4 說明各種相對的組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，您可以指定在程式碼中使用<xref:System.Uri?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b02fe-267">Table 4 illustrates the various relative pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] that you can specify in code using <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="b02fe-268">表 4：使用程式碼的相對套件 URI</span><span class="sxs-lookup"><span data-stu-id="b02fe-268">Table 4: Relative Pack URIs in Code</span></span>  
  
|<span data-ttu-id="b02fe-269">檔案</span><span class="sxs-lookup"><span data-stu-id="b02fe-269">File</span></span>|<span data-ttu-id="b02fe-270">相對的組件 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b02fe-270">Relative pack [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]</span></span>|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="b02fe-271">資源檔 - 本機組件</span><span class="sxs-lookup"><span data-stu-id="b02fe-271">Resource file - local assembly</span></span>|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="b02fe-272">子資料夾中的資源檔 - 本機組件</span><span class="sxs-lookup"><span data-stu-id="b02fe-272">Resource file in subfolder - local assembly</span></span>|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="b02fe-273">資源檔 - 參考組件</span><span class="sxs-lookup"><span data-stu-id="b02fe-273">Resource file - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="b02fe-274">子資料夾中的資源檔 - 參考組件</span><span class="sxs-lookup"><span data-stu-id="b02fe-274">Resource file in subfolder - referenced assembly</span></span>|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="b02fe-275">內容檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-275">Content file</span></span>|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|<span data-ttu-id="b02fe-276">子資料夾中的內容檔</span><span class="sxs-lookup"><span data-stu-id="b02fe-276">Content file in subfolder</span></span>|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### <a name="common-pack-uri-scenarios"></a><span data-ttu-id="b02fe-277">常見套件 URI 案例</span><span class="sxs-lookup"><span data-stu-id="b02fe-277">Common Pack URI Scenarios</span></span>  
 <span data-ttu-id="b02fe-278">如前幾節討論了如何建構組件[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]來識別資源、 內容和來源檔案的站台。</span><span class="sxs-lookup"><span data-stu-id="b02fe-278">The preceding sections have discussed how to construct pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] to identify resource, content, and site of origin files.</span></span> <span data-ttu-id="b02fe-279">在[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、 這些語法結構用於各種不同的方式，以及下列各節涵蓋數個常見的使用方式。</span><span class="sxs-lookup"><span data-stu-id="b02fe-279">In [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], these constructions are used in a variety of ways, and the following sections cover several common usages.</span></span>  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a><span data-ttu-id="b02fe-280">指定要在啟動應用程式時顯示的 UI</span><span class="sxs-lookup"><span data-stu-id="b02fe-280">Specifying the UI to Show When an Application Starts</span></span>  
 <span data-ttu-id="b02fe-281"><xref:System.Windows.Application.StartupUri%2A> 指定第一個[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]以顯示[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="b02fe-281"><xref:System.Windows.Application.StartupUri%2A> specifies the first [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to show when a [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] application is launched.</span></span> <span data-ttu-id="b02fe-282">對於獨立應用程式，[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]可以是一個視窗中，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b02fe-282">For standalone applications, the [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] can be a window, as shown in the following example.</span></span>  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 <span data-ttu-id="b02fe-283">獨立應用程式和[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]也可以指定頁面做為初始的 UI 中，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b02fe-283">Standalone applications and [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] can also specify a page as the initial UI, as shown in the following example.</span></span>  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 <span data-ttu-id="b02fe-284">如果應用程式是一個獨立應用程式，並指定頁面<xref:System.Windows.Application.StartupUri%2A>，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]開啟<xref:System.Windows.Navigation.NavigationWindow>裝載的網頁。</span><span class="sxs-lookup"><span data-stu-id="b02fe-284">If the application is a standalone application and a page is specified with <xref:System.Windows.Application.StartupUri%2A>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] opens a <xref:System.Windows.Navigation.NavigationWindow> to host the page.</span></span> <span data-ttu-id="b02fe-285">如[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]，網頁會顯示主機瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="b02fe-285">For [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], the page is shown in the host browser.</span></span>  
  
<a name="Navigating_to_a_Page"></a>   
#### <a name="navigating-to-a-page"></a><span data-ttu-id="b02fe-286">巡覽至頁面</span><span class="sxs-lookup"><span data-stu-id="b02fe-286">Navigating to a Page</span></span>  
 <span data-ttu-id="b02fe-287">下列範例示範如何巡覽至頁面。</span><span class="sxs-lookup"><span data-stu-id="b02fe-287">The following example shows how to navigate to a page.</span></span>  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 <span data-ttu-id="b02fe-288">如需詳細資訊，以各種方式來巡覽程式[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，請參閱[巡覽概觀](../../../../docs/framework/wpf/app-development/navigation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b02fe-288">For more information on the various ways to navigate in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Navigation Overview](../../../../docs/framework/wpf/app-development/navigation-overview.md).</span></span>  
  
<a name="Specifying_a_Window_Icon"></a>   
#### <a name="specifying-a-window-icon"></a><span data-ttu-id="b02fe-289">指定視窗圖示</span><span class="sxs-lookup"><span data-stu-id="b02fe-289">Specifying a Window Icon</span></span>  
 <span data-ttu-id="b02fe-290">下列範例示範如何使用 URI 來指定視窗的圖示。</span><span class="sxs-lookup"><span data-stu-id="b02fe-290">The following example shows how to use a URI to specify a window's icon.</span></span>  
  
 [!code-xaml[WindowIconSnippets#WindowIconSetXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 <span data-ttu-id="b02fe-291">如需詳細資訊，請參閱<xref:System.Windows.Window.Icon%2A>。</span><span class="sxs-lookup"><span data-stu-id="b02fe-291">For more information, see <xref:System.Windows.Window.Icon%2A>.</span></span>  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### <a name="loading-image-audio-and-video-files"></a><span data-ttu-id="b02fe-292">載入影像、音訊和視訊檔案</span><span class="sxs-lookup"><span data-stu-id="b02fe-292">Loading Image, Audio, and Video Files</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="b02fe-293"> 可讓應用程式中使用各種不同的媒體類型，其中可以識別和使用組件載入[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b02fe-293"> allows applications to use a wide variety of media types, all of which can be identified and loaded with pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], as shown in the following examples.</span></span>  
  
 [!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xaml[ImageSample#ImagePackURIContent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 <span data-ttu-id="b02fe-294">如需使用媒體內容的詳細資訊，請參閱[圖形和多媒體](../../../../docs/framework/wpf/graphics-multimedia/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b02fe-294">For more information on working with media content, see [Graphics and Multimedia](../../../../docs/framework/wpf/graphics-multimedia/index.md).</span></span>  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a><span data-ttu-id="b02fe-295">從來源網站載入資源字典</span><span class="sxs-lookup"><span data-stu-id="b02fe-295">Loading a Resource Dictionary from the Site of Origin</span></span>  
 <span data-ttu-id="b02fe-296">資源字典 (<xref:System.Windows.ResourceDictionary>) 可以用來支援應用程式佈景主題。</span><span class="sxs-lookup"><span data-stu-id="b02fe-296">Resource dictionaries (<xref:System.Windows.ResourceDictionary>) can be used to support application themes.</span></span> <span data-ttu-id="b02fe-297">建立和管理主題的一種方法是將多個主題建立為位在應用程式來源網站的資源字典。</span><span class="sxs-lookup"><span data-stu-id="b02fe-297">One way to create and manage themes is to create multiple themes as resource dictionaries that are located at an application's site of origin.</span></span> <span data-ttu-id="b02fe-298">這樣可新增和更新主題，而不需要重新編譯和重新部署應用程式的。</span><span class="sxs-lookup"><span data-stu-id="b02fe-298">This allows themes to be added and updated without recompiling and redeploying an application.</span></span> <span data-ttu-id="b02fe-299">這些資源字典可以識別，並且使用組件載入[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]，這下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b02fe-299">These resource dictionaries can be identified and loaded using pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], which is shown in the following example.</span></span>  
  
 [!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 <span data-ttu-id="b02fe-300">如需在佈景主題的概觀[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，請參閱[設定樣式和範本](../../../../docs/framework/wpf/controls/styling-and-templating.md)。</span><span class="sxs-lookup"><span data-stu-id="b02fe-300">For an overview of themes in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b02fe-301">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b02fe-301">See Also</span></span>  
 [<span data-ttu-id="b02fe-302">WPF 應用程式資源、內容和資料檔案</span><span class="sxs-lookup"><span data-stu-id="b02fe-302">WPF Application Resource, Content, and Data Files</span></span>](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
