---
title: 如何：建立發行者原則
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
author: mcleblanc
ms.author: markl
ms.openlocfilehash: e7cac3c7e6c588a82e9dfff169ba7b7aa72c35f8
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028010"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="5e770-102">如何：建立發行者原則</span><span class="sxs-lookup"><span data-stu-id="5e770-102">How to: Create a Publisher Policy</span></span>
<span data-ttu-id="5e770-103">組件的廠商可以應用程式應該使用較新版的組件，包含與升級後的組件的發行者原則檔的狀態。</span><span class="sxs-lookup"><span data-stu-id="5e770-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="5e770-104">發行者原則檔會指定組件重新導向和程式碼基底設定，並使用應用程式組態檔相同的格式。</span><span class="sxs-lookup"><span data-stu-id="5e770-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="5e770-105">發行者原則檔會編譯成組件，並放置於全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="5e770-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>  
  
 <span data-ttu-id="5e770-106">建立發行者原則是三個步驟：</span><span class="sxs-lookup"><span data-stu-id="5e770-106">There are three steps involved in creating a publisher policy:</span></span>  
  
1.  <span data-ttu-id="5e770-107">建立發行者原則檔。</span><span class="sxs-lookup"><span data-stu-id="5e770-107">Create a publisher policy file.</span></span>  
  
2.  <span data-ttu-id="5e770-108">建立發行者原則組件。</span><span class="sxs-lookup"><span data-stu-id="5e770-108">Create a publisher policy assembly.</span></span>  
  
