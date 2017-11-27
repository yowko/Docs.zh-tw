---
title: "IALink 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: IALink
helpviewer_keywords: IALink interface
ms.assetid: 50abd02d-6488-4815-999b-4fb89af4d568
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8864e33fa281f69b72af12276ed31e5e543045ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ialink-interface"></a><span data-ttu-id="19582-102">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="19582-102">IALink Interface</span></span>
<span data-ttu-id="19582-103">可協助建構.NET Framework 組件。</span><span class="sxs-lookup"><span data-stu-id="19582-103">Helps in constructing .NET Framework assemblies.</span></span> <span data-ttu-id="19582-104">在其他方面，介面包含協助您撰寫多模組組件的組件資訊清單、 簽署組件具有強式名稱，以及建立的 netmodule 中的方法。</span><span class="sxs-lookup"><span data-stu-id="19582-104">Among other things, the interface contains methods that assist in writing assembly manifests for multi-module assemblies, signing assemblies with strong names, and creating netmodules.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="19582-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="19582-105">In This Section</span></span>  
 [<span data-ttu-id="19582-106">AddFile Method1</span><span class="sxs-lookup"><span data-stu-id="19582-106">AddFile Method1</span></span>](../../../../docs/framework/unmanaged-api/alink/addfile-method.md)  
  
 [<span data-ttu-id="19582-107">AddImport Method1</span><span class="sxs-lookup"><span data-stu-id="19582-107">AddImport Method1</span></span>](../../../../docs/framework/unmanaged-api/alink/addimport-method.md)  
  
 [<span data-ttu-id="19582-108">CloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="19582-108">CloseAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/alink/closeassembly-method.md)  
  
 [<span data-ttu-id="19582-109">CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="19582-109">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/alink/closeenum-method.md)  
  
 [<span data-ttu-id="19582-110">EmbedResource 方法</span><span class="sxs-lookup"><span data-stu-id="19582-110">EmbedResource Method</span></span>](../../../../docs/framework/unmanaged-api/alink/embedresource-method.md)  
  
 [<span data-ttu-id="19582-111">EmitAssemblyCustomAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="19582-111">EmitAssemblyCustomAttribute Method</span></span>](../../../../docs/framework/unmanaged-api/alink/emitassemblycustomattribute-method.md)  
  
 [<span data-ttu-id="19582-112">EmitManifest 方法</span><span class="sxs-lookup"><span data-stu-id="19582-112">EmitManifest Method</span></span>](../../../../docs/framework/unmanaged-api/alink/emitmanifest-method.md)  
  
 [<span data-ttu-id="19582-113">EndMerge 方法</span><span class="sxs-lookup"><span data-stu-id="19582-113">EndMerge Method</span></span>](../../../../docs/framework/unmanaged-api/alink/endmerge-method.md)  
  
 [<span data-ttu-id="19582-114">EnumCustomAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="19582-114">EnumCustomAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/alink/enumcustomattributes-method.md)  
  
 [<span data-ttu-id="19582-115">EnumImportTypes 方法</span><span class="sxs-lookup"><span data-stu-id="19582-115">EnumImportTypes Method</span></span>](../../../../docs/framework/unmanaged-api/alink/enumimporttypes-method.md)  
  
 [<span data-ttu-id="19582-116">ExportNestedType 方法</span><span class="sxs-lookup"><span data-stu-id="19582-116">ExportNestedType Method</span></span>](../../../../docs/framework/unmanaged-api/alink/exportnestedtype-method.md)  
  
 [<span data-ttu-id="19582-117">ExportNestedTypeForwarder 方法</span><span class="sxs-lookup"><span data-stu-id="19582-117">ExportNestedTypeForwarder Method</span></span>](../../../../docs/framework/unmanaged-api/alink/exportnestedtypeforwarder-method.md)  
  
 [<span data-ttu-id="19582-118">ExportType 方法</span><span class="sxs-lookup"><span data-stu-id="19582-118">ExportType Method</span></span>](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md)  
  
 [<span data-ttu-id="19582-119">ExportTypeForwarder 方法</span><span class="sxs-lookup"><span data-stu-id="19582-119">ExportTypeForwarder Method</span></span>](../../../../docs/framework/unmanaged-api/alink/exporttypeforwarder-method.md)  
  
 [<span data-ttu-id="19582-120">FreeWin32ResBlob 方法</span><span class="sxs-lookup"><span data-stu-id="19582-120">FreeWin32ResBlob Method</span></span>](../../../../docs/framework/unmanaged-api/alink/freewin32resblob-method.md)  
  
 [<span data-ttu-id="19582-121">GetAssemblyRefHash 方法</span><span class="sxs-lookup"><span data-stu-id="19582-121">GetAssemblyRefHash Method</span></span>](../../../../docs/framework/unmanaged-api/alink/getassemblyrefhash-method.md)  
  
 [<span data-ttu-id="19582-122">GetResolutionScope 方法</span><span class="sxs-lookup"><span data-stu-id="19582-122">GetResolutionScope Method</span></span>](../../../../docs/framework/unmanaged-api/alink/getresolutionscope-method.md)  
  
 [<span data-ttu-id="19582-123">GetScope Method1</span><span class="sxs-lookup"><span data-stu-id="19582-123">GetScope Method1</span></span>](../../../../docs/framework/unmanaged-api/alink/getscope-method.md)  
  
 [<span data-ttu-id="19582-124">GetWin32ResBlob 方法</span><span class="sxs-lookup"><span data-stu-id="19582-124">GetWin32ResBlob Method</span></span>](../../../../docs/framework/unmanaged-api/alink/getwin32resblob-method.md)  
  
 [<span data-ttu-id="19582-125">ImportFile 方法</span><span class="sxs-lookup"><span data-stu-id="19582-125">ImportFile Method</span></span>](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)  
  
 [<span data-ttu-id="19582-126">ImportFile2 方法</span><span class="sxs-lookup"><span data-stu-id="19582-126">ImportFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/alink/importfile2-method.md)  
  
 [<span data-ttu-id="19582-127">ImportTypes 方法</span><span class="sxs-lookup"><span data-stu-id="19582-127">ImportTypes Method</span></span>](../../../../docs/framework/unmanaged-api/alink/importtypes-method.md)  
  
 <span data-ttu-id="19582-128">< Init 方法 ></span><span class="sxs-lookup"><span data-stu-id="19582-128">"Init Method"</span></span>  
  
 [<span data-ttu-id="19582-129">LinkResource 方法</span><span class="sxs-lookup"><span data-stu-id="19582-129">LinkResource Method</span></span>](../../../../docs/framework/unmanaged-api/alink/linkresource-method.md)  
  
 [<span data-ttu-id="19582-130">PreCloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="19582-130">PreCloseAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/alink/precloseassembly-method.md)  
  
 [<span data-ttu-id="19582-131">SetAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="19582-131">SetAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/alink/setassemblyfile-method.md)  
  
 [<span data-ttu-id="19582-132">SetAssemblyProps 方法</span><span class="sxs-lookup"><span data-stu-id="19582-132">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/alink/setassemblyprops-method.md)  
  
 [<span data-ttu-id="19582-133">SetNonAssemblyFlags 方法</span><span class="sxs-lookup"><span data-stu-id="19582-133">SetNonAssemblyFlags Method</span></span>](../../../../docs/framework/unmanaged-api/alink/setnonassemblyflags-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="19582-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19582-134">See Also</span></span>  
 [<span data-ttu-id="19582-135">ALink API</span><span class="sxs-lookup"><span data-stu-id="19582-135">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)  
 [<span data-ttu-id="19582-136">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="19582-136">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="19582-137">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="19582-137">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
