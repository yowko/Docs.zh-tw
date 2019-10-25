---
title: 如何：建立發行者原則
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 608918828bf72369a1bd48e2391e2423078e9df0
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846842"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="fd08c-102">如何：建立發行者原則</span><span class="sxs-lookup"><span data-stu-id="fd08c-102">How to: Create a Publisher Policy</span></span>

<span data-ttu-id="fd08c-103">元件的廠商可以指出應用程式應該使用較新版本的元件，方法是包含發行者原則檔案與已升級的元件。</span><span class="sxs-lookup"><span data-stu-id="fd08c-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="fd08c-104">發行者原則檔會指定元件重新導向和程式碼基底設定，並使用與應用程式佈建檔相同的格式。</span><span class="sxs-lookup"><span data-stu-id="fd08c-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="fd08c-105">發行者原則檔會編譯成元件，並放在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="fd08c-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>

<span data-ttu-id="fd08c-106">建立發行者原則包含三個步驟：</span><span class="sxs-lookup"><span data-stu-id="fd08c-106">There are three steps involved in creating a publisher policy:</span></span>

1. <span data-ttu-id="fd08c-107">建立發行者原則檔。</span><span class="sxs-lookup"><span data-stu-id="fd08c-107">Create a publisher policy file.</span></span>

2. <span data-ttu-id="fd08c-108">建立發行者原則元件。</span><span class="sxs-lookup"><span data-stu-id="fd08c-108">Create a publisher policy assembly.</span></span>

3. <span data-ttu-id="fd08c-109">將發行者原則元件加入至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="fd08c-109">Add the publisher policy assembly to the global assembly cache.</span></span>

<span data-ttu-id="fd08c-110">重新導向[元件版本](redirect-assembly-versions.md)中會描述發行者原則的架構。</span><span class="sxs-lookup"><span data-stu-id="fd08c-110">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="fd08c-111">下列範例顯示將一個 `myAssembly` 版本重新導向至另一個版本的發行者原則檔。</span><span class="sxs-lookup"><span data-stu-id="fd08c-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>

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

<span data-ttu-id="fd08c-112">若要瞭解如何指定程式碼基底，請參閱[指定元件的位置](specify-assembly-location.md)。</span><span class="sxs-lookup"><span data-stu-id="fd08c-112">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>

## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="fd08c-113">建立發行者原則元件</span><span class="sxs-lookup"><span data-stu-id="fd08c-113">Creating the Publisher Policy Assembly</span></span>

<span data-ttu-id="fd08c-114">使用[元件連結器（al.exe）](../tools/al-exe-assembly-linker.md)來建立發行者原則元件。</span><span class="sxs-lookup"><span data-stu-id="fd08c-114">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>

#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="fd08c-115">若要建立發行者原則元件</span><span class="sxs-lookup"><span data-stu-id="fd08c-115">To create a publisher policy assembly</span></span>

<span data-ttu-id="fd08c-116">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="fd08c-116">Type the following command at the command prompt:</span></span>

<span data-ttu-id="fd08c-117">**al/link：** *publisherPolicyFile* **/Out：** *publisherPolicyAssemblyFile* **/keyfile：** *keyPairFile* **/platform：** *processorArchitecture*</span><span class="sxs-lookup"><span data-stu-id="fd08c-117">**al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span></span>

<span data-ttu-id="fd08c-118">在此命令中：</span><span class="sxs-lookup"><span data-stu-id="fd08c-118">In this command:</span></span>

- <span data-ttu-id="fd08c-119">*PublisherPolicyFile*引數是發行者原則檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="fd08c-119">The *publisherPolicyFile* argument is the name of the publisher policy file.</span></span>

- <span data-ttu-id="fd08c-120">*PublisherPolicyAssemblyFile*引數是此命令所產生之發行者原則元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="fd08c-120">The *publisherPolicyAssemblyFile* argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="fd08c-121">元件檔案名的格式必須如下：</span><span class="sxs-lookup"><span data-stu-id="fd08c-121">The assembly file name must follow the format:</span></span>

  <span data-ttu-id="fd08c-122">**策略.**</span><span class="sxs-lookup"><span data-stu-id="fd08c-122">**policy.**</span></span> <span data-ttu-id="fd08c-123">*majorNumber* **。**</span><span class="sxs-lookup"><span data-stu-id="fd08c-123">*majorNumber* **.**</span></span> <span data-ttu-id="fd08c-124">*minorNumber* **。**</span><span class="sxs-lookup"><span data-stu-id="fd08c-124">*minorNumber* **.**</span></span> <span data-ttu-id="fd08c-125">*mainAssemblyName* **.dll**</span><span class="sxs-lookup"><span data-stu-id="fd08c-125">*mainAssemblyName* **.dll**</span></span>

