---
title: "IMetaDataAssemblyEmit 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit
helpviewer_keywords: IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a7e4bd68bfd985b8902ae3b2340773ca77eee10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="50b64-102">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="50b64-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="50b64-103">提供方法，以便支援 Common Language Runtime 解析及消耗資源時所用的自我描述模型。</span><span class="sxs-lookup"><span data-stu-id="50b64-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50b64-104">方法</span><span class="sxs-lookup"><span data-stu-id="50b64-104">Methods</span></span>  
  
|<span data-ttu-id="50b64-105">方法</span><span class="sxs-lookup"><span data-stu-id="50b64-105">Method</span></span>|<span data-ttu-id="50b64-106">描述</span><span class="sxs-lookup"><span data-stu-id="50b64-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50b64-107">DefineAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="50b64-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="50b64-108">為指定的組件，建立包含其中繼資料的組件資料結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="50b64-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="50b64-109">DefineAssemblyRef 方法</span><span class="sxs-lookup"><span data-stu-id="50b64-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="50b64-110">為這個組件所參考的組件，建立包含其中繼資料的 `AssemblyRef` 結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="50b64-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="50b64-111">DefineExportedType 方法</span><span class="sxs-lookup"><span data-stu-id="50b64-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="50b64-112">為指定的已匯出類型，建立包含其中繼資料的 `ExportedType` 結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="50b64-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="50b64-113">DefineFile 方法</span><span class="sxs-lookup"><span data-stu-id="50b64-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="50b64-114">為這個組件所參考的組件，建立包含其中繼資料的 `File` 中繼資料結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="50b64-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="50b64-115">DefineManifestResource 方法</span><span class="sxs-lookup"><span data-stu-id="50b64-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="50b64-116">為指定的資訊清單資源，建立包含其中繼資料的 `ManifestResource` 結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="50b64-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="50b64-117">SetAssemblyProps 方法</span><span class="sxs-lookup"><span data-stu-id="50b64-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="50b64-118">修改指定的 `Assembly` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="50b64-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="50b64-119">SetAssemblyRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="50b64-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="50b64-120">修改指定的 `AssemblyRef` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="50b64-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="50b64-121">SetExportedTypeProps 方法</span><span class="sxs-lookup"><span data-stu-id="50b64-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="50b64-122">修改指定的 `ExportedType` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="50b64-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="50b64-123">SetFileProps 方法</span><span class="sxs-lookup"><span data-stu-id="50b64-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="50b64-124">修改指定的 `File` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="50b64-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="50b64-125">SetManifestResourceProps 方法</span><span class="sxs-lookup"><span data-stu-id="50b64-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="50b64-126">修改指定的 `ManifestResource` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="50b64-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50b64-127">備註</span><span class="sxs-lookup"><span data-stu-id="50b64-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50b64-128">需求</span><span class="sxs-lookup"><span data-stu-id="50b64-128">Requirements</span></span>  
 <span data-ttu-id="50b64-129">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="50b64-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50b64-130">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="50b64-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50b64-131">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="50b64-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50b64-132">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50b64-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50b64-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="50b64-133">See Also</span></span>  
 [<span data-ttu-id="50b64-134">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="50b64-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="50b64-135">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="50b64-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
