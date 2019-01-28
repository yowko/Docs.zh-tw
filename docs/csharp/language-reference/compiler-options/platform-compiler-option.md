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
ms.openlocfilehash: 1573e28f2a6f9dec7825d364debcdf1085ef7ff2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635659"
---
# <a name="-platform-c-compiler-options"></a><span data-ttu-id="891c1-102">-platform (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="891c1-102">-platform (C# Compiler Options)</span></span>
<span data-ttu-id="891c1-103">指定哪個 Common Language Runtime (CLR) 版本可以執行組件。</span><span class="sxs-lookup"><span data-stu-id="891c1-103">Specifies which version of the Common Language Runtime (CLR) can run the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="891c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="891c1-104">Syntax</span></span>  
  
```console  
-platform:string  
```  
  
#### <a name="parameters"></a><span data-ttu-id="891c1-105">參數</span><span class="sxs-lookup"><span data-stu-id="891c1-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="891c1-106">anycpu (預設值)、anycpu32bitpreferred、ARM、x64、x86 或 Itanium。</span><span class="sxs-lookup"><span data-stu-id="891c1-106">anycpu (default), anycpu32bitpreferred, ARM, x64, x86, or Itanium.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="891c1-107">備註</span><span class="sxs-lookup"><span data-stu-id="891c1-107">Remarks</span></span>  
  
-   <span data-ttu-id="891c1-108">**anycpu** (預設值) 會將組件編譯為可在所有平台上執行。</span><span class="sxs-lookup"><span data-stu-id="891c1-108">**anycpu** (default) compiles your assembly to run on any platform.</span></span> <span data-ttu-id="891c1-109">您的應用程式會盡可能做為 64 位元處理序執行，而且只有在 32 位元模式可用時才會回到該模式。</span><span class="sxs-lookup"><span data-stu-id="891c1-109">Your application runs as a 64-bit process whenever possible and falls back to 32-bit when only that mode is available.</span></span>  
  
-   <span data-ttu-id="891c1-110">**anycpu32bitpreferred** 會將組件編譯為可在所有平台上執行。</span><span class="sxs-lookup"><span data-stu-id="891c1-110">**anycpu32bitpreferred** compiles your assembly to run on any platform.</span></span> <span data-ttu-id="891c1-111">您的應用程式在同時支援 64 位元和 32 位元應用程式的系統上會以 32 位元模式執行。</span><span class="sxs-lookup"><span data-stu-id="891c1-111">Your application runs in 32-bit mode on systems that support both 64-bit and 32-bit applications.</span></span> <span data-ttu-id="891c1-112">您只能針對以 .NET Framework 4.5 為目標的專案指定此選項。</span><span class="sxs-lookup"><span data-stu-id="891c1-112">You can specify this option only for projects that target the .NET Framework 4.5.</span></span>  
  
-   <span data-ttu-id="891c1-113">**ARM** 會將您的組件編譯為可在採用 Advanced RISC Machine (ARM) 處理器的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="891c1-113">**ARM** compiles your assembly to run on a computer that has an Advanced RISC Machine (ARM) processor.</span></span>  
  
-   <span data-ttu-id="891c1-114">在支援 AMD64 或 EM64T 指令集的電腦上，**x64** 會將組件編譯成由 64 位元 CLR 執行。</span><span class="sxs-lookup"><span data-stu-id="891c1-114">**x64** compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>  
  
-   <span data-ttu-id="891c1-115">**x86** 會將組件編譯為以 32 位元、與 x86 相容的 CLR 執行。</span><span class="sxs-lookup"><span data-stu-id="891c1-115">**x86** compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>  
  
-   <span data-ttu-id="891c1-116">**Itanium** 會將組件編譯為可以在使用 Itanium 處理器的電腦上以 64 位元 CLR 執行。</span><span class="sxs-lookup"><span data-stu-id="891c1-116">**Itanium** compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>  
  
 <span data-ttu-id="891c1-117">在 64 位元 Windows 作業系統上：</span><span class="sxs-lookup"><span data-stu-id="891c1-117">On a 64-bit Windows operating system:</span></span>  
  
-   <span data-ttu-id="891c1-118">使用 **-platform:x86** 所編譯的組件會在 WOW64 下執行的 32 位元 CLR 上執行。</span><span class="sxs-lookup"><span data-stu-id="891c1-118">Assemblies compiled with **-platform:x86** execute on the 32-bit CLR running under WOW64.</span></span>  
  
-   <span data-ttu-id="891c1-119">使用 **-platform:anycpu** 所編譯的 DLL 會在與載入它的程序相同的 CLR 上執行。</span><span class="sxs-lookup"><span data-stu-id="891c1-119">A DLL compiled with the **-platform:anycpu** executes on the same CLR as the process into which it is loaded.</span></span>  
  
-   <span data-ttu-id="891c1-120">使用 **-platform:anycpu** 所編譯的可執行檔會在 64 位元 CLR 上執行。</span><span class="sxs-lookup"><span data-stu-id="891c1-120">Executables that are compiled with the **-platform:anycpu** execute on the 64-bit CLR.</span></span>  
  
-   <span data-ttu-id="891c1-121">使用 **-platform:anycpu32bitpreferred** 所編譯的可執行檔會在 32 位元 CLR 上執行。</span><span class="sxs-lookup"><span data-stu-id="891c1-121">Executables compiled with **-platform:anycpu32bitpreferred** execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="891c1-122">**anycpu32bitpreferred** 設定只對可執行檔 (.EXE) 有效，而且需要 .NET Framework 4.5。</span><span class="sxs-lookup"><span data-stu-id="891c1-122">The **anycpu32bitpreferred** setting is valid only for executable (.EXE) files, and it requires the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="891c1-123">如需開發要在 Windows 64 位元作業系統上執行之應用程式的詳細資訊，請參閱 [64 位元應用程式](../../../framework/64-bit-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="891c1-123">For more information about developing an application to run on a Windows 64-bit operating system, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="891c1-124">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="891c1-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="891c1-125">開啟專案的 [屬性]  頁面。</span><span class="sxs-lookup"><span data-stu-id="891c1-125">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="891c1-126">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="891c1-126">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="891c1-127">修改**平台目標**屬性，並且針對以 .NET Framework 4.5 為目標的專案選取或清除 [建議使用 32 位元] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="891c1-127">Modify the **Platform target** property and, for projects that target the .NET Framework 4.5, select or clear the **Prefer 32-bit** check box.</span></span>  
  
 <span data-ttu-id="891c1-128">請注意，在 Visual C# Express 開發環境中無法使用 **-platform**。</span><span class="sxs-lookup"><span data-stu-id="891c1-128">**Note -platform** is not available in the development environment in Visual C# Express.</span></span>  
  
 <span data-ttu-id="891c1-129">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>。</span><span class="sxs-lookup"><span data-stu-id="891c1-129">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="891c1-130">範例</span><span class="sxs-lookup"><span data-stu-id="891c1-130">Example</span></span>  
 <span data-ttu-id="891c1-131">下列範例示範如何使用 **-platform** 選項，指定應用程式應該在 64 位元 Windows 作業系統上以 64 位元 CLR 執行。</span><span class="sxs-lookup"><span data-stu-id="891c1-131">The following example shows how to use the **-platform** option to specify that the application should be run by the 64-bit CLR on a 64-bit Windows operating system.</span></span>  
  
```console  
csc -platform:anycpu filename.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="891c1-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="891c1-132">See also</span></span>

- [<span data-ttu-id="891c1-133">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="891c1-133">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="891c1-134">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="891c1-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
