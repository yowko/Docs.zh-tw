---
title: 如何：使用強式名稱簽署元件
description: 本文說明如何使用 [簽署] 索引標籤、元件連結器、元件屬性或編譯器選項，以強式名稱簽署 .NET 元件。
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET], signing
- assemblies [.NET], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 5192f7f372b9ef7927930c3599aebc6fca9f1f0f
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687657"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="bb44a-103">如何：使用強式名稱簽署元件</span><span class="sxs-lookup"><span data-stu-id="bb44a-103">How to: Sign an assembly with a strong name</span></span>

> [!NOTE]
> <span data-ttu-id="bb44a-104">雖然 .NET Core 支援強式名稱的元件，以及 .NET Core 程式庫中的所有元件都已簽署，但大部分的協力廠商元件都不需要強名稱。</span><span class="sxs-lookup"><span data-stu-id="bb44a-104">Although .NET Core supports strong-named assemblies, and all assemblies in the .NET Core library are signed, the majority of third-party assemblies do not need strong names.</span></span> <span data-ttu-id="bb44a-105">如需詳細資訊，請參閱 GitHub 上的 [強式名稱簽署](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) 。</span><span class="sxs-lookup"><span data-stu-id="bb44a-105">For more information, see [Strong Name Signing](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) on GitHub.</span></span>

