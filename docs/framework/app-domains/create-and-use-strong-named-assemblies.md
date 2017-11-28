---
title: "建立和使用強式名稱的組件"
ms.date: 08/01/2017
ms.prod: .net-framework
ms.technology: dotnet-bcl
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, about strong-named assemblies
- strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, scenarios
- assemblies [.NET Framework], strong-named
- strong-named assemblies, loading into trusted application domains
- assembly binding, strong-named
ms.assetid: ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 39fbd38549a791a761c633dca90dbdeeeefce10b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="creating-and-using-strong-named-assemblies"></a><span data-ttu-id="a4fc5-102">建立和使用強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="a4fc5-102">Creating and Using Strong-Named Assemblies</span></span>
<span data-ttu-id="a4fc5-103"><a name="top"></a> 強式名稱是由組件的識別，也就是其簡單文字名稱、版本號碼及文化特性資訊 (如果有提供)，加上公開金鑰和數位簽章所組成的。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-103"><a name="top"></a> A strong name consists of the assembly's identity—its simple text name, version number, and culture information (if provided)—plus a public key and a digital signature.</span></span> <span data-ttu-id="a4fc5-104">這是使用對應的私密金鑰，從組件檔案所產生 </span><span class="sxs-lookup"><span data-stu-id="a4fc5-104">It is generated from an assembly file using the corresponding private key.</span></span> <span data-ttu-id="a4fc5-105">(組件檔案包含附屬組件資訊清單，而資訊清單則包含組件中所有檔案的名稱和雜湊)。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-105">(The assembly file contains the assembly manifest, which contains the names and hashes of all the files that make up the assembly.)</span></span>  
  
 <span data-ttu-id="a4fc5-106">強式名稱的組件只可使用來自其他強式名稱組件的類型。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-106">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="a4fc5-107">否則，強式名稱組件的完整性會受到危害。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-107">Otherwise, the integrity of the strong-named assembly would be compromised.</span></span>  
  
 <span data-ttu-id="a4fc5-108">本概觀包含下列各節：</span><span class="sxs-lookup"><span data-stu-id="a4fc5-108">This overview contains the following sections:</span></span>  
  
