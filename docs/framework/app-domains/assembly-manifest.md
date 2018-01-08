---
title: "組件資訊清單"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41dc27798e9d39d391e5958b86f691e3a0062582
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-manifest"></a><span data-ttu-id="8d0b1-102">組件資訊清單</span><span class="sxs-lookup"><span data-stu-id="8d0b1-102">Assembly Manifest</span></span>
<span data-ttu-id="8d0b1-103">每個組件 (不論是靜態或是動態) 都含有描述組件中項目彼此如何關聯的資料集合。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-103">Every assembly, whether static or dynamic, contains a collection of data that describes how the elements in the assembly relate to each other.</span></span> <span data-ttu-id="8d0b1-104">組件資訊清單就包含這個組件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-104">The assembly manifest contains this assembly metadata.</span></span> <span data-ttu-id="8d0b1-105">組件資訊清單含有指定組件的版本需求和安全性識別所需的所有中繼資料，以及定義組件範圍和解析資源與類別參考所需的所有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-105">An assembly manifest contains all the metadata needed to specify the assembly's version requirements and security identity, and all metadata needed to define the scope of the assembly and resolve references to resources and classes.</span></span> <span data-ttu-id="8d0b1-106">組件資訊清單可以存放在具有 Microsoft Intermediate Language (MSIL) 程式碼的可移植執行檔 (PE) (.exe 或 .dll) 中，或者存放在只包含組件資訊清單的獨立 PE 檔中。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-106">The assembly manifest can be stored in either a PE file (an .exe or .dll) with Microsoft intermediate language (MSIL) code or in a standalone PE file that contains only assembly manifest information.</span></span>  
  
 <span data-ttu-id="8d0b1-107">下圖所示為儲存資訊清單的不同方式。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-107">The following illustration shows the different ways the manifest can be stored.</span></span>  
  
 <span data-ttu-id="8d0b1-108">![單一檔案組件](../../../docs/framework/app-domains/media/assemblytypes.gif "assemblytypes")</span><span class="sxs-lookup"><span data-stu-id="8d0b1-108">![A single&#45;file assembly](../../../docs/framework/app-domains/media/assemblytypes.gif "assemblytypes")</span></span>  
<span data-ttu-id="8d0b1-109">組件的類型</span><span class="sxs-lookup"><span data-stu-id="8d0b1-109">Types of assemblies</span></span>  
  
 <span data-ttu-id="8d0b1-110">對於具有一個關聯檔案的組件，資訊清單是合併在 PE 檔中以構成單一檔案組件。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-110">For an assembly with one associated file, the manifest is incorporated into the PE file to form a single-file assembly.</span></span> <span data-ttu-id="8d0b1-111">您可以建立多檔案組件，它可具有獨立的資訊清單檔案，或者將資訊清單合併在該組件中的某一個 PE 檔中。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-111">You can create a multifile assembly with a standalone manifest file or with the manifest incorporated into one of the PE files in the assembly.</span></span>  
  
 <span data-ttu-id="8d0b1-112">每個組件的資訊清單都會執行下列功能：</span><span class="sxs-lookup"><span data-stu-id="8d0b1-112">Each assembly's manifest performs the following functions:</span></span>  
  
-   <span data-ttu-id="8d0b1-113">列舉構成組件的檔案</span><span class="sxs-lookup"><span data-stu-id="8d0b1-113">Enumerates the files that make up the assembly.</span></span>  
  
-   <span data-ttu-id="8d0b1-114">控制組件之型別和資源的參考如何對應到含有它們的宣告和實作的檔案</span><span class="sxs-lookup"><span data-stu-id="8d0b1-114">Governs how references to the assembly's types and resources map to the files that contain their declarations and implementations.</span></span>  
  
-   <span data-ttu-id="8d0b1-115">列舉組件所依賴的其他組件</span><span class="sxs-lookup"><span data-stu-id="8d0b1-115">Enumerates other assemblies on which the assembly depends.</span></span>  
  
-   <span data-ttu-id="8d0b1-116">在組件使用者與組件的實作詳細資料之間提供一層間接取值 (Indirection)</span><span class="sxs-lookup"><span data-stu-id="8d0b1-116">Provides a level of indirection between consumers of the assembly and the assembly's implementation details.</span></span>  
  
-   <span data-ttu-id="8d0b1-117">轉譯組件的自我描述</span><span class="sxs-lookup"><span data-stu-id="8d0b1-117">Renders the assembly self-describing.</span></span>  
  
## <a name="assembly-manifest-contents"></a><span data-ttu-id="8d0b1-118">組件資訊清單內容</span><span class="sxs-lookup"><span data-stu-id="8d0b1-118">Assembly Manifest Contents</span></span>  
 <span data-ttu-id="8d0b1-119">下表所示為組件資訊清單中包含的資訊。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-119">The following table shows the information contained in the assembly manifest.</span></span> <span data-ttu-id="8d0b1-120">前四個項目 - 組件名稱、版本號碼、文化特性 (Culture) 和強式名稱 (Strong Name) 資訊 - 構成組件的識別。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-120">The first four items—the assembly name, version number, culture, and strong name information—make up the assembly's identity.</span></span>  
  
|<span data-ttu-id="8d0b1-121">資訊</span><span class="sxs-lookup"><span data-stu-id="8d0b1-121">Information</span></span>|<span data-ttu-id="8d0b1-122">描述</span><span class="sxs-lookup"><span data-stu-id="8d0b1-122">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="8d0b1-123">組件名稱</span><span class="sxs-lookup"><span data-stu-id="8d0b1-123">Assembly name</span></span>|<span data-ttu-id="8d0b1-124">指定組件名稱的文字字串。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-124">A text string specifying the assembly's name.</span></span>|  
|<span data-ttu-id="8d0b1-125">版本號碼</span><span class="sxs-lookup"><span data-stu-id="8d0b1-125">Version number</span></span>|<span data-ttu-id="8d0b1-126">主要和次要版本號碼，以及修訂和組建編號。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-126">A major and minor version number, and a revision and build number.</span></span> <span data-ttu-id="8d0b1-127">Common Language Runtime 會使用這些編號來強制執行版本原則。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-127">The common language runtime uses these numbers to enforce version policy.</span></span>|  
|<span data-ttu-id="8d0b1-128">culture</span><span class="sxs-lookup"><span data-stu-id="8d0b1-128">Culture</span></span>|<span data-ttu-id="8d0b1-129">有關組件所支援文化特性或語言的資訊。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-129">Information on the culture or language the assembly supports.</span></span> <span data-ttu-id="8d0b1-130">這項資訊應該只用來將組件指定為包含文化特性或語言相關資訊的附屬組件</span><span class="sxs-lookup"><span data-stu-id="8d0b1-130">This information should be used only to designate an assembly as a satellite assembly containing culture- or language-specific information.</span></span> <span data-ttu-id="8d0b1-131">(具有文化特性資訊的組件會自動假設為附屬組件)。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-131">(An assembly with culture information is automatically assumed to be a satellite assembly.)</span></span>|  
|<span data-ttu-id="8d0b1-132">強式名稱資訊</span><span class="sxs-lookup"><span data-stu-id="8d0b1-132">Strong name information</span></span>|<span data-ttu-id="8d0b1-133">如果已經為組件指定強式名稱，則為發行者 (Publisher) 的公開金鑰 (Public Key)。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-133">The public key from the publisher if the assembly has been given a strong name.</span></span>|  
|<span data-ttu-id="8d0b1-134">組件中所有檔案的清單</span><span class="sxs-lookup"><span data-stu-id="8d0b1-134">List of all files in the assembly</span></span>|<span data-ttu-id="8d0b1-135">組件中所含每一檔案的雜湊和檔名。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-135">A hash of each file contained in the assembly and a file name.</span></span> <span data-ttu-id="8d0b1-136">請注意，構成組件的所有檔案必須與含有組件資訊清單的檔案在同一個目錄中。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-136">Note that all files that make up the assembly must be in the same directory as the file containing the assembly manifest.</span></span>|  
|<span data-ttu-id="8d0b1-137">型別參考資訊</span><span class="sxs-lookup"><span data-stu-id="8d0b1-137">Type reference information</span></span>|<span data-ttu-id="8d0b1-138">Runtime 用來將型別參考對應到含有其宣告和實作之檔案的資訊。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-138">Information used by the runtime to map a type reference to the file that contains its declaration and implementation.</span></span> <span data-ttu-id="8d0b1-139">這是使用於從組件匯出之型別。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-139">This is used for types that are exported from the assembly.</span></span>|  
|<span data-ttu-id="8d0b1-140">所參考組件的資訊</span><span class="sxs-lookup"><span data-stu-id="8d0b1-140">Information on referenced assemblies</span></span>|<span data-ttu-id="8d0b1-141">組件以靜態方式參考之其他組件的清單。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-141">A list of other assemblies that are statically referenced by the assembly.</span></span> <span data-ttu-id="8d0b1-142">每一參考包括相依組件的名稱、組件中繼資料 (版本、文化特性、作業系統等)，以及公開金鑰 (如果組件具有強式名稱)。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-142">Each reference includes the dependent assembly's name, assembly metadata (version, culture, operating system, and so on), and public key, if the assembly is strong named.</span></span>|  
  
 <span data-ttu-id="8d0b1-143">您可以在程式碼中使用組件屬性在組件資訊清單中加入或變更某些資訊。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-143">You can add or change some information in the assembly manifest by using assembly attributes in your code.</span></span> <span data-ttu-id="8d0b1-144">您可以變更版本資訊和資訊屬性，包括商標、著作權、產品、公司和資訊版本。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-144">You can change version information and informational attributes, including Trademark, Copyright, Product, Company, and Informational Version.</span></span> <span data-ttu-id="8d0b1-145">如需完整的組件屬性清單，請參閱[設定組件屬性](../../../docs/framework/app-domains/set-assembly-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="8d0b1-145">For a complete list of assembly attributes, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d0b1-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="8d0b1-146">See Also</span></span>  
 [<span data-ttu-id="8d0b1-147">組件內容</span><span class="sxs-lookup"><span data-stu-id="8d0b1-147">Assembly Contents</span></span>](../../../docs/framework/app-domains/assembly-contents.md)  
 [<span data-ttu-id="8d0b1-148">組件版本控制</span><span class="sxs-lookup"><span data-stu-id="8d0b1-148">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 [<span data-ttu-id="8d0b1-149">建立附屬組件</span><span class="sxs-lookup"><span data-stu-id="8d0b1-149">Creating Satellite Assemblies</span></span>](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)  
 [<span data-ttu-id="8d0b1-150">強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="8d0b1-150">Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/strong-named-assemblies.md)
