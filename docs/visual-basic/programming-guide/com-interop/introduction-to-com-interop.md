---
title: COM Interop 簡介
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: 7bfbf0c6de8519e91a458ab4cbb5693024cdbeb2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090387"
---
# <a name="introduction-to-com-interop-visual-basic"></a><span data-ttu-id="30dc5-102">COM Interop 簡介 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30dc5-102">Introduction to COM Interop (Visual Basic)</span></span>

<span data-ttu-id="30dc5-103">元件物件模型 (COM) 可讓物件向其他元件公開其功能，以及裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="30dc5-103">The Component Object Model (COM) lets an object expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="30dc5-104">雖然 COM 物件在許多方面都是 Windows 程式設計的基礎，但是針對 common language runtime (CLR) 所設計的應用程式提供許多優點。</span><span class="sxs-lookup"><span data-stu-id="30dc5-104">While COM objects have been fundamental to Windows programming for many years, applications designed for the common language runtime (CLR) offer many advantages.</span></span>  
  
 <span data-ttu-id="30dc5-105">.NET Framework 的應用程式最終會取代以 COM 開發的應用程式。</span><span class="sxs-lookup"><span data-stu-id="30dc5-105">.NET Framework applications will eventually replace those developed with COM.</span></span> <span data-ttu-id="30dc5-106">在那之前，您可能必須使用 Visual Studio 來使用或建立 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="30dc5-106">Until then, you may have to use or create COM objects by using Visual Studio.</span></span> <span data-ttu-id="30dc5-107">與 COM 或 *com interop*的互通性，可讓您使用現有的 COM 物件，並以您自己的步調轉換至 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="30dc5-107">Interoperability with COM, or *COM interop*, enables you to use existing COM objects while transitioning to the .NET Framework at your own pace.</span></span>  
  
 <span data-ttu-id="30dc5-108">使用 .NET Framework 來建立 COM 元件時，您可以使用無註冊的 COM interop。</span><span class="sxs-lookup"><span data-stu-id="30dc5-108">By using the .NET Framework to create COM components, you can use registration-free COM interop.</span></span> <span data-ttu-id="30dc5-109">這可讓您在電腦上安裝多個版本時，控制已啟用的 DLL 版本，並讓使用者使用 XCOPY 或 FTP 將應用程式複製到其電腦上可執行檔適當目錄。</span><span class="sxs-lookup"><span data-stu-id="30dc5-109">This lets you control which DLL version is enabled when more than one version is installed on a computer, and lets end users use XCOPY or FTP to copy your application to an appropriate directory on their computer where it can be run.</span></span> <span data-ttu-id="30dc5-110">如需詳細資訊，請參閱 [免註冊的 COM Interop](../../../framework/interop/registration-free-com-interop.md)。</span><span class="sxs-lookup"><span data-stu-id="30dc5-110">For more information, see [Registration-Free COM Interop](../../../framework/interop/registration-free-com-interop.md).</span></span>  
  
## <a name="managed-code-and-data"></a><span data-ttu-id="30dc5-111">Managed 程式碼和資料</span><span class="sxs-lookup"><span data-stu-id="30dc5-111">Managed Code and Data</span></span>  

 <span data-ttu-id="30dc5-112">針對 .NET Framework 開發的程式碼稱為 managed 程式 *代碼*，其中包含 CLR 所使用的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="30dc5-112">Code developed for the .NET Framework is referred to as *managed code*, and contains metadata that is used by the CLR.</span></span> <span data-ttu-id="30dc5-113">.NET Framework 的應用程式所使用的資料稱為 *managed 資料* ，因為執行時間會管理與資料相關的工作，例如配置和回收記憶體以及執行類型檢查。</span><span class="sxs-lookup"><span data-stu-id="30dc5-113">Data used by .NET Framework applications is called *managed data* because the runtime manages data-related tasks such as allocating and reclaiming memory and performing type checking.</span></span> <span data-ttu-id="30dc5-114">根據預設，Visual Basic .NET 會使用 managed 程式碼和資料，但您可以使用 interop 元件存取非受控程式碼和 COM 物件的資料， (稍後在此頁面) 所述。</span><span class="sxs-lookup"><span data-stu-id="30dc5-114">By default, Visual Basic .NET uses managed code and data, but you can access the unmanaged code and data of COM objects using interop assemblies (described later on this page).</span></span>  
  