-   [<span data-ttu-id="a4fc5-109">強式名稱案例</span><span class="sxs-lookup"><span data-stu-id="a4fc5-109">Strong Name Scenario</span></span>](#strong_name_scenario)  
  
-   [<span data-ttu-id="a4fc5-110">略過信任組件的簽章驗證</span><span class="sxs-lookup"><span data-stu-id="a4fc5-110">Bypassing Signature Verification of Trusted Assemblies</span></span>](#bypassing_signature_verification)  
  
-   [<span data-ttu-id="a4fc5-111">相關主題</span><span class="sxs-lookup"><span data-stu-id="a4fc5-111">Related Topics</span></span>](#related_topics)  
  
<a name="strong_name_scenario"></a>   
## <a name="strong-name-scenario"></a><span data-ttu-id="a4fc5-112">強式名稱案例</span><span class="sxs-lookup"><span data-stu-id="a4fc5-112">Strong Name Scenario</span></span>  
 <span data-ttu-id="a4fc5-113">下列案例概述處理序如何使用強式名稱簽署組件，然後再使用該名稱參考該組件。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-113">The following scenario outlines the process of signing an assembly with a strong name and later referencing it by that name.</span></span>  
  
1.  <span data-ttu-id="a4fc5-114">組件 A 是以下列方法之一，使用強式名稱所建立：</span><span class="sxs-lookup"><span data-stu-id="a4fc5-114">Assembly A is created with a strong name using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="a4fc5-115">使用支援建立強式名稱的開發環境，例如 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-115">Using a development environment that supports creating strong names, such as [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].</span></span>  
  
    -   <span data-ttu-id="a4fc5-116">使用[強式名稱工具 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) 建立密碼編譯金鑰組，並使用命令列編譯器或[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將該金鑰組指派給組件。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-116">Creating a cryptographic key pair using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) and assigning that key pair to the assembly using either a command-line compiler or the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="a4fc5-117">Windows 軟體開發套件 (SDK) 提供 Sn.exe 和 Al.exe。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-117">The Windows Software Development Kit (SDK) provides both Sn.exe and Al.exe.</span></span>  
  
2.  <span data-ttu-id="a4fc5-118">開發環境或工具會使用開發人員的私密金鑰簽署檔案雜湊，而該檔案中包含組件的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-118">The development environment or tool signs the hash of the file containing the assembly's manifest with the developer's private key.</span></span> <span data-ttu-id="a4fc5-119">此數位簽章儲存在可攜式執行檔 (PE) 中，而該檔案包含組件 A 的 資訊清單。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-119">This digital signature is stored in the portable executable (PE) file that contains Assembly A's manifest.</span></span>  
  
3.  <span data-ttu-id="a4fc5-120">組件 B 是組件 A 的消費者。組件 B 的資訊清單參考區段包含代表組件 A 公開金鑰的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-120">Assembly B is a consumer of Assembly A. The reference section of Assembly B's manifest includes a token that represents Assembly A's public key.</span></span> <span data-ttu-id="a4fc5-121">語彙基元是完整公開金鑰的一部分，會取代金鑰本身來節省空間。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-121">A token is a portion of the full public key and is used rather than the key itself to save space.</span></span>  
  
4.  <span data-ttu-id="a4fc5-122">當組件放在全域組件快取時，Common Language Runtime 會驗證強式名稱簽草章。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-122">The common language runtime verifies the strong name signature when the assembly is placed in the global assembly cache.</span></span> <span data-ttu-id="a4fc5-123">Common Language Runtime 在執行階段以強式名稱繫結時，會比較儲存在組件 B 資訊清單的金鑰，以及用來產生組件 A 強式名稱的金鑰。若 .NET Framework 通過安全性檢查且繫結成功，組件 B 就能保證組件 A 的位元未被修改，而且確實來自組件 A 的開發人員。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-123">When binding by strong name at run time, the common language runtime compares the key stored in Assembly B's manifest with the key used to generate the strong name for Assembly A. If the .NET Framework security checks pass and the bind succeeds, Assembly B has a guarantee that Assembly A's bits have not been tampered with and that these bits actually come from the developers of Assembly A.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4fc5-124">此案例無法解決信任問題。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-124">This scenario doesn't address trust issues.</span></span> <span data-ttu-id="a4fc5-125">除了強式名稱之外，組件能夠包含完整的 Microsoft Authenticode 簽章。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-125">Assemblies can carry full Microsoft Authenticode signatures in addition to a strong name.</span></span> <span data-ttu-id="a4fc5-126">Authenticode 簽章包含建立信任的憑證。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-126">Authenticode signatures include a certificate that establishes trust.</span></span> <span data-ttu-id="a4fc5-127">請務必注意，強式名稱不會要求程式碼以這種方式簽署。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-127">It's important to note that strong names don't require code to be signed in this way.</span></span> <span data-ttu-id="a4fc5-128">強式名稱僅提供唯一身分識別。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-128">Strong names only provide a unique identity.</span></span>  
  
 [<span data-ttu-id="a4fc5-129">回到頁首</span><span class="sxs-lookup"><span data-stu-id="a4fc5-129">Back to top</span></span>](#top)  
  
<a name="bypassing_signature_verification"></a>   
## <a name="bypassing-signature-verification-of-trusted-assemblies"></a><span data-ttu-id="a4fc5-130">略過信任組件的簽章驗證</span><span class="sxs-lookup"><span data-stu-id="a4fc5-130">Bypassing Signature Verification of Trusted Assemblies</span></span>  
 <span data-ttu-id="a4fc5-131">從 [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)] 開始，當組件載入到完全信任的應用程式網域 (例如適用於 `MyComputer` 區域的預設應用程式網域) 時，不會驗證強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-131">Starting with the [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], strong-name signatures are not validated when an assembly is loaded into a full-trust application domain, such as the default application domain for the `MyComputer` zone.</span></span> <span data-ttu-id="a4fc5-132">這是指強式名稱略過功能。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-132">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="a4fc5-133">在完全信任環境中，不論簽章為何，已簽署、完全信任的組件要求 <xref:System.Security.Permissions.StrongNameIdentityPermission> 一律會成功。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-133">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies, regardless of their signature.</span></span> <span data-ttu-id="a4fc5-134">強式名稱略過功能可以避免在這種狀況中不必要的額外負荷，也就是完全信任組件的強式名稱簽章驗證，讓組件能夠更快載入。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-134">The strong-name bypass feature avoids the unnecessary overhead of strong-name signature verification of full-trust assemblies in this situation, allowing the assemblies to load faster.</span></span>  
  
 <span data-ttu-id="a4fc5-135">略過功能適用於任何以強式名稱簽署並具有下列特性的組件：</span><span class="sxs-lookup"><span data-stu-id="a4fc5-135">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="a4fc5-136">完全信任而不具有 <xref:System.Security.Policy.StrongName> 辨識項 (例如具有 `MyComputer` 區域辨識項)。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-136">Fully trusted without <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
-   <span data-ttu-id="a4fc5-137">載入到完全信任的 <xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-137">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="a4fc5-138">從 <xref:System.AppDomain> 的 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性下的位置載入。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-138">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="a4fc5-139">不延遲簽署。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-139">Not delay-signed.</span></span>  
  
 <span data-ttu-id="a4fc5-140">個別應用程式或電腦可停用此功能。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-140">This feature can be disabled for individual applications or for a computer.</span></span> <span data-ttu-id="a4fc5-141">請參閱[如何：停用強式名稱略過功能](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-141">See [How to: Disable the Strong-Name Bypass Feature](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
 [<span data-ttu-id="a4fc5-142">回到頁首</span><span class="sxs-lookup"><span data-stu-id="a4fc5-142">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="a4fc5-143">相關主題</span><span class="sxs-lookup"><span data-stu-id="a4fc5-143">Related Topics</span></span>  
  
|<span data-ttu-id="a4fc5-144">標題</span><span class="sxs-lookup"><span data-stu-id="a4fc5-144">Title</span></span>|<span data-ttu-id="a4fc5-145">描述</span><span class="sxs-lookup"><span data-stu-id="a4fc5-145">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a4fc5-146">如何：建立公開/私密金鑰組</span><span class="sxs-lookup"><span data-stu-id="a4fc5-146">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)|<span data-ttu-id="a4fc5-147">描述如何建立簽署組件的密碼編譯金鑰組。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-147">Describes how to create a cryptographic key pair for signing an assembly.</span></span>|  
|[<span data-ttu-id="a4fc5-148">如何：使用強式名稱簽署組件</span><span class="sxs-lookup"><span data-stu-id="a4fc5-148">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)|<span data-ttu-id="a4fc5-149">描述如何建立強式名稱組件。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-149">Describes how to create a strong-named assembly.</span></span>|  
|[<span data-ttu-id="a4fc5-150">進階強式命名</span><span class="sxs-lookup"><span data-stu-id="a4fc5-150">Enhanced Strong Naming</span></span>](../../../docs/framework/app-domains/enhanced-strong-naming.md)|<span data-ttu-id="a4fc5-151">描述 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中強式名稱的改進項目。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-151">Describes enhancements to strong-names in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|[<span data-ttu-id="a4fc5-152">如何：參考以強式名稱命名的組件</span><span class="sxs-lookup"><span data-stu-id="a4fc5-152">How to: Reference a Strong-Named Assembly</span></span>](../../../docs/framework/app-domains/how-to-reference-a-strong-named-assembly.md)|<span data-ttu-id="a4fc5-153">描述如何在編譯或執行階段期間，參考以強式名稱命名之組件中的類型或資源。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-153">Describes how to reference types or resources in a strong-named assembly at compile time or run time.</span></span>|  
|[<span data-ttu-id="a4fc5-154">如何：停用強式名稱略過功能</span><span class="sxs-lookup"><span data-stu-id="a4fc5-154">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)|<span data-ttu-id="a4fc5-155">描述如何停用會略過強式名稱簽章驗證的功能。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-155">Describes how to disable the feature that bypasses the validation of strong-name signatures.</span></span> <span data-ttu-id="a4fc5-156">所有應用程式皆可停用此功能，也可以只停用特定應用程式中的此功能。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-156">This feature can be disabled for all or for specific applications.</span></span>|  
|[<span data-ttu-id="a4fc5-157">建立組件</span><span class="sxs-lookup"><span data-stu-id="a4fc5-157">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)|<span data-ttu-id="a4fc5-158">提供單一檔案和多檔案組件的概觀。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-158">Provides an overview of single-file and multifile assemblies.</span></span>|  
|[<span data-ttu-id="a4fc5-159">如何在 Visual Studio 中延遲簽署組件</span><span class="sxs-lookup"><span data-stu-id="a4fc5-159">How to Delay Sign an Assembly in Visual Studio</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|<span data-ttu-id="a4fc5-160">說明如何在建立組件之後，使用強式名稱簽署組件。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-160">Explains how to sign an assembly with a strong name after the assembly has been created.</span></span>|  
|[<span data-ttu-id="a4fc5-161">Sn.exe (強式名稱工具)</span><span class="sxs-lookup"><span data-stu-id="a4fc5-161">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)|<span data-ttu-id="a4fc5-162">描述 .NET Framework 中可協助使用強式名稱來建立組件的工具。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-162">Describes the tool included in the .NET Framework that helps create assemblies with strong names.</span></span> <span data-ttu-id="a4fc5-163">這個工具提供了金鑰管理、簽章產生和簽章驗證的選項。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-163">This tool provides options for key management, signature generation, and signature verification.</span></span>|  
|[<span data-ttu-id="a4fc5-164">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="a4fc5-164">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)|<span data-ttu-id="a4fc5-165">描述 .NET Framework 中可產生檔案的工具，而該檔案具有來自模組或資源檔案組件的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="a4fc5-165">Describes the tool included in the .NET Framework that generates a file that has an assembly manifest from modules or resource files.</span></span>|
