---
title: "64 位元應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [C++], 64-bit
- 64-bit applications [C++]
- 64-bit programming [C++]
ms.assetid: fd4026bc-2c3d-4b27-86dc-ec5e96018181
caps.latest.revision: 53
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9930b44e8ab711f319140e43ad0a36d5d78a7ffb
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="64-bit-applications"></a><span data-ttu-id="d985d-102">64 位元應用程式</span><span class="sxs-lookup"><span data-stu-id="d985d-102">64-bit Applications</span></span>
<span data-ttu-id="d985d-103">您在編譯應用程式時，可以指定其應以原生應用程式在 Windows 64 位元作業系統上或在 WOW64 下 (Windows 64 位元上的 Windows 32 位元) 執行。</span><span class="sxs-lookup"><span data-stu-id="d985d-103">When you compile an application, you can specify that it should run on a Windows 64-bit operating system either as a native application or under WOW64 (Windows 32-bit on Windows 64-bit).</span></span> <span data-ttu-id="d985d-104">WOW64 是讓 32 位元應用程式可在 64 位元系統上執行的相容性環境。</span><span class="sxs-lookup"><span data-stu-id="d985d-104">WOW64 is a compatibility environment that enables a 32-bit application to run on a 64-bit system.</span></span> <span data-ttu-id="d985d-105">所有 64 位元版本的 Windows 作業系統中都包含 WOW64。</span><span class="sxs-lookup"><span data-stu-id="d985d-105">WOW64 is included in all 64-bit versions of the Windows operating system.</span></span>  
  