- <span data-ttu-id="fd08c-126">*KeyPairFile*引數是包含金鑰組的檔案名。</span><span class="sxs-lookup"><span data-stu-id="fd08c-126">The *keyPairFile* argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="fd08c-127">您必須使用相同的金鑰組來簽署元件和發行者原則元件。</span><span class="sxs-lookup"><span data-stu-id="fd08c-127">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>

- <span data-ttu-id="fd08c-128">*ProcessorArchitecture*引數會識別特定處理器元件的目標平臺。</span><span class="sxs-lookup"><span data-stu-id="fd08c-128">The *processorArchitecture* argument identifies the platform targeted by a processor-specific assembly.</span></span>

  > [!NOTE]
  > <span data-ttu-id="fd08c-129">從 .NET Framework 2.0 開始，可以取得以特定處理器架構為目標的功能。</span><span class="sxs-lookup"><span data-stu-id="fd08c-129">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span>

<span data-ttu-id="fd08c-130">從 .NET Framework 2.0 開始，可以取得以特定處理器架構為目標的功能。</span><span class="sxs-lookup"><span data-stu-id="fd08c-130">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span> <span data-ttu-id="fd08c-131">下列命令會從名為 `pub.config`的發行者原則檔案建立名為 `policy.1.0.myAssembly` 的發行者原則元件，並使用 `sgKey.snk` 檔案中的金鑰組，將強式名稱指派給元件，並指定元件以 x86 處理器為目標結構.</span><span class="sxs-lookup"><span data-stu-id="fd08c-131">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>

```
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

<span data-ttu-id="fd08c-132">發行者原則元件必須符合其適用之元件的處理器架構。</span><span class="sxs-lookup"><span data-stu-id="fd08c-132">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="fd08c-133">因此，如果您的元件具有 <xref:System.Reflection.ProcessorArchitecture.MSIL>的 <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> 值，則必須使用 `/platform:anycpu`來建立該元件的發行者原則元件。</span><span class="sxs-lookup"><span data-stu-id="fd08c-133">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="fd08c-134">您必須為每個處理器特定的元件提供個別的發行者原則元件。</span><span class="sxs-lookup"><span data-stu-id="fd08c-134">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>

<span data-ttu-id="fd08c-135">這項規則的結果是，若要變更元件的處理器架構，您必須變更版本號碼的主要或次要元件，讓您可以使用正確的處理器架構來提供新的發行者原則元件。</span><span class="sxs-lookup"><span data-stu-id="fd08c-135">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="fd08c-136">當您的元件有不同的處理器架構時，舊的發行者原則元件無法服務您的元件。</span><span class="sxs-lookup"><span data-stu-id="fd08c-136">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>

<span data-ttu-id="fd08c-137">另一個結果是版本2.0 連結器無法用來建立使用舊版 .NET Framework 所編譯之元件的發行者原則元件，因為它一律會指定處理器架構。</span><span class="sxs-lookup"><span data-stu-id="fd08c-137">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="fd08c-138">將發行者原則元件加入至全域組件快取</span><span class="sxs-lookup"><span data-stu-id="fd08c-138">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>

<span data-ttu-id="fd08c-139">使用[全域組件快取工具（Gacutil）](../tools/gacutil-exe-gac-tool.md) ，將發行者原則元件加入至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="fd08c-139">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="fd08c-140">將發行者原則元件加入至全域組件快取</span><span class="sxs-lookup"><span data-stu-id="fd08c-140">To add the publisher policy assembly to the global assembly cache</span></span>

<span data-ttu-id="fd08c-141">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="fd08c-141">Type the following command at the command prompt:</span></span>

<span data-ttu-id="fd08c-142">**gacutil/I**  *publisherPolicyAssemblyFile*</span><span class="sxs-lookup"><span data-stu-id="fd08c-142">**gacutil /i**  *publisherPolicyAssemblyFile*</span></span>

<span data-ttu-id="fd08c-143">下列命令會將 `policy.1.0.myAssembly.dll` 新增至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="fd08c-143">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>

```
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> <span data-ttu-id="fd08c-144">發行者原則元件無法加入至全域組件快取，除非原始發行者原則檔位於與元件相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="fd08c-144">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file is located in the same directory as the assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd08c-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="fd08c-145">See also</span></span>

- [<span data-ttu-id="fd08c-146">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="fd08c-146">Programming with Assemblies</span></span>](../../standard/assembly/program.md)
- [<span data-ttu-id="fd08c-147">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="fd08c-147">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="fd08c-148">使用設定檔設定應用程式</span><span class="sxs-lookup"><span data-stu-id="fd08c-148">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="fd08c-149">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="fd08c-149">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="fd08c-150">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="fd08c-150">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="fd08c-151">重新導向組件版本</span><span class="sxs-lookup"><span data-stu-id="fd08c-151">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
