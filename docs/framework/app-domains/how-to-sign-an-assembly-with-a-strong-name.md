---
title: 如何：使用強式名稱簽署組件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45f8ad3bd9226ffd821fc792cdd4d0a6dac1a414
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744625"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="fe9a3-102">如何：使用強式名稱簽署組件</span><span class="sxs-lookup"><span data-stu-id="fe9a3-102">How to: Sign an Assembly with a Strong Name</span></span>
<span data-ttu-id="fe9a3-103">以下是幾種以強式名稱簽署組件的方式：</span><span class="sxs-lookup"><span data-stu-id="fe9a3-103">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
-   <span data-ttu-id="fe9a3-104">使用 Visual Studio 中，專案之 [ **屬性** ] 對話方塊中的 [ **簽署** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-104">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="fe9a3-105">這是最簡單、最方便以強式名稱簽署組件的方式。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-105">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
-   <span data-ttu-id="fe9a3-106">透過使用 [組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將 .NET Framework 程式碼模組 (.netmodule 檔) 與金鑰檔連結在一起。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-106">By using the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a .netmodule file) with a key file.</span></span>  
  
-   <span data-ttu-id="fe9a3-107">使用組件屬性將強式名稱資訊插入您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-107">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="fe9a3-108">您可以使用 <xref:System.Reflection.AssemblyKeyFileAttribute> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 屬性，視使用的金鑰檔所在位置而定。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-108">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
-   <span data-ttu-id="fe9a3-109">使用編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-109">By using compiler options.</span></span>  
  
 <span data-ttu-id="fe9a3-110">您必須使用密碼編譯金鑰組將組件簽署為強式名稱。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-110">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="fe9a3-111">如需建立金鑰組 (Key Pair) 的詳細資訊，請參閱[如何：建立公開/私密金鑰組](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-111">For more information about creating a key pair, see [How to: Create a Public-Private Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="fe9a3-112">若要使用 Visual Studio 建立組件並以強式名稱簽署組件</span><span class="sxs-lookup"><span data-stu-id="fe9a3-112">To create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1.  <span data-ttu-id="fe9a3-113">在 **方案總管**中，開啟專案的捷徑功能表，然後選擇 [屬性] 。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-113">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="fe9a3-114">選擇 [ **簽署** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-114">Choose the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="fe9a3-115">選取 [簽署組件] 方塊。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-115">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="fe9a3-116">在 [選擇強式名稱金鑰檔] 方塊中，選擇 [\<瀏覽...>]，然後巡覽至金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-116">In the **Choose a strong name key file** box, choose **\<Browse…>**, and then navigate to the key file.</span></span> <span data-ttu-id="fe9a3-117">若要建立新的金鑰檔，請選擇 [\<新增...>]，並且在 [建立強式名稱金鑰] 對話方塊中輸入其名稱。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-117">To create a new key file, choose **\<New…>** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="fe9a3-118">若要使用組件連結器建立組件並以強式名稱簽署組件</span><span class="sxs-lookup"><span data-stu-id="fe9a3-118">To create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
-   <span data-ttu-id="fe9a3-119">在 [Visual Studio 命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="fe9a3-119">At the [Visual Studio Command Prompt](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="fe9a3-120">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span><span class="sxs-lookup"><span data-stu-id="fe9a3-120">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  
  
     <span data-ttu-id="fe9a3-121">其中：</span><span class="sxs-lookup"><span data-stu-id="fe9a3-121">where:</span></span>  
  
     <span data-ttu-id="fe9a3-122">*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="fe9a3-122">*assemblyName*</span></span>  
     <span data-ttu-id="fe9a3-123">組件連結器將發出的強式簽署組件名稱 (.dll 或 .exe 檔)。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-123">The name of the strongly signed assembly (a .dll or .exe file) that Assembly Linker will emit.</span></span>  
  
     <span data-ttu-id="fe9a3-124">*moduleName*</span><span class="sxs-lookup"><span data-stu-id="fe9a3-124">*moduleName*</span></span>  
     <span data-ttu-id="fe9a3-125">.NET Framework 程式碼模組 (.netmodule 檔) 的名稱，其中包括一或多個類型。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-125">The name of a .NET Framework code module (a .netmodule file) that includes one or more types.</span></span> <span data-ttu-id="fe9a3-126">您可以在 C# 或 Visual Basic 中使用 `/target:module` 參數編譯程式碼，藉此建立 .netmodule 檔。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-126">You can create a .netmodule file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>  
  
     <span data-ttu-id="fe9a3-127">*keyfileName*</span><span class="sxs-lookup"><span data-stu-id="fe9a3-127">*keyfileName*</span></span>  
     <span data-ttu-id="fe9a3-128">包含金鑰組之容器或檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-128">The name of the container or file that contains the key pair.</span></span> <span data-ttu-id="fe9a3-129">組件連結器會解譯與目前目錄相關的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-129">Assembly Linker interprets a relative path in relationship to the current directory.</span></span>  
  
 <span data-ttu-id="fe9a3-130">下列範例將使用金鑰檔 `MyAssembly.dll` 以強式名稱簽署組件 `sgKey.snk`。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-130">The following example signs the assembly `MyAssembly.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 <span data-ttu-id="fe9a3-131">如需這項工具的詳細資訊，請參閱 [組件連結器](../../../docs/framework/tools/al-exe-assembly-linker.md)。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-131">For more information about this tool, see [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="fe9a3-132">若要使用屬性以強式名稱簽署組件</span><span class="sxs-lookup"><span data-stu-id="fe9a3-132">To sign an assembly with a strong name by using attributes</span></span>  
  
1.  <span data-ttu-id="fe9a3-133">將 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 屬性加入至您的原始程式碼檔，並指定容器或檔案名稱，其中包含以強式名稱簽署組件時所使用的金鑰組。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-133">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  
  
2.  <span data-ttu-id="fe9a3-134">以一般方式編譯原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-134">Compile the source code file normally.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe9a3-135">C# 和 Visual Basic 編譯器在原始程式碼中遇到 <xref:System.Reflection.AssemblyKeyFileAttribute> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 屬性時，會發出編譯器警告 (分別為 CS1699 和 BC41008)。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-135">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="fe9a3-136">您可以忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-136">You can ignore the warnings.</span></span>  
  
 <span data-ttu-id="fe9a3-137">下列範例將搭配稱為 <xref:System.Reflection.AssemblyKeyFileAttribute> 的金鑰檔使用 `keyfile.snk`屬性，這個金鑰檔位於編譯組件所在的目錄中。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-137">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called `keyfile.snk`, which is located in the directory where the assembly is compiled.</span></span>  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 <span data-ttu-id="fe9a3-138">您也可以在編譯原始程式檔時延遲簽署組件。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-138">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="fe9a3-139">如需詳細資訊，請參閱 [延遲簽署組件](../../../docs/framework/app-domains/delay-sign-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-139">For more information, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="fe9a3-140">若要使用編譯器以強式名稱簽署組件</span><span class="sxs-lookup"><span data-stu-id="fe9a3-140">To sign an assembly with a strong name by using the compiler</span></span>  
  
-   <span data-ttu-id="fe9a3-141">在 C# 和 Visual Basic 中使用 `/keyfile` 或 `/delaysign` 編譯器選項，或是在 C++ 中使用 `/KEYFILE` 或 `/DELAYSIGN` 連結器選項編譯原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-141">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="fe9a3-142">在選項名稱後面加上冒號和金鑰檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-142">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="fe9a3-143">使用命令列編譯器時，您可以將金鑰檔複製到包含您的原始程式碼檔的目錄中。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-143">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  
  
     <span data-ttu-id="fe9a3-144">如需延遲簽署的詳細資訊，請參閱 [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-144">For information on delay signing, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
     <span data-ttu-id="fe9a3-145">下列範例將使用 C# 編譯器，並且使用金鑰檔 `UtilityLibrary.dll` 以強式名稱簽署 `sgKey.snk` 組件。</span><span class="sxs-lookup"><span data-stu-id="fe9a3-145">The following example uses the C# compiler and signs the assembly `UtilityLibrary.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fe9a3-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe9a3-146">See Also</span></span>  
 [<span data-ttu-id="fe9a3-147">建立和使用強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="fe9a3-147">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [<span data-ttu-id="fe9a3-148">如何：建立公開/私密金鑰組</span><span class="sxs-lookup"><span data-stu-id="fe9a3-148">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [<span data-ttu-id="fe9a3-149">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="fe9a3-149">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [<span data-ttu-id="fe9a3-150">延遲簽署組件</span><span class="sxs-lookup"><span data-stu-id="fe9a3-150">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 [<span data-ttu-id="fe9a3-151">管理組件和資訊清單簽署</span><span class="sxs-lookup"><span data-stu-id="fe9a3-151">Managing Assembly and Manifest Signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)  
 [<span data-ttu-id="fe9a3-152">專案設計工具、簽署頁面</span><span class="sxs-lookup"><span data-stu-id="fe9a3-152">Signing Page, Project Designer</span></span>](https://msdn.microsoft.com/library/0k50fs3b)
