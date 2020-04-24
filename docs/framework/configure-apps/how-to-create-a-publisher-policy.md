---
title: 如何：建立發行者原則
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 7c36f6126f0d779a43a22fc11e647ba2d3b03a30
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646062"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="df4cc-102">如何：建立發行者原則</span><span class="sxs-lookup"><span data-stu-id="df4cc-102">How to: Create a Publisher Policy</span></span>

<span data-ttu-id="df4cc-103">程式集的供應商可以聲明應用程式應使用較新版本的程式集,通過將發佈者策略檔與升級的程式集一起。</span><span class="sxs-lookup"><span data-stu-id="df4cc-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="df4cc-104">發行者策略檔指定程式集重定向和代碼庫設置,並使用與應用程式設定檔相同的格式。</span><span class="sxs-lookup"><span data-stu-id="df4cc-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="df4cc-105">發行者策略檔編譯到程式集中並放置在全域程式集緩存中。</span><span class="sxs-lookup"><span data-stu-id="df4cc-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>

<span data-ttu-id="df4cc-106">建立發行者政策涉及三個步驟:</span><span class="sxs-lookup"><span data-stu-id="df4cc-106">There are three steps involved in creating a publisher policy:</span></span>

1. <span data-ttu-id="df4cc-107">建立發行者策略檔。</span><span class="sxs-lookup"><span data-stu-id="df4cc-107">Create a publisher policy file.</span></span>

2. <span data-ttu-id="df4cc-108">建立發行者策略程式集。</span><span class="sxs-lookup"><span data-stu-id="df4cc-108">Create a publisher policy assembly.</span></span>

3. <span data-ttu-id="df4cc-109">將發行者策略程式集添加到全域程式集緩存。</span><span class="sxs-lookup"><span data-stu-id="df4cc-109">Add the publisher policy assembly to the global assembly cache.</span></span>

<span data-ttu-id="df4cc-110">發行者策略的架構在[重定向程式集版本](redirect-assembly-versions.md)中描述。</span><span class="sxs-lookup"><span data-stu-id="df4cc-110">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="df4cc-111">下面的範例顯示一個發行者策略檔,該檔將一`myAssembly`個版本重定向到另一個版本。</span><span class="sxs-lookup"><span data-stu-id="df4cc-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>

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

<span data-ttu-id="df4cc-112">要瞭解如何指定程式庫,請參閱[指定程式集的位置](specify-assembly-location.md)。</span><span class="sxs-lookup"><span data-stu-id="df4cc-112">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>

## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="df4cc-113">建立發行者原則程式集</span><span class="sxs-lookup"><span data-stu-id="df4cc-113">Creating the Publisher Policy Assembly</span></span>

<span data-ttu-id="df4cc-114">使用[程式集連結器 (Al.exe)](../tools/al-exe-assembly-linker.md)建立發行者策略程式集。</span><span class="sxs-lookup"><span data-stu-id="df4cc-114">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>

#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="df4cc-115">建立發行者原則程式集</span><span class="sxs-lookup"><span data-stu-id="df4cc-115">To create a publisher policy assembly</span></span>

<span data-ttu-id="df4cc-116">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="df4cc-116">Type the following command at the command prompt:</span></span>

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

<span data-ttu-id="df4cc-117">在這個命令中：</span><span class="sxs-lookup"><span data-stu-id="df4cc-117">In this command:</span></span>

- <span data-ttu-id="df4cc-118">參數`publisherPolicyFile`是發布者策略檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="df4cc-118">The `publisherPolicyFile` argument is the name of the publisher policy file.</span></span>

