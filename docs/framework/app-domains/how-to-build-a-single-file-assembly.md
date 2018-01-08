---
title: "如何：建置單一檔案組件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd9f2bab23fff1bbc4ebb521b167ac8031af3bc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-a-single-file-assembly"></a><span data-ttu-id="c97a1-102">如何：建置單一檔案組件</span><span class="sxs-lookup"><span data-stu-id="c97a1-102">How to: Build a Single-File Assembly</span></span>
<span data-ttu-id="c97a1-103">單一檔案組件，是最簡單的組件類型，包含類型資訊和實作，以及[組件資訊清單](../../../docs/framework/app-domains/assembly-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="c97a1-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md).</span></span> <span data-ttu-id="c97a1-104">您可以使用命令列編譯器或 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 來建立單一檔案組件。</span><span class="sxs-lookup"><span data-stu-id="c97a1-104">You can use command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] to create a single-file assembly.</span></span> <span data-ttu-id="c97a1-105">編譯器預設會建立副檔名為 .exe 的組件檔案。</span><span class="sxs-lookup"><span data-stu-id="c97a1-105">By default, the compiler creates an assembly file with an .exe extension.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]<span data-ttu-id="c97a1-106"> for C# 和 Visual Basic 只能用於建立單一檔案組件。</span><span class="sxs-lookup"><span data-stu-id="c97a1-106"> for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="c97a1-107">如想建立多檔案組件，您必須使用命令列編譯器或 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for Visual C++。</span><span class="sxs-lookup"><span data-stu-id="c97a1-107">If you want to create multifile assemblies, you must use command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for Visual C++.</span></span>  
  
 <span data-ttu-id="c97a1-108">下列程序示範如何使用命令列編譯器建立單一檔案組件。</span><span class="sxs-lookup"><span data-stu-id="c97a1-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>  
  
### <a name="to-create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="c97a1-109">建立副檔名為 .exe 的組件</span><span class="sxs-lookup"><span data-stu-id="c97a1-109">To create an assembly with an .exe extension</span></span>  
  
1.  <span data-ttu-id="c97a1-110">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="c97a1-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="c97a1-111">\<*編譯器命令*> \<*模組名稱*></span><span class="sxs-lookup"><span data-stu-id="c97a1-111">\<*compiler command*> \<*module name*></span></span>  
  
     <span data-ttu-id="c97a1-112">在這個命令中，「編譯器命令」是您程式碼模組所用語言的編譯器命令，而「模組名稱」則是編譯至組件的程式碼模組名稱。</span><span class="sxs-lookup"><span data-stu-id="c97a1-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>  
  
 <span data-ttu-id="c97a1-113">以下範例會從稱為 `myCode` 的程式碼模組建立名為 `myCode.exe` 的組件。</span><span class="sxs-lookup"><span data-stu-id="c97a1-113">The following example creates an assembly named `myCode.exe` from a code module called `myCode`.</span></span>  
  
```csharp  
csc myCode.cs  
```  
  
```vb  
vbc myCode.vb  
```  
  
#### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="c97a1-114">建立副檔名為 .exe 的組件並指定輸出檔名稱</span><span class="sxs-lookup"><span data-stu-id="c97a1-114">To create an assembly with an .exe extension and specify the output file name</span></span>  
  
1.  <span data-ttu-id="c97a1-115">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="c97a1-115">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="c97a1-116">\<*編譯器命令*> **/out:**\<*檔案名稱*> \<*模組名稱*></span><span class="sxs-lookup"><span data-stu-id="c97a1-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>  
  
     <span data-ttu-id="c97a1-117">在這個命令中，「編譯器命令」是您程式碼模組所用語言的編譯器命令、「檔案名稱」是輸出檔名稱，而「模組名稱」則是編譯至組件的程式碼模組名稱。</span><span class="sxs-lookup"><span data-stu-id="c97a1-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>  
  
 <span data-ttu-id="c97a1-118">以下範例會從稱為 `myCode` 的程式碼模組建立名為 `myAssembly.exe` 的組件。</span><span class="sxs-lookup"><span data-stu-id="c97a1-118">The following example creates an assembly named `myAssembly.exe` from a code module called `myCode`.</span></span>  
  
```csharp  
csc /out:myAssembly.exe myCode.cs  
```  
  
```vb  
vbc /out:myAssembly.exe myCode.vb  
```  
  
## <a name="creating-library-assemblies"></a><span data-ttu-id="c97a1-119">建立程式庫組件</span><span class="sxs-lookup"><span data-stu-id="c97a1-119">Creating Library Assemblies</span></span>  
 <span data-ttu-id="c97a1-120">程式庫組件類似類別庫。</span><span class="sxs-lookup"><span data-stu-id="c97a1-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="c97a1-121">它包含其他組件會參考的類型，但沒有可開始執行的進入點。</span><span class="sxs-lookup"><span data-stu-id="c97a1-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>  
  
#### <a name="to-create-a-library-assembly"></a><span data-ttu-id="c97a1-122">建立程式庫組件</span><span class="sxs-lookup"><span data-stu-id="c97a1-122">To create a library assembly</span></span>  
  
1.  <span data-ttu-id="c97a1-123">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="c97a1-123">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="c97a1-124">\<*編譯器命令*> **/t:library** \<*模組名稱*></span><span class="sxs-lookup"><span data-stu-id="c97a1-124">\<*compiler command*> **/t:library** \<*module name*></span></span>  
  
     <span data-ttu-id="c97a1-125">在這個命令中，「編譯器命令」是您程式碼模組所用語言的編譯器命令，而「模組名稱」則是編譯至組件的程式碼模組名稱。</span><span class="sxs-lookup"><span data-stu-id="c97a1-125">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="c97a1-126">您也可以使用其他編譯器選項，例如 **/out:** 選項。</span><span class="sxs-lookup"><span data-stu-id="c97a1-126">You can also use other compiler options, such as the **/out:** option.</span></span>  
  
 <span data-ttu-id="c97a1-127">以下範例會從稱為 `myCode` 的程式碼模組建立名為 `myCodeAssembly.dll` 的程式庫組件。</span><span class="sxs-lookup"><span data-stu-id="c97a1-127">The following example creates a library assembly named `myCodeAssembly.dll` from a code module called `myCode`.</span></span>  
  
```csharp  
csc /out:myCodeLibrary.dll /t:library myCode.cs  
```  
  
```vb  
vbc /out:myCodeLibrary.dll /t:library myCode.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c97a1-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="c97a1-128">See Also</span></span>  
 [<span data-ttu-id="c97a1-129">建立組件</span><span class="sxs-lookup"><span data-stu-id="c97a1-129">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="c97a1-130">多檔案組件</span><span class="sxs-lookup"><span data-stu-id="c97a1-130">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 [<span data-ttu-id="c97a1-131">操作說明：建置多檔案組件</span><span class="sxs-lookup"><span data-stu-id="c97a1-131">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="c97a1-132">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="c97a1-132">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