## <a name="running-32-bit-vs-64-bit-applications-on-windows"></a><span data-ttu-id="d985d-106">在 Windows 上執行 32 位元及64 位元應用程式。</span><span class="sxs-lookup"><span data-stu-id="d985d-106">Running 32-bit vs. 64-bit Applications on Windows</span></span>  
 <span data-ttu-id="d985d-107">所有在 .NET Framework 1.0 或 1.1 上建置的應用程式都會被視為在 64 位元作業系統上的 32 位元應用程式，並一律在 WOW64 和 32 位元 Common Language Runtime (CLR) 下執行。</span><span class="sxs-lookup"><span data-stu-id="d985d-107">All applications that are built on the .NET Framework 1.0 or 1.1 are treated as 32-bit applications on a 64-bit operating system and are always executed under WOW64 and the 32-bit common language runtime (CLR).</span></span> <span data-ttu-id="d985d-108">在 [!INCLUDE[net_v40_long](../../includes/net-v40-long-md.md)] 或更新版本上建置的 32 位元應用程式也會在 64 位元系統的 WOW64 下執行。</span><span class="sxs-lookup"><span data-stu-id="d985d-108">32-bit applications that are built on the [!INCLUDE[net_v40_long](../../includes/net-v40-long-md.md)] or later versions also run under WOW64 on 64-bit systems.</span></span>  
  
 <span data-ttu-id="d985d-109">Visual Studio 在 x86 電腦上安裝 CLR 32 位元版本，而在 64 位元 Windows 電腦上同時安裝 32 位元版本和適當的 CLR 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="d985d-109">Visual Studio installs the 32-bit version of the CLR on an x86 computer, and both the 32-bit version and the appropriate 64-bit version of the CLR on a 64-bit Windows computer.</span></span> <span data-ttu-id="d985d-110">(由於 Visual Studio 是 32 位元應用程式，所以安裝在 64 位元系統上時，會在 WOW64 下執行。)</span><span class="sxs-lookup"><span data-stu-id="d985d-110">(Because Visual Studio is a 32-bit application, when it is installed on a 64-bit system, it runs under WOW64.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d985d-111">X86 模擬和 Itanium 處理器系列之 WOW64 子系統的設計會限制應用程式在一個處理器上執行。</span><span class="sxs-lookup"><span data-stu-id="d985d-111">Because of the design of x86 emulation and the WOW64 subsystem for the Itanium processor family, applications are restricted to execution on one processor.</span></span> <span data-ttu-id="d985d-112">這些因素會降低在 Itanium 系統上執行之 32 位元 .NET Framework 應用程式的效能和延展性。</span><span class="sxs-lookup"><span data-stu-id="d985d-112">These factors reduce the performance and scalability of 32-bit .NET Framework applications that run on Itanium-based systems.</span></span> <span data-ttu-id="d985d-113">為了增加效能和延展性，我們建議您選用包含 Itanium 系統原生 64 位元支援的 [!INCLUDE[net_v40_long](../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d985d-113">We recommend that you use the [!INCLUDE[net_v40_long](../../includes/net-v40-long-md.md)], which includes native 64-bit support for Itanium-based systems, for increased performance and scalability.</span></span>  
  
 <span data-ttu-id="d985d-114">根據預設，當您在 64 位元 Windows 作業系統上執行 64 位元 Managed 應用程式時，可以建立不超過 2 GB 的物件。</span><span class="sxs-lookup"><span data-stu-id="d985d-114">By default, when you run a 64-bit managed application on a 64-bit Windows operating system, you can create an object of no more than 2 gigabytes (GB).</span></span> <span data-ttu-id="d985d-115">不過，在 [!INCLUDE[net_v45](../../includes/net-v45-md.md)] 中，您可以提高上限。</span><span class="sxs-lookup"><span data-stu-id="d985d-115">However, in the [!INCLUDE[net_v45](../../includes/net-v45-md.md)], you can increase this limit.</span></span>  <span data-ttu-id="d985d-116">如需詳細資訊，請參閱 [\<gcAllowVeryLargeObjects> 元素](../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)。</span><span class="sxs-lookup"><span data-stu-id="d985d-116">For more information, see the [\<gcAllowVeryLargeObjects> element](../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md).</span></span>  
  
 <span data-ttu-id="d985d-117">許多組件在 32 位元 CLR 和 64 位元 CLR 上以相同方式執行。</span><span class="sxs-lookup"><span data-stu-id="d985d-117">Many assemblies run identically on both the 32-bit CLR and the 64-bit CLR.</span></span> <span data-ttu-id="d985d-118">不過，取決於 CLR，有些程式可能會有不同的行為，若它們包含下列一或多項情形：</span><span class="sxs-lookup"><span data-stu-id="d985d-118">However, some programs may behave differently, depending on the CLR, if they contain one or more of the following:</span></span>  
  
-   <span data-ttu-id="d985d-119">包含視平台而變更大小之成員的結構，(例如任何指標類型)。</span><span class="sxs-lookup"><span data-stu-id="d985d-119">Structures that contain members that change size depending on the platform (for example, any pointer type).</span></span>  
  
-   <span data-ttu-id="d985d-120">包含常數大小的指標算術。</span><span class="sxs-lookup"><span data-stu-id="d985d-120">Pointer arithmetic that includes constant sizes.</span></span>  
  
-   <span data-ttu-id="d985d-121">不正確的平台叫用，或是使用 `Int32` 而不是 `IntPtr` 作為控點的 COM 宣告。</span><span class="sxs-lookup"><span data-stu-id="d985d-121">Incorrect platform invoke or COM declarations that use `Int32` for handles instead of `IntPtr`.</span></span>  
  
-   <span data-ttu-id="d985d-122">將 `IntPtr` 轉換到 `Int32` 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d985d-122">Code that casts `IntPtr` to `Int32`.</span></span>  
  
 <span data-ttu-id="d985d-123">如需如何將 32 位元應用程式移植到 64 位元 CLR 上執行的詳細資訊，請參閱 MSDN Library 中的[將 32 位元 Managed 程式碼移轉至 64 位元](http://go.microsoft.com/fwlink/?LinkId=150542)。</span><span class="sxs-lookup"><span data-stu-id="d985d-123">For more information about how to port a 32-bit application to run on the 64-bit CLR, see [Migrating 32-bit Managed Code to 64-bit](http://go.microsoft.com/fwlink/?LinkId=150542) in the MSDN Library.</span></span>  
  
## <a name="general-64-bit-programming-information"></a><span data-ttu-id="d985d-124">64 位元程式設計的一般資訊</span><span class="sxs-lookup"><span data-stu-id="d985d-124">General 64-Bit Programming Information</span></span>  
 <span data-ttu-id="d985d-125">如需 64 位元程式設計的一般資訊，請參閱下列文件：</span><span class="sxs-lookup"><span data-stu-id="d985d-125">For general information about 64-bit programming, see the following documents:</span></span>  
  
-   <span data-ttu-id="d985d-126">如需 64 位元 Windows 電腦上的 64 位元版本 CLR 的詳細資訊，請參閱 MSDN 網站上的 [.NET Framework 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=37079)。</span><span class="sxs-lookup"><span data-stu-id="d985d-126">For more information about the 64-bit version of the CLR on a 64-bit Windows computer, see the [.NET Framework Developer Center](http://go.microsoft.com/fwlink/?LinkId=37079) on the MSDN website.</span></span>  
  
-   <span data-ttu-id="d985d-127">在 [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)] 文件中，請參閱 [64 位元 Windows 程式設計指南](http://go.microsoft.com/fwlink/p/?LinkId=253512)。</span><span class="sxs-lookup"><span data-stu-id="d985d-127">In the [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)] documentation, see [Programming Guide for 64-bit Windows](http://go.microsoft.com/fwlink/p/?LinkId=253512).</span></span>  
  
-   <span data-ttu-id="d985d-128">如需如何下載 64 位元版本 CLR 的詳細資訊，請參閱 MSDN 網站上的 [.NET Framework 開發人員中心下載](http://go.microsoft.com/fwlink/?LinkId=50953)。</span><span class="sxs-lookup"><span data-stu-id="d985d-128">For information about how to download a 64-bit version of the CLR, see [.NET Framework Developer Center Downloads](http://go.microsoft.com/fwlink/?LinkId=50953) on the MSDN website.</span></span>  
  
-   <span data-ttu-id="d985d-129">如需 Visual Studio 支援建立 64 位元應用程式的相關資訊，請參閱 [Visual Studio IDE 64 位元支援](http://msdn.microsoft.com/library/b08ff3ad-c6fd-468f-94d5-01a61aab6833)。</span><span class="sxs-lookup"><span data-stu-id="d985d-129">For information about Visual Studio support for creating 64-bit applications, see [Visual Studio IDE 64-Bit Support](http://msdn.microsoft.com/library/b08ff3ad-c6fd-468f-94d5-01a61aab6833).</span></span>  
  
## <a name="compiler-support-for-creating-64-bit-applications"></a><span data-ttu-id="d985d-130">建立 64 位元應用程式的編譯器支援</span><span class="sxs-lookup"><span data-stu-id="d985d-130">Compiler Support for Creating 64-Bit Applications</span></span>  
 <span data-ttu-id="d985d-131">根據預設，當您在 32 位元或 64 位元的電腦上使用 .NET Framework 應用程式建置應用程式時，應用程式會以原生應用程式在 64 位元電腦上執行 (也就是不在 WOW64 下)。</span><span class="sxs-lookup"><span data-stu-id="d985d-131">By default, when you use the .NET Framework to build an application on either a 32-bit or a 64-bit computer, the application will run on a 64-bit computer as a native application (that is, not under WOW64).</span></span> <span data-ttu-id="d985d-132">下表列出說明如何使用 Visual Studio 編譯器來建立將會在 WOW64 下以原生執行 (或兩者) 之 64 位元應用程式的文件。</span><span class="sxs-lookup"><span data-stu-id="d985d-132">The following table lists documents that explain how to use Visual Studio compilers to create 64-bit applications that will run as native, under WOW64, or both.</span></span>  
  
|<span data-ttu-id="d985d-133">編譯器</span><span class="sxs-lookup"><span data-stu-id="d985d-133">Compiler</span></span>|<span data-ttu-id="d985d-134">編譯器選項</span><span class="sxs-lookup"><span data-stu-id="d985d-134">Compiler option</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="d985d-135">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d985d-135">Visual Basic</span></span>|[<span data-ttu-id="d985d-136">/platform (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d985d-136">/platform (Visual Basic)</span></span>](~/docs/visual-basic/reference/command-line-compiler/platform.md)|  
|<span data-ttu-id="d985d-137">Visual C#</span><span class="sxs-lookup"><span data-stu-id="d985d-137">Visual C#</span></span>|[<span data-ttu-id="d985d-138">/platform (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="d985d-138">/platform (C# Compiler Options)</span></span>](~/docs/csharp/language-reference/compiler-options/platform-compiler-option.md)|  
|<span data-ttu-id="d985d-139">Visual C++</span><span class="sxs-lookup"><span data-stu-id="d985d-139">Visual C++</span></span>|<span data-ttu-id="d985d-140">您可以使用 **/clr:safe** 建立各平台適用的 Microsoft 中繼語言 (MSIL) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d985d-140">You can create platform-agnostic, Microsoft intermediate language (MSIL) applications by using **/clr:safe**.</span></span> <span data-ttu-id="d985d-141">如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](/cpp/build/reference/clr-common-language-runtime-compilation)。</span><span class="sxs-lookup"><span data-stu-id="d985d-141">For more information, see [/clr (Common Language Runtime Compilation)](/cpp/build/reference/clr-common-language-runtime-compilation).</span></span><br /><br /> <span data-ttu-id="d985d-142">Visual C++ 針對每個 64 位元作業系統包含了個別的編譯器。</span><span class="sxs-lookup"><span data-stu-id="d985d-142">Visual C++ includes a separate compiler for each 64-bit operating system.</span></span> <span data-ttu-id="d985d-143">如需如何使用 Visual C++ 建立可在 64 位元 Windows 作業系統上執行之原生應用程式的詳細資訊，請參閱 [64 位元程式設計](http://msdn.microsoft.com/library/h2k70f3s\(v=vs.80\))。</span><span class="sxs-lookup"><span data-stu-id="d985d-143">For more information about how to use Visual C++ to create native applications that run on a 64-bit Windows operating system, see [64-bit Programming](http://msdn.microsoft.com/library/h2k70f3s\(v=vs.80\)).</span></span>|  
  
## <a name="determining-the-status-of-an-exe-file-or-dll-file"></a><span data-ttu-id="d985d-144">判斷 .exe 檔或 .dll 檔的狀態</span><span class="sxs-lookup"><span data-stu-id="d985d-144">Determining the Status of an .exe File or .dll File</span></span>  
 <span data-ttu-id="d985d-145">若要判斷 .exe 檔或 .dll 檔案是否只能在特定平台上或在 WOW64 下執行，請使用不含選項的 [CorFlags.exe (CorFlags 轉換工具)](../../docs/framework/tools/corflags-exe-corflags-conversion-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="d985d-145">To determine whether an .exe file or .dll file is meant to run only on a specific platform or under WOW64, use [CorFlags.exe (CorFlags Conversion Tool)](../../docs/framework/tools/corflags-exe-corflags-conversion-tool.md) with no options.</span></span> <span data-ttu-id="d985d-146">您也可以使用 CorFlags.exe 來變更 .exe 檔或 .dll 檔的平台狀態。</span><span class="sxs-lookup"><span data-stu-id="d985d-146">You can also use CorFlags.exe to change the platform status of an .exe file or .dll file.</span></span> <span data-ttu-id="d985d-147">Visual Studio 組件的 CLR 標頭中的執行階段主要版本號碼設為 2，而執行階段次要版本號碼設為 5。</span><span class="sxs-lookup"><span data-stu-id="d985d-147">The CLR header of a Visual Studio assembly has the major runtime version number set to 2 and the minor runtime version number set to 5.</span></span> <span data-ttu-id="d985d-148">將次要執行階段版本設定為 0 的應用程式會被視為舊版應用程式，並一律在 WOW64 下執行。</span><span class="sxs-lookup"><span data-stu-id="d985d-148">Applications that have the minor runtime version set to 0 are treated as legacy applications and are always executed under WOW64.</span></span>  
  
 <span data-ttu-id="d985d-149">若要以程式設計方式查詢 .exe 或 .dll 以查看其是否只在特定平台上或在 WOW64 下執行，請使用 <xref:System.Reflection.Module.GetPEKind%2A?displayProperty=fullName> 方法。</span><span class="sxs-lookup"><span data-stu-id="d985d-149">To programmatically query an .exe or .dll to see whether it is meant to run only on a specific platform or under WOW64, use the <xref:System.Reflection.Module.GetPEKind%2A?displayProperty=fullName> method.</span></span>

