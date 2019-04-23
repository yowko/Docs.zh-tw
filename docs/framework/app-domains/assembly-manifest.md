---
title: 組件資訊清單
ms.date: 03/30/2017
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cce67b36330714a821012082457e0297395a09c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087530"
---
# <a name="assembly-manifest"></a><span data-ttu-id="de608-102">組件資訊清單</span><span class="sxs-lookup"><span data-stu-id="de608-102">Assembly Manifest</span></span>
<span data-ttu-id="de608-103">每個組件 (不論是靜態或是動態) 都含有描述組件中項目彼此如何關聯的資料集合。</span><span class="sxs-lookup"><span data-stu-id="de608-103">Every assembly, whether static or dynamic, contains a collection of data that describes how the elements in the assembly relate to each other.</span></span> <span data-ttu-id="de608-104">組件資訊清單就包含這個組件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="de608-104">The assembly manifest contains this assembly metadata.</span></span> <span data-ttu-id="de608-105">組件資訊清單含有指定組件的版本需求和安全性識別所需的所有中繼資料，以及定義組件範圍和解析資源與類別參考所需的所有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="de608-105">An assembly manifest contains all the metadata needed to specify the assembly's version requirements and security identity, and all metadata needed to define the scope of the assembly and resolve references to resources and classes.</span></span> <span data-ttu-id="de608-106">組件資訊清單可以存放在具有 Microsoft Intermediate Language (MSIL) 程式碼的可移植執行檔 (PE) (.exe 或 .dll) 中，或者存放在只包含組件資訊清單的獨立 PE 檔中。</span><span class="sxs-lookup"><span data-stu-id="de608-106">The assembly manifest can be stored in either a PE file (an .exe or .dll) with Microsoft intermediate language (MSIL) code or in a standalone PE file that contains only assembly manifest information.</span></span>  
  
 <span data-ttu-id="de608-107">下圖所示為儲存資訊清單的不同方式。</span><span class="sxs-lookup"><span data-stu-id="de608-107">The following illustration shows the different ways the manifest can be stored.</span></span>  
  
 ![在單一檔案組件和多檔案組件組態中顯示資訊清單的圖表。](./media/assembly-manifest/assembly-types-diagram.gif)  
  
 <span data-ttu-id="de608-109">對於具有一個關聯檔案的組件，資訊清單是合併在 PE 檔中以構成單一檔案組件。</span><span class="sxs-lookup"><span data-stu-id="de608-109">For an assembly with one associated file, the manifest is incorporated into the PE file to form a single-file assembly.</span></span> <span data-ttu-id="de608-110">您可以建立多檔案組件，它可具有獨立的資訊清單檔案，或者將資訊清單合併在該組件中的某一個 PE 檔中。</span><span class="sxs-lookup"><span data-stu-id="de608-110">You can create a multifile assembly with a standalone manifest file or with the manifest incorporated into one of the PE files in the assembly.</span></span>  
  
 <span data-ttu-id="de608-111">每個組件的資訊清單都會執行下列功能：</span><span class="sxs-lookup"><span data-stu-id="de608-111">Each assembly's manifest performs the following functions:</span></span>  
  
-   <span data-ttu-id="de608-112">列舉構成組件的檔案</span><span class="sxs-lookup"><span data-stu-id="de608-112">Enumerates the files that make up the assembly.</span></span>  
  
-   <span data-ttu-id="de608-113">控制組件之型別和資源的參考如何對應到含有它們的宣告和實作的檔案</span><span class="sxs-lookup"><span data-stu-id="de608-113">Governs how references to the assembly's types and resources map to the files that contain their declarations and implementations.</span></span>  
  
-   <span data-ttu-id="de608-114">列舉組件所依賴的其他組件</span><span class="sxs-lookup"><span data-stu-id="de608-114">Enumerates other assemblies on which the assembly depends.</span></span>  
  
-   <span data-ttu-id="de608-115">在組件使用者與組件的實作詳細資料之間提供一層間接取值 (Indirection)</span><span class="sxs-lookup"><span data-stu-id="de608-115">Provides a level of indirection between consumers of the assembly and the assembly's implementation details.</span></span>  
  
-   <span data-ttu-id="de608-116">轉譯組件的自我描述</span><span class="sxs-lookup"><span data-stu-id="de608-116">Renders the assembly self-describing.</span></span>  
  
## <a name="assembly-manifest-contents"></a><span data-ttu-id="de608-117">組件資訊清單內容</span><span class="sxs-lookup"><span data-stu-id="de608-117">Assembly Manifest Contents</span></span>  
 <span data-ttu-id="de608-118">下表所示為組件資訊清單中包含的資訊。</span><span class="sxs-lookup"><span data-stu-id="de608-118">The following table shows the information contained in the assembly manifest.</span></span> <span data-ttu-id="de608-119">前四個項目 - 組件名稱、版本號碼、文化特性 (Culture) 和強式名稱 (Strong Name) 資訊 - 構成組件的識別。</span><span class="sxs-lookup"><span data-stu-id="de608-119">The first four items—the assembly name, version number, culture, and strong name information—make up the assembly's identity.</span></span>  
  
