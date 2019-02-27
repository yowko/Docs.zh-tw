---
title: -platform (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /platform
helpviewer_keywords:
- platform compiler option [C#]
- -platform compiler option [C#]
- /platform compiler option [C#]
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
ms.openlocfilehash: 6d4918407c68c7164db023b19cb170aef12fd203
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56663895"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="02666-102">-platform (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="02666-102">-platform (C# Compiler Options)</span></span>
<span data-ttu-id="02666-103">指定哪個 Common Language Runtime (CLR) 版本可以執行組件。</span><span class="sxs-lookup"><span data-stu-id="02666-103">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02666-104">語法</span><span class="sxs-lookup"><span data-stu-id="02666-104">Syntax</span></span>  
  
```console  
-platform:string  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02666-105">參數</span><span class="sxs-lookup"><span data-stu-id="02666-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="02666-106">anycpu (預設值)、anycpu32bitpreferred、ARM、x64、x86 或 Itanium。</span><span class="sxs-lookup"><span data-stu-id="02666-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02666-107">備註</span><span class="sxs-lookup"><span data-stu-id="02666-107">Remarks</span></span>  
  
-   <span data-ttu-id="02666-108">**anycpu** (預設值) 會將組件編譯為可在所有平台上執行。</span><span class="sxs-lookup"><span data-stu-id="02666-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="02666-109">您的應用程式會盡可能做為 64 位元處理序執行，而且只有在 32 位元模式可用時才會回到該模式。</span><span class="sxs-lookup"><span data-stu-id="02666-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>  
  
-   <span data-ttu-id="02666-110">**anycpu32bitpreferred** 會將組件編譯為可在所有平台上執行。</span><span class="sxs-lookup"><span data-stu-id="02666-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="02666-111">您的應用程式在同時支援 64 位元和 32 位元應用程式的系統上會以 32 位元模式執行。</span><span class="sxs-lookup"><span data-stu-id="02666-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="02666-112">您只能針對以 .NET Framework 4.5 為目標的專案指定此選項。</span><span class="sxs-lookup"><span data-stu-id="02666-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>  
  
-   <span data-ttu-id="02666-113">**ARM** 會將您的組件編譯為可在採用 Advanced RISC Machine (ARM) 處理器的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="02666-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>  
  
-   <span data-ttu-id="02666-114">**ARM64** 會編譯您的組件，使其可由具備支援 A64 指令集進階 RISC 機器 (ARM) 處理器電腦上的 64 位元 CLR 執行。</span><span class="sxs-lookup"><span data-stu-id="02666-114">**ARM64** compiles your assembly to run by the 64-bit CLR on a computer that has an Advanced RISC Machine (ARM) processor that supports the A64 instruction set.</span></span>  

-   <span data-ttu-id="02666-115">在支援 AMD64 或 EM64T 指令集的電腦上，**x64** 會將組件編譯成由 64 位元 CLR 執行。</span><span class="sxs-lookup"><span data-stu-id="02666-115">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>  
  
-   <span data-ttu-id="02666-116">**x86** 會將組件編譯為以 32 位元、與 x86 相容的 CLR 執行。</span><span class="sxs-lookup"><span data-stu-id="02666-116">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>  
  
-   <span data-ttu-id="02666-117">**Itanium** 會將組件編譯為可以在使用 Itanium 處理器的電腦上以 64 位元 CLR 執行。</span><span class="sxs-lookup"><span data-stu-id="02666-117">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>  
  
 <span data-ttu-id="02666-118">在 64 位元 Windows 作業系統上：</span><span class="sxs-lookup"><span data-stu-id="02666-118">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="02666-119">使用 **-platform:x86** 所編譯的組件會在 WOW64 下執行的 32 位元 CLR 上執行。</span><span class="sxs-lookup"><span data-stu-id="02666-119">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="02666-120">使用 **-platform:anycpu** 所編譯的 DLL 會在與載入它的程序相同的 CLR 上執行。</span><span class="sxs-lookup"><span data-stu-id="02666-120">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>  
  
-   <span data-ttu-id="02666-121">使用 **-platform:anycpu** 所編譯的可執行檔會在 64 位元 CLR 上執行。</span><span class="sxs-lookup"><span data-stu-id="02666-121">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="02666-122">使用 **-platform:anycpu32bitpreferred** 所編譯的可執行檔會在 32 位元 CLR 上執行。</span><span class="sxs-lookup"><span data-stu-id="02666-122">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="02666-123">**anycpu32bitpreferred** 設定只對可執行檔 (.EXE) 有效，而且需要 .NET Framework 4.5。</span><span class="sxs-lookup"><span data-stu-id="02666-123">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="02666-124">如需開發要在 Windows 64 位元作業系統上執行之應用程式的詳細資訊，請參閱 [64 位元應用程式](../../../framework/64-bit-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="02666-124">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="02666-125">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="02666-125">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="02666-126">開啟專案的 [屬性]  頁面。</span><span class="sxs-lookup"><span data-stu-id="02666-126">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="02666-127">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="02666-127">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="02666-128">修改**平台目標**屬性，並且針對以 .NET Framework 4.5 為目標的專案選取或清除 [建議使用 32 位元] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="02666-128">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>  
  
 <span data-ttu-id="02666-129">請注意，在 Visual C# Express 開發環境中無法使用 **-platform**。</span><span class="sxs-lookup"><span data-stu-id="02666-129">**Note -platform** is not available in the development environment in Visual C# Express.</span></span>  
  
 <span data-ttu-id="02666-130">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>。</span><span class="sxs-lookup"><span data-stu-id="02666-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02666-131">範例</span><span class="sxs-lookup"><span data-stu-id="02666-131">Example</span></span>  
 <span data-ttu-id="02666-132">下列範例示範如何使用 **-platform** 選項，指定應用程式應該在 64 位元 Windows 作業系統上以 64 位元 CLR 執行。</span><span class="sxs-lookup"><span data-stu-id="02666-132">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>  
  
```console  
csc -platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="02666-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02666-133">See also</span></span>

- [<span data-ttu-id="02666-134">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="02666-134">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="02666-135">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="02666-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
