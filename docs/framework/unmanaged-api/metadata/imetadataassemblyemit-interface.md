---
title: IMetaDataAssemblyEmit 介面
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
ms.openlocfilehash: 807e1ee831a43a4ef1e7b0a269ee38131f24081e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008114"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="3e134-102">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="3e134-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="3e134-103">提供方法，以便支援 Common Language Runtime 解析及消耗資源時所用的自我描述模型。</span><span class="sxs-lookup"><span data-stu-id="3e134-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e134-104">方法</span><span class="sxs-lookup"><span data-stu-id="3e134-104">Methods</span></span>  
  
|<span data-ttu-id="3e134-105">方法</span><span class="sxs-lookup"><span data-stu-id="3e134-105">Method</span></span>|<span data-ttu-id="3e134-106">描述</span><span class="sxs-lookup"><span data-stu-id="3e134-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e134-107">DefineAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="3e134-107">DefineAssembly Method</span></span>](imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="3e134-108">為指定的組件，建立包含其中繼資料的組件資料結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3e134-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="3e134-109">DefineAssemblyRef 方法</span><span class="sxs-lookup"><span data-stu-id="3e134-109">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="3e134-110">為這個組件所參考的組件，建立包含其中繼資料的 `AssemblyRef` 結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3e134-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="3e134-111">DefineExportedType 方法</span><span class="sxs-lookup"><span data-stu-id="3e134-111">DefineExportedType Method</span></span>](imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="3e134-112">為指定的已匯出類型，建立包含其中繼資料的 `ExportedType` 結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3e134-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="3e134-113">DefineFile 方法</span><span class="sxs-lookup"><span data-stu-id="3e134-113">DefineFile Method</span></span>](imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="3e134-114">為這個組件所參考的組件，建立包含其中繼資料的 `File` 中繼資料結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3e134-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="3e134-115">DefineManifestResource 方法</span><span class="sxs-lookup"><span data-stu-id="3e134-115">DefineManifestResource Method</span></span>](imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="3e134-116">為指定的資訊清單資源，建立包含其中繼資料的 `ManifestResource` 結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3e134-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="3e134-117">SetAssemblyProps 方法</span><span class="sxs-lookup"><span data-stu-id="3e134-117">SetAssemblyProps Method</span></span>](imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="3e134-118">修改指定的 `Assembly` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="3e134-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="3e134-119">SetAssemblyRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="3e134-119">SetAssemblyRefProps Method</span></span>](imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="3e134-120">修改指定的 `AssemblyRef` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="3e134-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="3e134-121">SetExportedTypeProps 方法</span><span class="sxs-lookup"><span data-stu-id="3e134-121">SetExportedTypeProps Method</span></span>](imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="3e134-122">修改指定的 `ExportedType` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="3e134-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="3e134-123">SetFileProps 方法</span><span class="sxs-lookup"><span data-stu-id="3e134-123">SetFileProps Method</span></span>](imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="3e134-124">修改指定的 `File` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="3e134-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="3e134-125">SetManifestResourceProps 方法</span><span class="sxs-lookup"><span data-stu-id="3e134-125">SetManifestResourceProps Method</span></span>](imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="3e134-126">修改指定的 `ManifestResource` 中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="3e134-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e134-127">備註</span><span class="sxs-lookup"><span data-stu-id="3e134-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e134-128">需求</span><span class="sxs-lookup"><span data-stu-id="3e134-128">Requirements</span></span>  
 <span data-ttu-id="3e134-129">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e134-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e134-130">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="3e134-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3e134-131">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="3e134-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3e134-132">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e134-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e134-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e134-133">See also</span></span>

- [<span data-ttu-id="3e134-134">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="3e134-134">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="3e134-135">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="3e134-135">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