<span data-ttu-id="bb44a-106">以下是幾種以強式名稱簽署組件的方式：</span><span class="sxs-lookup"><span data-stu-id="bb44a-106">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
- <span data-ttu-id="bb44a-107">使用 Visual Studio 中，專案之 [ **屬性** ] 對話方塊中的 [ **簽署** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bb44a-107">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="bb44a-108">這是最簡單、最方便以強式名稱簽署組件的方式。</span><span class="sxs-lookup"><span data-stu-id="bb44a-108">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
- <span data-ttu-id="bb44a-109">藉由使用 [元件連結器 ( # A0)](../../framework/tools/al-exe-assembly-linker.md) 將 .NET Framework 程式碼模組與金鑰檔) 連結 ( *.netmodule* 檔。</span><span class="sxs-lookup"><span data-stu-id="bb44a-109">By using the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a *.netmodule* file) with a key file.</span></span>  
  
- <span data-ttu-id="bb44a-110">使用組件屬性將強式名稱資訊插入您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bb44a-110">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="bb44a-111">您可以使用 <xref:System.Reflection.AssemblyKeyFileAttribute> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 屬性，視使用的金鑰檔所在位置而定。</span><span class="sxs-lookup"><span data-stu-id="bb44a-111">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
- <span data-ttu-id="bb44a-112">使用編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="bb44a-112">By using compiler options.</span></span>  
  
 <span data-ttu-id="bb44a-113">您必須使用密碼編譯金鑰組將組件簽署為強式名稱。</span><span class="sxs-lookup"><span data-stu-id="bb44a-113">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="bb44a-114">如需建立金鑰組的詳細資訊，請參閱 [如何：建立公開/私密金鑰](create-public-private-key-pair.md)組。</span><span class="sxs-lookup"><span data-stu-id="bb44a-114">For more information about creating a key pair, see [How to: Create a public-private key pair](create-public-private-key-pair.md).</span></span>  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="bb44a-115">使用 Visual Studio 建立元件並以強式名稱簽署元件</span><span class="sxs-lookup"><span data-stu-id="bb44a-115">Create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="bb44a-116">在  。</span><span class="sxs-lookup"><span data-stu-id="bb44a-116">In **Solution Explorer** , open the shortcut menu for the project, and then choose **Properties** .</span></span>  
  
2. <span data-ttu-id="bb44a-117">選擇 [ **簽署** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bb44a-117">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="bb44a-118">選取 [簽署組件]  方塊。</span><span class="sxs-lookup"><span data-stu-id="bb44a-118">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="bb44a-119">在 [ **選擇強式名稱金鑰** 檔案] 方塊中，選擇 **[流覽]** ，然後流覽至金鑰檔案。</span><span class="sxs-lookup"><span data-stu-id="bb44a-119">In the **Choose a strong name key file** box, choose **Browse** , and then navigate to the key file.</span></span> <span data-ttu-id="bb44a-120">若要建立新的金鑰檔，請選擇 [ **新增** ]，然後在 [ **建立強式名稱金鑰** ] 對話方塊中輸入其名稱。</span><span class="sxs-lookup"><span data-stu-id="bb44a-120">To create a new key file, choose **New** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bb44a-121">若要[延遲簽署組件](delay-sign.md)，請選擇公開金鑰檔案。</span><span class="sxs-lookup"><span data-stu-id="bb44a-121">In order to [delay sign an assembly](delay-sign.md), choose a public key file.</span></span>  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="bb44a-122">使用元件連結器建立元件並以強式名稱簽署元件</span><span class="sxs-lookup"><span data-stu-id="bb44a-122">Create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
<span data-ttu-id="bb44a-123">在 [Visual Studio 的開發人員命令提示字元](../../framework/tools/developer-command-prompt-for-vs.md)上，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="bb44a-123">At the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), enter the following command:</span></span>  

<span data-ttu-id="bb44a-124">**al** **/out：** \<*assemblyName*> *\<moduleName>* **/keyfile：**\<*keyfileName*></span><span class="sxs-lookup"><span data-stu-id="bb44a-124">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  

<span data-ttu-id="bb44a-125">其中：</span><span class="sxs-lookup"><span data-stu-id="bb44a-125">Where:</span></span>  

- <span data-ttu-id="bb44a-126">*assemblyName* 是強式簽署元件的名稱， ( *.dll* 或 *.Exe* 檔案，) 該元件連結器將發出。</span><span class="sxs-lookup"><span data-stu-id="bb44a-126">*assemblyName* is the name of the strongly signed assembly (a *.dll* or *.exe* file) that Assembly Linker will emit.</span></span>  
  
- <span data-ttu-id="bb44a-127">*moduleName* 是 .NET Framework 程式碼模組的名稱， (包含一或多個類型的 *.netmodule* 檔案) 。</span><span class="sxs-lookup"><span data-stu-id="bb44a-127">*moduleName* is the name of a .NET Framework code module (a *.netmodule* file) that includes one or more types.</span></span> <span data-ttu-id="bb44a-128">您可以使用 *.netmodule* `/target:module` c # 或 Visual Basic 中的參數來編譯您的程式碼，以建立 .netmodule 檔案。</span><span class="sxs-lookup"><span data-stu-id="bb44a-128">You can create a *.netmodule* file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>
  
- <span data-ttu-id="bb44a-129">*keyfileName* 是包含金鑰組的容器或檔案名。</span><span class="sxs-lookup"><span data-stu-id="bb44a-129">*keyfileName* is the name of the container or file that contains the key pair.</span></span> <span data-ttu-id="bb44a-130">元件連結器會解讀相對於目前的目錄的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="bb44a-130">Assembly Linker interprets a relative path in relation to the current directory.</span></span>  

<span data-ttu-id="bb44a-131">下列範例會使用 *sgKey* 金鑰檔，以強式名稱簽署元件 *MyAssembly.dll* 。</span><span class="sxs-lookup"><span data-stu-id="bb44a-131">The following example signs the assembly *MyAssembly.dll* with a strong name by using the key file *sgKey.snk* .</span></span>  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
<span data-ttu-id="bb44a-132">如需這項工具的詳細資訊，請參閱 [組件連結器](../../framework/tools/al-exe-assembly-linker.md)。</span><span class="sxs-lookup"><span data-stu-id="bb44a-132">For more information about this tool, see [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span></span>  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="bb44a-133">使用屬性以強式名稱簽署元件</span><span class="sxs-lookup"><span data-stu-id="bb44a-133">Sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="bb44a-134">將 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 屬性加入至您的原始程式碼檔，並指定容器或檔案名稱，其中包含以強式名稱簽署組件時所使用的金鑰組。</span><span class="sxs-lookup"><span data-stu-id="bb44a-134">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  

2. <span data-ttu-id="bb44a-135">以一般方式編譯原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="bb44a-135">Compile the source code file normally.</span></span>  

   > [!NOTE]
   > <span data-ttu-id="bb44a-136">C# 和 Visual Basic 編譯器在原始程式碼中遇到 <xref:System.Reflection.AssemblyKeyFileAttribute> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 屬性時，會發出編譯器警告 (分別為 CS1699 和 BC41008)。</span><span class="sxs-lookup"><span data-stu-id="bb44a-136">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="bb44a-137">您可以忽略這些警告。</span><span class="sxs-lookup"><span data-stu-id="bb44a-137">You can ignore the warnings.</span></span>  

<span data-ttu-id="bb44a-138">下列範例 <xref:System.Reflection.AssemblyKeyFileAttribute> 會使用具有金鑰檔的屬性，名為 *keyfile .snk* ，它位於編譯元件的目錄中。</span><span class="sxs-lookup"><span data-stu-id="bb44a-138">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called *keyfile.snk* , which is located in the directory where the assembly is compiled.</span></span>  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

<span data-ttu-id="bb44a-139">您也可以在編譯原始程式檔時延遲簽署組件。</span><span class="sxs-lookup"><span data-stu-id="bb44a-139">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="bb44a-140">如需詳細資訊，請參閱 [延遲簽署元件](delay-sign.md)。</span><span class="sxs-lookup"><span data-stu-id="bb44a-140">For more information, see [Delay-sign an assembly](delay-sign.md).</span></span>  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="bb44a-141">使用編譯器以強式名稱簽署元件</span><span class="sxs-lookup"><span data-stu-id="bb44a-141">Sign an assembly with a strong name by using the compiler</span></span>  

<span data-ttu-id="bb44a-142">在 C# 和 Visual Basic 中使用 `/keyfile` 或 `/delaysign` 編譯器選項，或是在 C++ 中使用 `/KEYFILE` 或 `/DELAYSIGN` 連結器選項編譯原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="bb44a-142">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="bb44a-143">在選項名稱後面加上冒號和金鑰檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="bb44a-143">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="bb44a-144">使用命令列編譯器時，您可以將金鑰檔複製到包含您的原始程式碼檔的目錄中。</span><span class="sxs-lookup"><span data-stu-id="bb44a-144">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  

<span data-ttu-id="bb44a-145">如需延遲簽署的詳細資訊，請參閱 [延遲簽署元件](delay-sign.md)。</span><span class="sxs-lookup"><span data-stu-id="bb44a-145">For information on delay signing, see [Delay-sign an assembly](delay-sign.md).</span></span>  

<span data-ttu-id="bb44a-146">下列範例會使用 c # 編譯器，並使用 SgKey *UtilityLibrary.dll* 的金鑰檔，以強式名稱簽署元件UtilityLibrary.dll *。*</span><span class="sxs-lookup"><span data-stu-id="bb44a-146">The following example uses the C# compiler and signs the assembly *UtilityLibrary.dll* with a strong name by using the key file *sgKey.snk* .</span></span>  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a><span data-ttu-id="bb44a-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="bb44a-147">See also</span></span>

- [<span data-ttu-id="bb44a-148">建立和使用強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="bb44a-148">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="bb44a-149">如何：建立公開/私密金鑰組</span><span class="sxs-lookup"><span data-stu-id="bb44a-149">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="bb44a-150">Al.exe (元件連結器) </span><span class="sxs-lookup"><span data-stu-id="bb44a-150">Al.exe (Assembly Linker)</span></span>](../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="bb44a-151">延遲簽署組件</span><span class="sxs-lookup"><span data-stu-id="bb44a-151">Delay-sign an assembly</span></span>](delay-sign.md)
- [<span data-ttu-id="bb44a-152">管理組件和資訊清單簽署</span><span class="sxs-lookup"><span data-stu-id="bb44a-152">Manage assembly and manifest signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="bb44a-153">專案設計工具、簽署頁</span><span class="sxs-lookup"><span data-stu-id="bb44a-153">Signing page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
