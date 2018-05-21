---
title: 延遲簽署組件
ms.date: 07/31/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4457bd6d5efd7404cdba6c5fbdbffa9f9eb62141
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="delay-signing-an-assembly"></a><span data-ttu-id="c12eb-102">延遲簽署組件</span><span class="sxs-lookup"><span data-stu-id="c12eb-102">Delay Signing an Assembly</span></span>
<span data-ttu-id="c12eb-103">組織可能會有開發人員無法每日存取的嚴密保護金鑰組。</span><span class="sxs-lookup"><span data-stu-id="c12eb-103">An organization can have a closely guarded key pair that developers do not have access to on a daily basis.</span></span> <span data-ttu-id="c12eb-104">公開金鑰經常都可以使用，但只有少數人才能存取私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="c12eb-104">The public key is often available, but access to the private key is restricted to only a few individuals.</span></span> <span data-ttu-id="c12eb-105">在以強式名稱開發組件時，每個參考強式名稱目標組件的組件都包含用來指定目標組件的強式名稱的公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c12eb-105">When developing assemblies with strong names, each assembly that references the strong-named target assembly contains the token of the public key used to give the target assembly a strong name.</span></span> <span data-ttu-id="c12eb-106">這需要可在開發程序期間使用公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="c12eb-106">This requires that the public key be available during the development process.</span></span>  
  
 <span data-ttu-id="c12eb-107">您可以在建置階段中使用延遲或部分簽署，以便在可攜式執行檔 (PE) 中保留強式名稱簽章的空間，但延後到之後的某個階段 (通常是就在傳送組件之前) 才實際簽署。</span><span class="sxs-lookup"><span data-stu-id="c12eb-107">You can use delayed or partial signing at build time to reserve space in the portable executable (PE) file for the strong name signature, but defer the actual signing until some later stage (typically just before shipping the assembly).</span></span>  
  
 <span data-ttu-id="c12eb-108">下列步驟概述延遲簽署組件的程序：</span><span class="sxs-lookup"><span data-stu-id="c12eb-108">The following steps outline the process to delay sign an assembly:</span></span>  
  
1.  <span data-ttu-id="c12eb-109">從將執行最終簽署的組織取得金鑰組的公開金鑰部分。</span><span class="sxs-lookup"><span data-stu-id="c12eb-109">Obtain the public key portion of the key pair from the organization that will do the eventual signing.</span></span> <span data-ttu-id="c12eb-110">此金鑰通常格式為 .snk 檔案，這可以使用 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 提供的[強式名稱工具 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)建立。</span><span class="sxs-lookup"><span data-stu-id="c12eb-110">Typically this key is in the form of an .snk file, which can be created using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
2.  <span data-ttu-id="c12eb-111">使用來自 <xref:System.Reflection> 的兩個自訂屬性為組件的原始碼加上註解：</span><span class="sxs-lookup"><span data-stu-id="c12eb-111">Annotate the source code for the assembly with two custom attributes from <xref:System.Reflection>:</span></span>  
  
    -   <span data-ttu-id="c12eb-112"><xref:System.Reflection.AssemblyKeyFileAttribute>，它會將傳遞包含公開金鑰的檔案名稱，作為其建構函式的參數。</span><span class="sxs-lookup"><span data-stu-id="c12eb-112"><xref:System.Reflection.AssemblyKeyFileAttribute>, which passes the name of the file containing the public key as a parameter to its constructor.</span></span>  
  
    -   <span data-ttu-id="c12eb-113"><xref:System.Reflection.AssemblyDelaySignAttribute>，它指出正在藉由傳遞 **true** 作為其建構函式的參數來使用延遲簽署。</span><span class="sxs-lookup"><span data-stu-id="c12eb-113"><xref:System.Reflection.AssemblyDelaySignAttribute>, which indicates that delay signing is being used by passing **true** as a parameter to its constructor.</span></span> <span data-ttu-id="c12eb-114">例如: </span><span class="sxs-lookup"><span data-stu-id="c12eb-114">For example:</span></span>  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3.  <span data-ttu-id="c12eb-115">編譯器會將公開金鑰插入到組件資訊清單，並在 PE 檔中保留完整強式名稱簽章的空間。</span><span class="sxs-lookup"><span data-stu-id="c12eb-115">The compiler inserts the public key into the assembly manifest and reserves space in the PE file for the full strong name signature.</span></span> <span data-ttu-id="c12eb-116">在建置組件時必須儲存真正的公開金鑰，以便參考這個組件的其他組件可以取得金鑰，儲存在它們自己的組件參考。</span><span class="sxs-lookup"><span data-stu-id="c12eb-116">The real public key must be stored while the assembly is built so that other assemblies that reference this assembly can obtain the key to store in their own assembly reference.</span></span>  
  
