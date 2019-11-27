---
title: IALink 介面
ms.date: 03/30/2017
f1_keywords:
- IALink
helpviewer_keywords:
- IALink interface
ms.assetid: 50abd02d-6488-4815-999b-4fb89af4d568
ms.openlocfilehash: 73b6bb9eac3f706df5cb1fd63b2f67c9791c8ed2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441813"
---
# <a name="ialink-interface"></a><span data-ttu-id="fd288-102">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="fd288-102">IALink Interface</span></span>
<span data-ttu-id="fd288-103">有助於 .NET Framework 元件的建立。</span><span class="sxs-lookup"><span data-stu-id="fd288-103">Helps in constructing .NET Framework assemblies.</span></span> <span data-ttu-id="fd288-104">除此之外，介面包含的方法可協助您撰寫多模組元件的組件資訊清單、以強式名稱簽署元件，以及建立 .netmodule。</span><span class="sxs-lookup"><span data-stu-id="fd288-104">Among other things, the interface contains methods that assist in writing assembly manifests for multi-module assemblies, signing assemblies with strong names, and creating netmodules.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fd288-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="fd288-105">In This Section</span></span>  
 [<span data-ttu-id="fd288-106">AddFile 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-106">AddFile Method</span></span>](addfile-method.md)  
  
 [<span data-ttu-id="fd288-107">AddImport 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-107">AddImport Method</span></span>](addimport-method.md)  
  
 [<span data-ttu-id="fd288-108">CloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-108">CloseAssembly Method</span></span>](closeassembly-method.md)  
  
 [<span data-ttu-id="fd288-109">CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-109">CloseEnum Method</span></span>](closeenum-method.md)  
  
 [<span data-ttu-id="fd288-110">EmbedResource 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-110">EmbedResource Method</span></span>](embedresource-method.md)  
  
 [<span data-ttu-id="fd288-111">EmitAssemblyCustomAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-111">EmitAssemblyCustomAttribute Method</span></span>](emitassemblycustomattribute-method.md)  
  
 [<span data-ttu-id="fd288-112">EmitManifest 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-112">EmitManifest Method</span></span>](emitmanifest-method.md)  
  
 [<span data-ttu-id="fd288-113">EndMerge 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-113">EndMerge Method</span></span>](endmerge-method.md)  
  
 [<span data-ttu-id="fd288-114">EnumCustomAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-114">EnumCustomAttributes Method</span></span>](enumcustomattributes-method.md)  
  
 [<span data-ttu-id="fd288-115">EnumImportTypes 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-115">EnumImportTypes Method</span></span>](enumimporttypes-method.md)  
  
 [<span data-ttu-id="fd288-116">ExportNestedType 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-116">ExportNestedType Method</span></span>](exportnestedtype-method.md)  
  
 [<span data-ttu-id="fd288-117">ExportNestedTypeForwarder 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-117">ExportNestedTypeForwarder Method</span></span>](exportnestedtypeforwarder-method.md)  
  
 [<span data-ttu-id="fd288-118">ExportType 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-118">ExportType Method</span></span>](exporttype-method.md)  
  
 [<span data-ttu-id="fd288-119">ExportTypeForwarder 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-119">ExportTypeForwarder Method</span></span>](exporttypeforwarder-method.md)  
  
 [<span data-ttu-id="fd288-120">FreeWin32ResBlob 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-120">FreeWin32ResBlob Method</span></span>](freewin32resblob-method.md)  
  
 [<span data-ttu-id="fd288-121">GetAssemblyRefHash 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-121">GetAssemblyRefHash Method</span></span>](getassemblyrefhash-method.md)  
  
 [<span data-ttu-id="fd288-122">GetResolutionScope 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-122">GetResolutionScope Method</span></span>](getresolutionscope-method.md)  
  
 [<span data-ttu-id="fd288-123">GetScope 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-123">GetScope Method</span></span>](getscope-method.md)  
  
 [<span data-ttu-id="fd288-124">GetWin32ResBlob 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-124">GetWin32ResBlob Method</span></span>](getwin32resblob-method.md)  
  
 [<span data-ttu-id="fd288-125">ImportFile 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-125">ImportFile Method</span></span>](importfile-method.md)  
  
 [<span data-ttu-id="fd288-126">ImportFile2 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-126">ImportFile2 Method</span></span>](importfile2-method.md)  
  
 [<span data-ttu-id="fd288-127">ImportTypes 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-127">ImportTypes Method</span></span>](importtypes-method.md)  
  
 <span data-ttu-id="fd288-128">"Init Method"</span><span class="sxs-lookup"><span data-stu-id="fd288-128">"Init Method"</span></span>  
  
 [<span data-ttu-id="fd288-129">LinkResource 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-129">LinkResource Method</span></span>](linkresource-method.md)  
  
 [<span data-ttu-id="fd288-130">PreCloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-130">PreCloseAssembly Method</span></span>](precloseassembly-method.md)  
  
 [<span data-ttu-id="fd288-131">SetAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-131">SetAssemblyFile Method</span></span>](setassemblyfile-method.md)  
  
 [<span data-ttu-id="fd288-132">SetAssemblyProps 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-132">SetAssemblyProps Method</span></span>](setassemblyprops-method.md)  
  
 [<span data-ttu-id="fd288-133">SetNonAssemblyFlags 方法</span><span class="sxs-lookup"><span data-stu-id="fd288-133">SetNonAssemblyFlags Method</span></span>](setnonassemblyflags-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="fd288-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd288-134">See also</span></span>

- [<span data-ttu-id="fd288-135">ALink API</span><span class="sxs-lookup"><span data-stu-id="fd288-135">ALink API</span></span>](index.md)
- [<span data-ttu-id="fd288-136">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="fd288-136">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="fd288-137">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="fd288-137">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