|<span data-ttu-id="de608-120">資訊</span><span class="sxs-lookup"><span data-stu-id="de608-120">Information</span></span>|<span data-ttu-id="de608-121">說明</span><span class="sxs-lookup"><span data-stu-id="de608-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="de608-122">組件名稱</span><span class="sxs-lookup"><span data-stu-id="de608-122">Assembly name</span></span>|<span data-ttu-id="de608-123">指定組件名稱的文字字串。</span><span class="sxs-lookup"><span data-stu-id="de608-123">A text string specifying the assembly's name.</span></span>|  
|<span data-ttu-id="de608-124">版本號碼</span><span class="sxs-lookup"><span data-stu-id="de608-124">Version number</span></span>|<span data-ttu-id="de608-125">主要和次要版本號碼，以及修訂和組建編號。</span><span class="sxs-lookup"><span data-stu-id="de608-125">A major and minor version number, and a revision and build number.</span></span> <span data-ttu-id="de608-126">Common Language Runtime 會使用這些編號來強制執行版本原則。</span><span class="sxs-lookup"><span data-stu-id="de608-126">The common language runtime uses these numbers to enforce version policy.</span></span>|  
|<span data-ttu-id="de608-127">culture</span><span class="sxs-lookup"><span data-stu-id="de608-127">Culture</span></span>|<span data-ttu-id="de608-128">有關組件所支援文化特性或語言的資訊。</span><span class="sxs-lookup"><span data-stu-id="de608-128">Information on the culture or language the assembly supports.</span></span> <span data-ttu-id="de608-129">這項資訊應該只用來將組件指定為包含文化特性或語言相關資訊的附屬組件</span><span class="sxs-lookup"><span data-stu-id="de608-129">This information should be used only to designate an assembly as a satellite assembly containing culture- or language-specific information.</span></span> <span data-ttu-id="de608-130">(具有文化特性資訊的組件會自動假設為附屬組件)。</span><span class="sxs-lookup"><span data-stu-id="de608-130">(An assembly with culture information is automatically assumed to be a satellite assembly.)</span></span>|  
|<span data-ttu-id="de608-131">強式名稱資訊</span><span class="sxs-lookup"><span data-stu-id="de608-131">Strong name information</span></span>|<span data-ttu-id="de608-132">如果已經為組件指定強式名稱，則為發行者 (Publisher) 的公開金鑰 (Public Key)。</span><span class="sxs-lookup"><span data-stu-id="de608-132">The public key from the publisher if the assembly has been given a strong name.</span></span>|  
|<span data-ttu-id="de608-133">組件中所有檔案的清單</span><span class="sxs-lookup"><span data-stu-id="de608-133">List of all files in the assembly</span></span>|<span data-ttu-id="de608-134">組件中所含每一檔案的雜湊和檔名。</span><span class="sxs-lookup"><span data-stu-id="de608-134">A hash of each file contained in the assembly and a file name.</span></span> <span data-ttu-id="de608-135">請注意，構成組件的所有檔案必須與含有組件資訊清單的檔案在同一個目錄中。</span><span class="sxs-lookup"><span data-stu-id="de608-135">Note that all files that make up the assembly must be in the same directory as the file containing the assembly manifest.</span></span>|  
|<span data-ttu-id="de608-136">型別參考資訊</span><span class="sxs-lookup"><span data-stu-id="de608-136">Type reference information</span></span>|<span data-ttu-id="de608-137">Runtime 用來將型別參考對應到含有其宣告和實作之檔案的資訊。</span><span class="sxs-lookup"><span data-stu-id="de608-137">Information used by the runtime to map a type reference to the file that contains its declaration and implementation.</span></span> <span data-ttu-id="de608-138">這是使用於從組件匯出之型別。</span><span class="sxs-lookup"><span data-stu-id="de608-138">This is used for types that are exported from the assembly.</span></span>|  
|<span data-ttu-id="de608-139">所參考組件的資訊</span><span class="sxs-lookup"><span data-stu-id="de608-139">Information on referenced assemblies</span></span>|<span data-ttu-id="de608-140">組件以靜態方式參考之其他組件的清單。</span><span class="sxs-lookup"><span data-stu-id="de608-140">A list of other assemblies that are statically referenced by the assembly.</span></span> <span data-ttu-id="de608-141">每一參考包括相依組件的名稱、組件中繼資料 (版本、文化特性、作業系統等)，以及公開金鑰 (如果組件具有強式名稱)。</span><span class="sxs-lookup"><span data-stu-id="de608-141">Each reference includes the dependent assembly's name, assembly metadata (version, culture, operating system, and so on), and public key, if the assembly is strong named.</span></span>|  
  
 <span data-ttu-id="de608-142">您可以在程式碼中使用組件屬性在組件資訊清單中加入或變更某些資訊。</span><span class="sxs-lookup"><span data-stu-id="de608-142">You can add or change some information in the assembly manifest by using assembly attributes in your code.</span></span> <span data-ttu-id="de608-143">您可以變更版本資訊和資訊屬性，包括商標、著作權、產品、公司和資訊版本。</span><span class="sxs-lookup"><span data-stu-id="de608-143">You can change version information and informational attributes, including Trademark, Copyright, Product, Company, and Informational Version.</span></span> <span data-ttu-id="de608-144">如需完整的組件屬性清單，請參閱[設定組件屬性](../../../docs/framework/app-domains/set-assembly-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="de608-144">For a complete list of assembly attributes, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de608-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de608-145">See also</span></span>

- [<span data-ttu-id="de608-146">組件內容</span><span class="sxs-lookup"><span data-stu-id="de608-146">Assembly Contents</span></span>](../../../docs/framework/app-domains/assembly-contents.md)
- [<span data-ttu-id="de608-147">組件版本控制</span><span class="sxs-lookup"><span data-stu-id="de608-147">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)
- [<span data-ttu-id="de608-148">建立附屬組件</span><span class="sxs-lookup"><span data-stu-id="de608-148">Creating Satellite Assemblies</span></span>](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [<span data-ttu-id="de608-149">強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="de608-149">Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/strong-named-assemblies.md)