4.  <span data-ttu-id="c12eb-117">因為組件沒有有效的強式名稱簽章，所以該簽章的驗證作業必須關閉。</span><span class="sxs-lookup"><span data-stu-id="c12eb-117">Because the assembly does not have a valid strong name signature, the verification of that signature must be turned off.</span></span> <span data-ttu-id="c12eb-118">您可以使用 **-Vr** 選項搭配強式名稱工具完成此作業。</span><span class="sxs-lookup"><span data-stu-id="c12eb-118">You can do this by using the **–Vr** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="c12eb-119">下列範例會關閉 `myAssembly.dll` 組件的驗證。</span><span class="sxs-lookup"><span data-stu-id="c12eb-119">The following example turns off verification for an assembly called `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     <span data-ttu-id="c12eb-120">若要在您無法在執行強式名稱工具的平台上關閉驗證，例如 Advanced RISC Machine (ARM) 微處理器，請使用 **– Vk** 選項來建立登錄檔。</span><span class="sxs-lookup"><span data-stu-id="c12eb-120">To turn off verification on platforms where you can’t run the Strong Name tool, such as Advanced RISC Machine (ARM) microprocessors, use the **–Vk** option to create a registry file.</span></span> <span data-ttu-id="c12eb-121">將登錄檔匯入到您要關閉驗證的電腦上的登錄。</span><span class="sxs-lookup"><span data-stu-id="c12eb-121">Import the registry file into the registry on the computer where you want to turn off verification.</span></span> <span data-ttu-id="c12eb-122">下列範例將建立 `myAssembly.dll` 的登錄檔。</span><span class="sxs-lookup"><span data-stu-id="c12eb-122">The following example creates a registry file for `myAssembly.dll`.</span></span>  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     <span data-ttu-id="c12eb-123">使用 **-Vr** 或 **– Vk** 選項時，您可以選擇性地包含測試金鑰簽署的 .snk 檔案。</span><span class="sxs-lookup"><span data-stu-id="c12eb-123">With either the **–Vr** or **–Vk** option, you can optionally include an .snk file for test key signing.</span></span>  
  
    > [!WARNING]
    > <span data-ttu-id="c12eb-124">請勿依賴強式名稱提供安全性。</span><span class="sxs-lookup"><span data-stu-id="c12eb-124">Do not rely on strong names for security.</span></span> <span data-ttu-id="c12eb-125">強式名稱僅提供唯一識別。</span><span class="sxs-lookup"><span data-stu-id="c12eb-125">They provide a unique identity only.</span></span>
  
    > [!NOTE]
    >  <span data-ttu-id="c12eb-126">如果您在 64 位元電腦上，使用 Visual Studio 進行開發期間使用延遲簽署，並且編譯**任何 CPU** 的組件，您可能要套用 **-Vr** 選項兩次。</span><span class="sxs-lookup"><span data-stu-id="c12eb-126">If you use delay signing during development with Visual Studio on a 64-bit computer, and you compile an assembly for **Any CPU**, you might have to apply the **-Vr** option twice.</span></span> <span data-ttu-id="c12eb-127">(在 Visual Studio 中，**任何 CPU** 是**平台目標**建置屬性的值，當您從命令列編譯時，它是預設值。)若要從命令列或檔案總管執行您的應用程式，請使用 64 位元版本的 [Sn.exe (強式名稱工具)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) 套用 **-Vr** 選項給組件。</span><span class="sxs-lookup"><span data-stu-id="c12eb-127">(In Visual Studio, **Any CPU** is a value of the **Platform Target** build property; when you compile from the command line, it is the default.) To run your application from the command line or from File Explorer, use the 64-bit version of the [Sn.exe (Strong Name Tool)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) to apply the **-Vr** option to the assembly.</span></span> <span data-ttu-id="c12eb-128">若要在設計階段將組件載入到 Visual Studio (例如，如果組件包含您應用程式中其他組件使用的元件)，請使用 32 位元版本的強式名稱工具。</span><span class="sxs-lookup"><span data-stu-id="c12eb-128">To load the assembly into Visual Studio at design time (for example, if the assembly contains components that are used by other assemblies in your application), use the 32-bit version of the strong-name tool.</span></span> <span data-ttu-id="c12eb-129">這是因為當組件是從命令列執行時，just-in-time (JIT) 編譯器會將組件編譯為 64 位元原生程式碼，而當載入到設計階段環境時，編譯為 32 位元原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="c12eb-129">This is because the just-in-time (JIT) compiler compiles the assembly to 64-bit native code when the assembly is run from the command line, and to 32-bit native code when the assembly is loaded into the design-time environment.</span></span>  
  
5.  <span data-ttu-id="c12eb-130">稍後，通常就在傳送之前，您會將組件送出給貴組織的簽署授權單位，以便使用強式名稱工具的 **–R** 選項進行實際的強式名稱簽署。</span><span class="sxs-lookup"><span data-stu-id="c12eb-130">Later, usually just before shipping, you submit the assembly to your organization's signing authority for the actual strong name signing using the **–R** option with the Strong Name tool.</span></span>  
  
     <span data-ttu-id="c12eb-131">下列範例會使用 `myAssembly.dll` 金鑰組，將組件 `sgKey.snk` 簽署為強式名稱。</span><span class="sxs-lookup"><span data-stu-id="c12eb-131">The following example signs an assembly called `myAssembly.dll` with a strong name using the `sgKey.snk` key pair.</span></span>  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c12eb-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="c12eb-132">See Also</span></span>  
 [<span data-ttu-id="c12eb-133">建立組件</span><span class="sxs-lookup"><span data-stu-id="c12eb-133">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="c12eb-134">如何：建立公開/私密金鑰組</span><span class="sxs-lookup"><span data-stu-id="c12eb-134">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [<span data-ttu-id="c12eb-135">Sn.exe (強式名稱工具)</span><span class="sxs-lookup"><span data-stu-id="c12eb-135">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [<span data-ttu-id="c12eb-136">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="c12eb-136">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
