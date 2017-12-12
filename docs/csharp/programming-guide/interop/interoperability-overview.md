---
title: "互通性概觀 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- COM interop
- C# language, interoperability
- C++ Interop
- interoperability, about interoperability
- platform invoke
ms.assetid: c025b2e0-2357-4c27-8461-118f0090aeff
caps.latest.revision: "43"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b24a367eaf78ef520cc2dd54db6ad58b215179ad
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2017
---
# <a name="interoperability-overview-c-programming-guide"></a><span data-ttu-id="c5eb9-102">互通性概觀 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="c5eb9-102">Interoperability Overview (C# Programming Guide)</span></span>
<span data-ttu-id="c5eb9-103">本主題說明可在 C# Managed 程式碼和 Unmanaged 程式碼之間啟用互通性的方法。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-103">The topic describes methods to enable interoperability between C# managed code and unmanaged code.</span></span>  
  
## <a name="platform-invoke"></a><span data-ttu-id="c5eb9-104">平台叫用</span><span class="sxs-lookup"><span data-stu-id="c5eb9-104">Platform Invoke</span></span>  
 <span data-ttu-id="c5eb9-105">「平台叫用」服務，可讓 Managed 程式碼呼叫 Unmanaged 函式在動態連結程式庫 (DLL) 中實作，例如 Win32 API 中。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-105">*Platform invoke* is a service that enables managed code to call unmanaged functions that are implemented in dynamic link libraries (DLLs), such as those in the Microsoft Win32 API.</span></span> <span data-ttu-id="c5eb9-106">它會找出並叫用匯出的函式，並且在需要的時候於交互操作界限之間封送處理其引數 (整數、 字串、 陣列、 結構和其他) 。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-106">It locates and invokes an exported function and marshals its arguments (integers, strings, arrays, structures, and so on) across the interoperation boundary as needed.</span></span>  
  
 <span data-ttu-id="c5eb9-107">如需詳細資訊，請參閱[使用 Unmanaged DLL 函式](../../../framework/interop/consuming-unmanaged-dll-functions.md)和[如何：使用平台叫用播放 WAV 檔](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-107">For more information, see [Consuming Unmanaged DLL Functions](../../../framework/interop/consuming-unmanaged-dll-functions.md) and [How to: Use Platform Invoke to Play a Wave File](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5eb9-108">[Common Language Runtime](../../../standard/clr.md) (CLR) 管理對系統資源的存取。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-108">The [Common Language Runtime](../../../standard/clr.md) (CLR) manages access to system resources.</span></span> <span data-ttu-id="c5eb9-109">在 CLR 外部呼叫 Unmanaged 程式碼會略過此安全性機制，因而造成安全性風險。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-109">Calling unmanaged code that is outside the CLR bypasses this security mechanism, and therefore presents a security risk.</span></span> <span data-ttu-id="c5eb9-110">例如，Unmanaged 程式碼可能會直接呼叫 Unmanaged 程式碼中的資源，並略過 CLR 安全性機制。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-110">For example, unmanaged code might call resources in unmanaged code directly, bypassing CLR security mechanisms.</span></span> <span data-ttu-id="c5eb9-111">如需詳細資訊，請參閱 [.NET Framework 安全性](http://go.microsoft.com/fwlink/?LinkId=37122)。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-111">For more information, see [.NET Framework Security](http://go.microsoft.com/fwlink/?LinkId=37122).</span></span>  
  
## <a name="c-interop"></a><span data-ttu-id="c5eb9-112">C++ Interop</span><span class="sxs-lookup"><span data-stu-id="c5eb9-112">C++ Interop</span></span>  
 <span data-ttu-id="c5eb9-113">您可以使用 C++ Interop (也稱為 It Just Works (IJW)) 包裝原生 C++ 類別，以供使用 C# 或其他 .NET Framework 語言撰寫的程式碼取用。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-113">You can use C++ interop, also known as It Just Works (IJW), to wrap a native C++ class so that it can be consumed by code that is authored in C# or another .NET Framework language.</span></span> <span data-ttu-id="c5eb9-114">若要這樣做，您可以撰寫 C++ 程式碼來包裝原生 DLL 或 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-114">To do this, you write C++ code to wrap a native DLL or COM component.</span></span> <span data-ttu-id="c5eb9-115">不同於其他 .NET Framework 語言，[!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] 提供互通性支援，因此可將 Managed 和 Unmanaged 程式碼放置在相同的應用程式，甚至是相同的檔案中。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-115">Unlike other .NET Framework languages, [!INCLUDE[vcprvc](~/includes/vcprvc-md.md)] has interoperability support that enables managed and unmanaged code to be located in the same application and even in the same file.</span></span> <span data-ttu-id="c5eb9-116">您接著可使用 **/clr** 編譯器參數建立 C++ 程式碼，以產生 Managed 組件。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-116">You then build the C++ code by using the **/clr** compiler switch to produce a managed assembly.</span></span> <span data-ttu-id="c5eb9-117">最後，您可以在 C# 專案中新增組件的參考，並使用包裝的物件，就像是使用其他 Managed 類別一樣。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-117">Finally, you add a reference to the assembly in your C# project and use the wrapped objects just as you would use other managed classes.</span></span>  
  
## <a name="exposing-com-components-to-c"></a><span data-ttu-id="c5eb9-118">將 COM 元件公開給 C#</span><span class="sxs-lookup"><span data-stu-id="c5eb9-118">Exposing COM Components to C#</span></span>  
 <span data-ttu-id="c5eb9-119">您可以從 C# 專案取用 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-119">You can consume a COM component from a C# project.</span></span> <span data-ttu-id="c5eb9-120">一般步驟如下所示：</span><span class="sxs-lookup"><span data-stu-id="c5eb9-120">The general steps are as follows:</span></span>  
  
1.  <span data-ttu-id="c5eb9-121">找出並註冊所要使用的 COM 元件。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-121">Locate a COM component to use and register it.</span></span> <span data-ttu-id="c5eb9-122">使用 regsvr32.exe 註冊或取消註冊 COM DLL。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-122">Use regsvr32.exe to register or un–register a COM DLL.</span></span>  
  
2.  <span data-ttu-id="c5eb9-123">將 COM 元件或型別程式庫的參考新增至專案。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-123">Add to the project a reference to the COM component or type library.</span></span>  
  
     <span data-ttu-id="c5eb9-124">當您新增參考時，[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 會使用接受型別程式庫作為輸入的 [Tlbimp.exe (型別程式庫匯入工具)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)，以輸出 .NET Framework Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-124">When you add the reference, [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] uses the [Tlbimp.exe (Type Library Importer)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382), which takes a type library as input, to output a .NET Framework interop assembly.</span></span> <span data-ttu-id="c5eb9-125">此組件 (也稱為執行階段可呼叫包裝函式 (RCW)) 包含 Managed 類別和介面，以包裝型別程式庫中的 COM 類別和介面。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-125">The assembly, also named a runtime callable wrapper (RCW), contains managed classes and interfaces that wrap the COM classes and interfaces that are in the type library.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="c5eb9-126"> 會將產生的組件參考新增至專案。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-126"> adds to the project a reference to the generated assembly.</span></span>  
  
3.  <span data-ttu-id="c5eb9-127">建立定義於 RCW 之類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-127">Create an instance of a class that is defined in the RCW.</span></span> <span data-ttu-id="c5eb9-128">這會接著建立 COM 物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-128">This, in turn, creates an instance of the COM object.</span></span>  
  
4.  <span data-ttu-id="c5eb9-129">就像是使用其他 Managed 物件一樣來使用此物件。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-129">Use the object just as you use other managed objects.</span></span> <span data-ttu-id="c5eb9-130">當記憶體回收將物件回收時，也會從記憶體釋放 COM 物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-130">When the object is reclaimed by garbage collection, the instance of the COM object is also released from memory.</span></span>  
  
 <span data-ttu-id="c5eb9-131">如需詳細資訊，請參閱[將 COM 元件公開給 .NET Framework](http://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730)。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-131">For more information, see [Exposing COM Components to the .NET Framework](http://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730).</span></span>  
  
## <a name="exposing-c-to-com"></a><span data-ttu-id="c5eb9-132">將 C# 公開給 COM</span><span class="sxs-lookup"><span data-stu-id="c5eb9-132">Exposing C# to COM</span></span>  
 <span data-ttu-id="c5eb9-133">COM 用戶端可取用已正確公開的 C# 類型。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-133">COM clients can consume C# types that have been correctly exposed.</span></span> <span data-ttu-id="c5eb9-134">公開 C# 類型的基本步驟如下所示：</span><span class="sxs-lookup"><span data-stu-id="c5eb9-134">The basic steps to expose C# types are as follows:</span></span>  
  
1.  <span data-ttu-id="c5eb9-135">在 C# 專案中新增 Interop 屬性。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-135">Add interop attributes in the C# project.</span></span>  
  
     <span data-ttu-id="c5eb9-136">您可以藉由修改 [!INCLUDE[csprcs](~/includes/csprcs-md.md)] 專案屬性來顯示組件 COM。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-136">You can make an assembly COM visible by modifying [!INCLUDE[csprcs](~/includes/csprcs-md.md)] project properties.</span></span> <span data-ttu-id="c5eb9-137">如需詳細資訊，請參閱[組件資訊對話方塊](/visualstudio/ide/reference/assembly-information-dialog-box)。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-137">For more information, see [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box).</span></span>  
  
2.  <span data-ttu-id="c5eb9-138">產生 COM 型別程式庫並註冊供 COM 使用。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-138">Generate a COM type library and register it for COM usage.</span></span>  
  
     <span data-ttu-id="c5eb9-139">您可以修改 [!INCLUDE[csprcs](~/includes/csprcs-md.md)] 專案屬性，以自動為 COM Interop 註冊 C# 組件。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-139">You can modify [!INCLUDE[csprcs](~/includes/csprcs-md.md)] project properties to automatically register the C# assembly for COM interop.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="c5eb9-140"> 使用 [Regasm.exe (組件登錄工具)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)，並使用接受 Managed 組件作為輸入的 `/tlb` 命令列參數，以產生型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-140"> uses the [Regasm.exe (Assembly Registration Tool)](http://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb), using the `/tlb` command-line switch, which takes a managed assembly as input, to generate a type library.</span></span> <span data-ttu-id="c5eb9-141">此型別程式庫描述組件中的 `public` 類型，並新增登錄項目，讓 COM 用戶端可以建立 Managed 類別。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-141">This type library describes the `public` types in the assembly and adds registry entries so that COM clients can create managed classes.</span></span>  
  
 <span data-ttu-id="c5eb9-142">如需詳細資訊，請參閱[將 .NET Framework 元件公開給 COM](http://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6) 和[範例 COM 類別](../../../csharp/programming-guide/interop/example-com-class.md)。</span><span class="sxs-lookup"><span data-stu-id="c5eb9-142">For more information, see [Exposing .NET Framework Components to COM](http://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6) and [Example COM Class](../../../csharp/programming-guide/interop/example-com-class.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5eb9-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5eb9-143">See Also</span></span>  
 <span data-ttu-id="c5eb9-144">[Improving Interop Performance](http://go.microsoft.com/fwlink/?LinkId=99564) (提升 Interop 效能)</span><span class="sxs-lookup"><span data-stu-id="c5eb9-144">[Improving Interop Performance](http://go.microsoft.com/fwlink/?LinkId=99564)</span></span>  
 [<span data-ttu-id="c5eb9-145">COM Interop 簡介</span><span class="sxs-lookup"><span data-stu-id="c5eb9-145">Introduction to COM Interop</span></span>](http://go.microsoft.com/fwlink/?LinkId=112406)  
 [<span data-ttu-id="c5eb9-146">在受控碼和非受控碼之間進行封送處理</span><span class="sxs-lookup"><span data-stu-id="c5eb9-146">Marshaling between Managed and Unmanaged Code</span></span>](http://go.microsoft.com/fwlink/?LinkId=112398)  
 [<span data-ttu-id="c5eb9-147">與 Unmanaged 程式碼互通</span><span class="sxs-lookup"><span data-stu-id="c5eb9-147">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="c5eb9-148">進階 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="c5eb9-148">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="c5eb9-149">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c5eb9-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
