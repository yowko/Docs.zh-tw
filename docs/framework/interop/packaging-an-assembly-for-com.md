---
title: 封裝 COM 的 .NET Framework 組件
description: 封裝 COM 的 .NET 元件。 收集 COM 應用程式可以取用的類型清單、版本控制和部署指示，以及類型程式庫。
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
ms.openlocfilehash: 4963892419fd1caec4483123f820d62967a87dd6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620829"
---
# <a name="packaging-a-net-framework-assembly-for-com"></a><span data-ttu-id="ba560-104">封裝 COM 的 .NET Framework 組件</span><span class="sxs-lookup"><span data-stu-id="ba560-104">Packaging a .NET Framework Assembly for COM</span></span>

<span data-ttu-id="ba560-105">COM 開發人員可以獲益於他們要併入其應用程式之 Managed 類型的下列資訊：</span><span class="sxs-lookup"><span data-stu-id="ba560-105">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>

- <span data-ttu-id="ba560-106">COM 應用程式可使用的類型清單</span><span class="sxs-lookup"><span data-stu-id="ba560-106">A list of types that COM applications can consume</span></span>

  <span data-ttu-id="ba560-107">COM 看不到一些 Managed 類型、有些看得到但無法建立，但有些是可見並可建立。</span><span class="sxs-lookup"><span data-stu-id="ba560-107">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="ba560-108">組件可以包含任意的不可見、可見、不可建立和可建立類型組合。</span><span class="sxs-lookup"><span data-stu-id="ba560-108">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="ba560-109">為求完整性，識別組件中想要公開至 COM 的類型，特別是這些類型是公開至 .NET Framework 之類型的子集。</span><span class="sxs-lookup"><span data-stu-id="ba560-109">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>

  <span data-ttu-id="ba560-110">如需詳細資訊，請參閱[限定交互操作的 .NET 類型](../../standard/native-interop/qualify-net-types-for-interoperation.md)。</span><span class="sxs-lookup"><span data-stu-id="ba560-110">For additional information, see [Qualifying .NET Types for Interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

- <span data-ttu-id="ba560-111">版本設定指示</span><span class="sxs-lookup"><span data-stu-id="ba560-111">Versioning instructions</span></span>

  <span data-ttu-id="ba560-112">可實作類別介面 (COM Interop 產生的介面) 的 Managed 類別受到版本設定限制。</span><span class="sxs-lookup"><span data-stu-id="ba560-112">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>

  <span data-ttu-id="ba560-113">如需使用類別介面的指導方針，請參閱[類別介面簡介](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)。</span><span class="sxs-lookup"><span data-stu-id="ba560-113">For guidelines on using the class interface, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>

- <span data-ttu-id="ba560-114">部署指示</span><span class="sxs-lookup"><span data-stu-id="ba560-114">Deployment instructions</span></span>

  <span data-ttu-id="ba560-115">發行者所簽署的強式名稱組件可以安裝到全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="ba560-115">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="ba560-116">未簽署的組件必須安裝在使用者電腦上，當成私用組件。</span><span class="sxs-lookup"><span data-stu-id="ba560-116">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>

  <span data-ttu-id="ba560-117">如需詳細資訊，請參閱[組件安全性考量](../../standard/assembly/security-considerations.md)。</span><span class="sxs-lookup"><span data-stu-id="ba560-117">For additional information, see [Assembly Security Considerations](../../standard/assembly/security-considerations.md).</span></span>

- <span data-ttu-id="ba560-118">型別程式庫包含</span><span class="sxs-lookup"><span data-stu-id="ba560-118">Type library inclusion</span></span>

  <span data-ttu-id="ba560-119">COM 應用程式使用時，大部分類型都需要型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="ba560-119">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="ba560-120">您可以產生型別程式庫，或讓 COM 開發人員執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="ba560-120">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="ba560-121">Windows SDK 提供下列選項來產生型別程式庫：</span><span class="sxs-lookup"><span data-stu-id="ba560-121">The Windows SDK provides the following options for generating a type library:</span></span>

  - [<span data-ttu-id="ba560-122">型別程式庫匯出工具</span><span class="sxs-lookup"><span data-stu-id="ba560-122">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)

  - [<span data-ttu-id="ba560-123">TypeLibConverter 類別</span><span class="sxs-lookup"><span data-stu-id="ba560-123">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)

  - [<span data-ttu-id="ba560-124">組件註冊工具</span><span class="sxs-lookup"><span data-stu-id="ba560-124">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)

  - [<span data-ttu-id="ba560-125">.NET 服務安裝工具</span><span class="sxs-lookup"><span data-stu-id="ba560-125">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)

  <span data-ttu-id="ba560-126">不論您選擇的機制為何，只有所提供組件中定義的公用類型才會包含在所產生的型別程式庫中。</span><span class="sxs-lookup"><span data-stu-id="ba560-126">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>

<span data-ttu-id="ba560-127">如需指示，請參閱[如何：將型別程式庫當作 Win32 資源內嵌在 .NET 架構應用程式中](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="ba560-127">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span></span>

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a><span data-ttu-id="ba560-128">類型程式庫匯出工具</span><span class="sxs-lookup"><span data-stu-id="ba560-128">Type Library Exporter</span></span>

<span data-ttu-id="ba560-129">[型別程式庫匯出工具 (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) 是一種命令列工具，可將組件中所含的類別和介面轉換成 COM 型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="ba560-129">The [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="ba560-130">有類別的類型資訊可用之後，COM 用戶端就可以建立 .NET 類別執行個體，並呼叫執行個體的方法，就像它是 COM 物件一樣。</span><span class="sxs-lookup"><span data-stu-id="ba560-130">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="ba560-131">Tlbexp.exe 一次會轉換整個組件。</span><span class="sxs-lookup"><span data-stu-id="ba560-131">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="ba560-132">您無法使用 Tlbexp.exe 來為組件中所定義的類型子集產生類型資訊。</span><span class="sxs-lookup"><span data-stu-id="ba560-132">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a><span data-ttu-id="ba560-133">TypeLibConverter 類別</span><span class="sxs-lookup"><span data-stu-id="ba560-133">TypeLibConverter Class</span></span>

<span data-ttu-id="ba560-134">位於 **System.Runtime.Interop** 命名空間中的 <xref:System.Runtime.InteropServices.TypeLibConverter> 類別會將組件中所含的類別和介面轉換成 COM 型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="ba560-134">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="ba560-135">此 API 會產生與型別程式庫匯出工具相同的類型資訊 (如上節所述)。</span><span class="sxs-lookup"><span data-stu-id="ba560-135">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>

<span data-ttu-id="ba560-136">**TypeLibConverter class** 實作 <xref:System.Runtime.InteropServices.ITypeLibConverter>。</span><span class="sxs-lookup"><span data-stu-id="ba560-136">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a><span data-ttu-id="ba560-137">組件註冊工具</span><span class="sxs-lookup"><span data-stu-id="ba560-137">Assembly Registration Tool</span></span>

<span data-ttu-id="ba560-138">當您套用 **/tlb:** 選項時，[組件註冊工具 (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) 可以產生和註冊型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="ba560-138">The [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="ba560-139">COM 用戶端需要在 Windows 登錄中安裝型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="ba560-139">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="ba560-140">沒有這個選項時，Regasm.exe 只會在組件中註冊類型，而不是型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="ba560-140">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="ba560-141">在組件中註冊類型以及在型別程式庫中註冊類型是不同的活動。</span><span class="sxs-lookup"><span data-stu-id="ba560-141">Registering the types in an assembly and registering the type library are distinct activities.</span></span>

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a><span data-ttu-id="ba560-142">.NET 服務安裝工具</span><span class="sxs-lookup"><span data-stu-id="ba560-142">.NET Services Installation Tool</span></span>

<span data-ttu-id="ba560-143">[.NET 服務安裝工具 (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) 會將 Managed 類別新增至 Windows 2000 元件服務，並將數項工作合併到單一工具。</span><span class="sxs-lookup"><span data-stu-id="ba560-143">The [.NET Services Installation Tool (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="ba560-144">除了載入和註冊組件之外，Regsvcs.exe 還可以在現有 COM+ 1.0 應用程式中產生、註冊和安裝型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="ba560-144">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba560-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba560-145">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [<span data-ttu-id="ba560-146">將 .NET Framework 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="ba560-146">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="ba560-147">限定交互操作的 .NET 類型</span><span class="sxs-lookup"><span data-stu-id="ba560-147">Qualifying .NET Types for Interoperation</span></span>](../../standard/native-interop/qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="ba560-148">類別介面簡介</span><span class="sxs-lookup"><span data-stu-id="ba560-148">Introducing the class interface</span></span>](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="ba560-149">元件安全性考慮</span><span class="sxs-lookup"><span data-stu-id="ba560-149">Assembly Security Considerations</span></span>](../../standard/assembly/security-considerations.md)
- [<span data-ttu-id="ba560-150">Tlbexp.exe （類型程式庫匯出工具）</span><span class="sxs-lookup"><span data-stu-id="ba560-150">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="ba560-151">向 COM 註冊組件</span><span class="sxs-lookup"><span data-stu-id="ba560-151">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="ba560-152">[如何：將型別程式庫當作 Win32 資源內嵌在應用程式中](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ba560-152">[How to: Embed Type Libraries as Win32 Resources in Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span></span>