## <a name="assemblies"></a><span data-ttu-id="30dc5-115">組件</span><span class="sxs-lookup"><span data-stu-id="30dc5-115">Assemblies</span></span>  

 <span data-ttu-id="30dc5-116">元件是 .NET Framework 應用程式的主要組建區塊。</span><span class="sxs-lookup"><span data-stu-id="30dc5-116">An assembly is the primary building block of a .NET Framework application.</span></span> <span data-ttu-id="30dc5-117">它是一組功能的集合，可建立、建立版本，並部署為包含一或多個檔案的單一執行單位。</span><span class="sxs-lookup"><span data-stu-id="30dc5-117">It is a collection of functionality that is built, versioned, and deployed as a single implementation unit containing one or more files.</span></span> <span data-ttu-id="30dc5-118">每個元件都包含一個組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="30dc5-118">Each assembly contains an assembly manifest.</span></span>  
  
## <a name="type-libraries-and-assembly-manifests"></a><span data-ttu-id="30dc5-119">類型程式庫和組件資訊清單</span><span class="sxs-lookup"><span data-stu-id="30dc5-119">Type Libraries and Assembly Manifests</span></span>  

 <span data-ttu-id="30dc5-120">類型程式庫描述 COM 物件的特性，例如成員名稱和資料類型。</span><span class="sxs-lookup"><span data-stu-id="30dc5-120">Type libraries describe characteristics of COM objects, such as member names and data types.</span></span> <span data-ttu-id="30dc5-121">元件資訊清單對 .NET Framework 的應用程式執行相同的功能。</span><span class="sxs-lookup"><span data-stu-id="30dc5-121">Assembly manifests perform the same function for .NET Framework applications.</span></span> <span data-ttu-id="30dc5-122">其中包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="30dc5-122">They include information about the following:</span></span>  
  
- <span data-ttu-id="30dc5-123">元件身分識別、版本、文化特性和數位簽章。</span><span class="sxs-lookup"><span data-stu-id="30dc5-123">Assembly identity, version, culture, and digital signature.</span></span>  
  
- <span data-ttu-id="30dc5-124">組成元件執行的檔案。</span><span class="sxs-lookup"><span data-stu-id="30dc5-124">Files that make up the assembly implementation.</span></span>  
  
- <span data-ttu-id="30dc5-125">組成元件的類型和資源。</span><span class="sxs-lookup"><span data-stu-id="30dc5-125">Types and resources that make up the assembly.</span></span> <span data-ttu-id="30dc5-126">這包括從它匯出的檔案。</span><span class="sxs-lookup"><span data-stu-id="30dc5-126">This includes those that are exported from it.</span></span>  
  
- <span data-ttu-id="30dc5-127">其他元件的編譯時間相依性。</span><span class="sxs-lookup"><span data-stu-id="30dc5-127">Compile-time dependencies on other assemblies.</span></span>  
  
- <span data-ttu-id="30dc5-128">正確執行元件所需的許可權。</span><span class="sxs-lookup"><span data-stu-id="30dc5-128">Permissions required for the assembly to run correctly.</span></span>  
  
 <span data-ttu-id="30dc5-129">如需元件和元件資訊清單的詳細資訊，請參閱 [.net 中的元件](../../../standard/assembly/index.md)。</span><span class="sxs-lookup"><span data-stu-id="30dc5-129">For more information about assemblies and assembly manifests, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