- <span data-ttu-id="df4cc-119">該`publisherPolicyAssemblyFile`參數是此命令產生的發行者策略程式集的名稱。</span><span class="sxs-lookup"><span data-stu-id="df4cc-119">The `publisherPolicyAssemblyFile` argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="df4cc-120">程式集檔名稱必須遵循以下格式:</span><span class="sxs-lookup"><span data-stu-id="df4cc-120">The assembly file name must follow the format:</span></span>

  <span data-ttu-id="df4cc-121">"策略.主要編號.次要編號.mainAssemblyname.dll"</span><span class="sxs-lookup"><span data-stu-id="df4cc-121">\`policy.majorNumber.minorNumber.mainAssemblyName.dll'</span></span>

- <span data-ttu-id="df4cc-122">參數`keyPairFile`是包含金鑰對的檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="df4cc-122">The `keyPairFile` argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="df4cc-123">您必須使用相同的金鑰對對程式集和發行者策略程式集進行簽名。</span><span class="sxs-lookup"><span data-stu-id="df4cc-123">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>

- <span data-ttu-id="df4cc-124">參數`processorArchitecture`標識處理器特定程式集的目標平臺。</span><span class="sxs-lookup"><span data-stu-id="df4cc-124">The `processorArchitecture` argument identifies the platform targeted by a processor-specific assembly.</span></span>

  > [!NOTE]
  > <span data-ttu-id="df4cc-125">從 .NET 框架 2.0 開始,可以定位特定處理器體系結構。</span><span class="sxs-lookup"><span data-stu-id="df4cc-125">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span>

<span data-ttu-id="df4cc-126">從 .NET 框架 2.0 開始,可以定位特定處理器體系結構。</span><span class="sxs-lookup"><span data-stu-id="df4cc-126">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span> <span data-ttu-id="df4cc-127">以下命令創建一個發佈者策略程式集`policy.1.0.myAssembly`,該程式集從稱為`pub.config`的 發行者策略檔調用`sgKey.snk`,使用 檔中的密鑰對向程式集分配強名稱,並指定程式集以 x86 處理器體系結構為目標。</span><span class="sxs-lookup"><span data-stu-id="df4cc-127">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

<span data-ttu-id="df4cc-128">發行者策略程式集必須與它所應用的程式集的處理器體系結構匹配。</span><span class="sxs-lookup"><span data-stu-id="df4cc-128">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="df4cc-129">因此,如果程式集的值<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A>為<xref:System.Reflection.ProcessorArchitecture.MSIL>`/platform:anycpu`</span><span class="sxs-lookup"><span data-stu-id="df4cc-129">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="df4cc-130">您必須為每個特定於處理器的程式集提供單獨的發行者策略程式集。</span><span class="sxs-lookup"><span data-stu-id="df4cc-130">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>

<span data-ttu-id="df4cc-131">此規則的結果是,為了更改程式集的處理器體系結構,必須更改版本號的主要或次要元件,以便可以使用正確的處理器體系結構提供新的發行者策略程式集。</span><span class="sxs-lookup"><span data-stu-id="df4cc-131">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="df4cc-132">一旦程式集具有不同的處理器體系結構,舊的發行者策略程式集將無法為程式集提供服務。</span><span class="sxs-lookup"><span data-stu-id="df4cc-132">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>

<span data-ttu-id="df4cc-133">另一個後果是,版本 2.0 連結器不能用於為使用早期版本的 .NET Framework 編譯的程式集創建發行者策略程式集,因為它始終指定處理器體系結構。</span><span class="sxs-lookup"><span data-stu-id="df4cc-133">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="df4cc-134">將宣告者政策程式集到全域程式集快取</span><span class="sxs-lookup"><span data-stu-id="df4cc-134">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>

<span data-ttu-id="df4cc-135">使用[全域程式集快取工具 (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md)將發布者策略程式集添加到全域程式集緩存。</span><span class="sxs-lookup"><span data-stu-id="df4cc-135">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="df4cc-136">將宣告者政策程式集到全域程式集快取</span><span class="sxs-lookup"><span data-stu-id="df4cc-136">To add the publisher policy assembly to the global assembly cache</span></span>

<span data-ttu-id="df4cc-137">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="df4cc-137">Type the following command at the command prompt:</span></span>

```console
gacutil /i publisherPolicyAssemblyFile
```

<span data-ttu-id="df4cc-138">以下命令添加到`policy.1.0.myAssembly.dll`全域程式集緩存。</span><span class="sxs-lookup"><span data-stu-id="df4cc-138">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> <span data-ttu-id="df4cc-139">除非`/link`參數中指定的原始發行者策略檔與程式集位於同一目錄中,否則無法將發行者策略程式集添加到全域程式集緩存中。</span><span class="sxs-lookup"><span data-stu-id="df4cc-139">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file specified in the `/link` argument is located in the same directory as the assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="df4cc-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df4cc-140">See also</span></span>

- [<span data-ttu-id="df4cc-141">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="df4cc-141">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="df4cc-142">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="df4cc-142">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="df4cc-143">使用組態檔設定應用程式</span><span class="sxs-lookup"><span data-stu-id="df4cc-143">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="df4cc-144">執行時設定架構</span><span class="sxs-lookup"><span data-stu-id="df4cc-144">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="df4cc-145">設定檔案架構</span><span class="sxs-lookup"><span data-stu-id="df4cc-145">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="df4cc-146">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="df4cc-146">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