3.  <span data-ttu-id="5e770-109">將發行者原則組件新增至全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="5e770-109">Add the publisher policy assembly to the global assembly cache.</span></span>  
  
 <span data-ttu-id="5e770-110">發行者原則的結構描述所述[重新導向組件版本](../../../docs/framework/configure-apps/redirect-assembly-versions.md)。</span><span class="sxs-lookup"><span data-stu-id="5e770-110">The schema for publisher policy is described in [Redirecting Assembly Versions](../../../docs/framework/configure-apps/redirect-assembly-versions.md).</span></span> <span data-ttu-id="5e770-111">下列範例顯示發行者原則檔會將重新導向的一個版本`myAssembly`到另一個。</span><span class="sxs-lookup"><span data-stu-id="5e770-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->  
         <bindingRedirect oldVersion="1.0.0.0"  
                          newVersion="2.0.0.0"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="5e770-112">若要了解如何指定程式碼基底，請參閱[指定組件的位置](../../../docs/framework/configure-apps/specify-assembly-location.md)。</span><span class="sxs-lookup"><span data-stu-id="5e770-112">To learn how to specify a code base, see [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  
  
## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="5e770-113">建立發行者原則組件</span><span class="sxs-lookup"><span data-stu-id="5e770-113">Creating the Publisher Policy Assembly</span></span>  
 <span data-ttu-id="5e770-114">使用[組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md)建立發行者原則組件。</span><span class="sxs-lookup"><span data-stu-id="5e770-114">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>  
  
#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="5e770-115">若要建立發行者原則組件</span><span class="sxs-lookup"><span data-stu-id="5e770-115">To create a publisher policy assembly</span></span>  
  
1.  <span data-ttu-id="5e770-116">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="5e770-116">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="5e770-117">**al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span><span class="sxs-lookup"><span data-stu-id="5e770-117">**al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span></span>  
  
     <span data-ttu-id="5e770-118">在這個命令：</span><span class="sxs-lookup"><span data-stu-id="5e770-118">In this command:</span></span>  
  
    -   <span data-ttu-id="5e770-119">*PublisherPolicyFile*引數是發行者原則檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="5e770-119">The *publisherPolicyFile* argument is the name of the publisher policy file.</span></span>  
  
    -   <span data-ttu-id="5e770-120">*PublisherPolicyAssemblyFile*引數是此命令會產生發行者原則組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="5e770-120">The *publisherPolicyAssemblyFile* argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="5e770-121">組件檔案名稱必須遵循格式：</span><span class="sxs-lookup"><span data-stu-id="5e770-121">The assembly file name must follow the format:</span></span>  
  
         <span data-ttu-id="5e770-122">**原則。**</span><span class="sxs-lookup"><span data-stu-id="5e770-122">**policy.**</span></span> <span data-ttu-id="5e770-123">*majorNumber* **。**</span><span class="sxs-lookup"><span data-stu-id="5e770-123">*majorNumber* **.**</span></span> <span data-ttu-id="5e770-124">*minorNumber* **。**</span><span class="sxs-lookup"><span data-stu-id="5e770-124">*minorNumber* **.**</span></span> <span data-ttu-id="5e770-125">*mainAssemblyName* **.dll**</span><span class="sxs-lookup"><span data-stu-id="5e770-125">*mainAssemblyName* **.dll**</span></span>  
  
    -   <span data-ttu-id="5e770-126">*KeyPairFile*引數是含有金鑰組檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="5e770-126">The *keyPairFile* argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="5e770-127">您必須簽署的組件和相同的金鑰組的發行者原則組件。</span><span class="sxs-lookup"><span data-stu-id="5e770-127">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>  
  
    -   <span data-ttu-id="5e770-128">*ProcessorArchitecture*引數會識別特定處理器的組件的目標平台。</span><span class="sxs-lookup"><span data-stu-id="5e770-128">The *processorArchitecture* argument identifies the platform targeted by a processor-specific assembly.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5e770-129">能夠針對特定的處理器架構是.NET Framework 2.0 版中的新功能。</span><span class="sxs-lookup"><span data-stu-id="5e770-129">The ability to target a specific processor architecture is new in the .NET Framework version 2.0.</span></span>  
  
     <span data-ttu-id="5e770-130">下列命令會建立稱為發行者原則組件`policy.1.0.myAssembly`從發行者原則檔名`pub.config`，將強式名稱指派給使用中的金鑰組的組件`sgKey.snk`檔案，並指定組件以 x86 為目標處理器架構。</span><span class="sxs-lookup"><span data-stu-id="5e770-130">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     <span data-ttu-id="5e770-131">發行者原則組件必須符合的組件，它會套用到的處理器架構。</span><span class="sxs-lookup"><span data-stu-id="5e770-131">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="5e770-132">因此，如果您的組件<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A>的值<xref:System.Reflection.ProcessorArchitecture.MSIL>，必須使用建立發行者原則組件，該組件`/platform:anycpu`。</span><span class="sxs-lookup"><span data-stu-id="5e770-132">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="5e770-133">您必須提供個別針對每個處理器特定組件的發行者原則組件。</span><span class="sxs-lookup"><span data-stu-id="5e770-133">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>  
  
     <span data-ttu-id="5e770-134">此規則的結果是，若要變更組件的處理器架構，您必須變更的主要或次要的元件的版本號碼，以便您可以提供新的發行者原則組件，以正確的處理器架構。</span><span class="sxs-lookup"><span data-stu-id="5e770-134">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="5e770-135">一旦您的組件具有不同的處理器架構，將舊的發行者原則組件無法服務您的組件。</span><span class="sxs-lookup"><span data-stu-id="5e770-135">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>  
  
     <span data-ttu-id="5e770-136">另一種結果是 2.0 版連結器，不能用來建立編譯使用舊版.NET Framework 中，因為它一律會指定處理器架構的組件的發行者原則組件。</span><span class="sxs-lookup"><span data-stu-id="5e770-136">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="5e770-137">將發行者原則組件新增至全域組件快取</span><span class="sxs-lookup"><span data-stu-id="5e770-137">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>  
 <span data-ttu-id="5e770-138">使用[全域組件快取工具 (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)將發行者原則組件新增至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="5e770-138">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="5e770-139">將發行者原則組件新增至全域組件快取</span><span class="sxs-lookup"><span data-stu-id="5e770-139">To add the publisher policy assembly to the global assembly cache</span></span>  
  
1.  <span data-ttu-id="5e770-140">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="5e770-140">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="5e770-141">\**gacutil /i\*\*\*publisherPolicyAssemblyFile*</span><span class="sxs-lookup"><span data-stu-id="5e770-141">**gacutil /i**  *publisherPolicyAssemblyFile*</span></span>  
  
     <span data-ttu-id="5e770-142">下列命令會將`policy.1.0.myAssembly.dll`至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="5e770-142">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="5e770-143">發行者原則組件無法新增至全域組件快取，除非原始發行者原則檔位於與組件相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="5e770-143">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file is located in the same directory as the assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e770-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e770-144">See Also</span></span>  
 [<span data-ttu-id="5e770-145">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="5e770-145">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="5e770-146">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="5e770-146">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="5e770-147">設定應用程式</span><span class="sxs-lookup"><span data-stu-id="5e770-147">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)  
 [<span data-ttu-id="5e770-148">設定.NET Framework 應用程式</span><span class="sxs-lookup"><span data-stu-id="5e770-148">Configuring .NET Framework Apps</span></span>](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [<span data-ttu-id="5e770-149">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5e770-149">Runtime Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="5e770-150">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="5e770-150">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="5e770-151">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="5e770-151">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