### <a name="importing-and-exporting-type-libraries"></a><span data-ttu-id="30dc5-130">匯入和匯出類型程式庫</span><span class="sxs-lookup"><span data-stu-id="30dc5-130">Importing and Exporting Type Libraries</span></span>  

 <span data-ttu-id="30dc5-131">Visual Studio 包含一個公用程式 Tlbimp.exe，可讓您將型別程式庫中的資訊匯入 .NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="30dc5-131">Visual Studio contains a utility, Tlbimp, that lets you import information from a type library into a .NET Framework application.</span></span> <span data-ttu-id="30dc5-132">您可以使用 Tlbexp.exe 公用程式從元件產生類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="30dc5-132">You can generate type libraries from assemblies by using the Tlbexp utility.</span></span>  
  
 <span data-ttu-id="30dc5-133">如需 Tlbimp.exe 和 Tlbexp.exe 的詳細資訊，請參閱 [Tlbimp.exe (型別程式庫匯入工具) ](../../../framework/tools/tlbimp-exe-type-library-importer.md) 和 [Tlbexp.exe (型別程式庫匯出工具) ](../../../framework/tools/tlbexp-exe-type-library-exporter.md)。</span><span class="sxs-lookup"><span data-stu-id="30dc5-133">For information about Tlbimp and Tlbexp, see [Tlbimp.exe (Type Library Importer)](../../../framework/tools/tlbimp-exe-type-library-importer.md) and [Tlbexp.exe (Type Library Exporter)](../../../framework/tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="30dc5-134">Interop 元件</span><span class="sxs-lookup"><span data-stu-id="30dc5-134">Interop Assemblies</span></span>  

 <span data-ttu-id="30dc5-135">Interop 元件是在 managed 和非受控碼之間橋接的 .NET Framework 元件，將 COM 物件成員對應至相等的 .NET Framework managed 成員。</span><span class="sxs-lookup"><span data-stu-id="30dc5-135">Interop assemblies are .NET Framework assemblies that bridge between managed and unmanaged code, mapping COM object members to equivalent .NET Framework managed members.</span></span> <span data-ttu-id="30dc5-136">Visual Basic .NET 所建立的 Interop 元件會處理許多使用 COM 物件的詳細資料，例如互通性封送處理。</span><span class="sxs-lookup"><span data-stu-id="30dc5-136">Interop assemblies created by Visual Basic .NET handle many of the details of working with COM objects, such as interoperability marshaling.</span></span>  
  
## <a name="interoperability-marshaling"></a><span data-ttu-id="30dc5-137">互通性封送處理</span><span class="sxs-lookup"><span data-stu-id="30dc5-137">Interoperability Marshaling</span></span>  

 <span data-ttu-id="30dc5-138">所有 .NET Framework 的應用程式都共用一組通用類型，可啟用物件的互通性，不論使用的程式設計語言為何。</span><span class="sxs-lookup"><span data-stu-id="30dc5-138">All .NET Framework applications share a set of common types that enable interoperability of objects, regardless of the programming language that is used.</span></span> <span data-ttu-id="30dc5-139">COM 物件的參數和傳回值有時會使用與 managed 程式碼中所使用的資料類型不同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="30dc5-139">The parameters and return values of COM objects sometimes use data types that differ from those used in managed code.</span></span> <span data-ttu-id="30dc5-140">*互通性封送處理* 是指將參數和傳回值，在與 COM 物件來回移動的相等資料類型中封裝的程式。</span><span class="sxs-lookup"><span data-stu-id="30dc5-140">*Interoperability marshaling* is the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="30dc5-141">如需詳細資訊，請參閱 [Interop 封送處理](../../../framework/interop/interop-marshaling.md)。</span><span class="sxs-lookup"><span data-stu-id="30dc5-141">For more information, see [Interop Marshaling](../../../framework/interop/interop-marshaling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30dc5-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30dc5-142">See also</span></span>

- [<span data-ttu-id="30dc5-143">COM Interop</span><span class="sxs-lookup"><span data-stu-id="30dc5-143">COM Interop</span></span>](index.md)
- [<span data-ttu-id="30dc5-144">逐步解說：實作 COM 物件的繼承</span><span class="sxs-lookup"><span data-stu-id="30dc5-144">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="30dc5-145">與 Unmanaged 程式碼互通</span><span class="sxs-lookup"><span data-stu-id="30dc5-145">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="30dc5-146">疑難排解互通性的問題</span><span class="sxs-lookup"><span data-stu-id="30dc5-146">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)
- [<span data-ttu-id="30dc5-147">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="30dc5-147">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="30dc5-148">Tlbimp.exe (類型程式庫匯入工具)</span><span class="sxs-lookup"><span data-stu-id="30dc5-148">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="30dc5-149">Tlbexp.exe (類型程式庫匯出工具)</span><span class="sxs-lookup"><span data-stu-id="30dc5-149">Tlbexp.exe (Type Library Exporter)</span></span>](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="30dc5-150">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="30dc5-150">Interop Marshaling</span></span>](../../../framework/interop/interop-marshaling.md)
- [<span data-ttu-id="30dc5-151">免註冊的 COM Interop</span><span class="sxs-lookup"><span data-stu-id="30dc5-151">Registration-Free COM Interop</span></span>](../../../framework/interop/registration-free-com-interop.md)
