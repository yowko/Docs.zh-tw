---
title: "IMetaDataAssemblyImport 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport
helpviewer_keywords: IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ef5b913dc9b1391c63cb123e1f922ca61da6a5bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="4b433-102">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="4b433-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="4b433-103">提供存取及檢查組件資訊清單內容的方法。</span><span class="sxs-lookup"><span data-stu-id="4b433-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b433-104">方法</span><span class="sxs-lookup"><span data-stu-id="4b433-104">Methods</span></span>  
  
|<span data-ttu-id="4b433-105">方法</span><span class="sxs-lookup"><span data-stu-id="4b433-105">Method</span></span>|<span data-ttu-id="4b433-106">說明</span><span class="sxs-lookup"><span data-stu-id="4b433-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b433-107">CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="4b433-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="4b433-108">釋放的控制代碼指定的列舉值。</span><span class="sxs-lookup"><span data-stu-id="4b433-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="4b433-109">EnumAssemblyRefs 方法</span><span class="sxs-lookup"><span data-stu-id="4b433-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="4b433-110">取得列舉值，其中包含的介面指標`mdAssemblyRef`目前中繼資料範圍內組件所參考的組件的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4b433-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="4b433-111">EnumExportedTypes 方法</span><span class="sxs-lookup"><span data-stu-id="4b433-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="4b433-112">取得列舉值，其中包含的介面指標`mdExportedType`目前中繼資料範圍內的組件所參考的 COM 類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4b433-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="4b433-113">EnumFiles 方法</span><span class="sxs-lookup"><span data-stu-id="4b433-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="4b433-114">取得列舉值，其中包含的介面指標`mdFile`檔案目前的中繼資料範圍內組件參考語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4b433-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="4b433-115">EnumManifestResources 方法</span><span class="sxs-lookup"><span data-stu-id="4b433-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="4b433-116">取得列舉值，其中包含的介面指標`mdManifestResource`語彙基元所參考的資源目前的中繼資料範圍中的組件。</span><span class="sxs-lookup"><span data-stu-id="4b433-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="4b433-117">FindAssembliesByName 方法</span><span class="sxs-lookup"><span data-stu-id="4b433-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="4b433-118">取得陣列的`mdAssemblyRef`語彙基元的指定名稱的組件。</span><span class="sxs-lookup"><span data-stu-id="4b433-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="4b433-119">FindExportedTypeByName 方法</span><span class="sxs-lookup"><span data-stu-id="4b433-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="4b433-120">取得`mdExportedType`具有指定名稱的 COM 類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4b433-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="4b433-121">FindManifestResourceByName 方法</span><span class="sxs-lookup"><span data-stu-id="4b433-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="4b433-122">取得`mdManifestResource`語彙基元的指定名稱的資源。</span><span class="sxs-lookup"><span data-stu-id="4b433-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="4b433-123">GetAssemblyFromScope 方法</span><span class="sxs-lookup"><span data-stu-id="4b433-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="4b433-124">取得目前中繼資料範圍內組件的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4b433-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="4b433-125">GetAssemblyProps 方法</span><span class="sxs-lookup"><span data-stu-id="4b433-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="4b433-126">取得指定的組件的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="4b433-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="4b433-127">GetAssemblyRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="4b433-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="4b433-128">取得指定的屬性設定`mdAssemblyRef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4b433-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="4b433-129">GetExportedTypeProps 方法</span><span class="sxs-lookup"><span data-stu-id="4b433-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="4b433-130">取得指定的 COM 類型的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="4b433-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="4b433-131">GetFileProps 方法</span><span class="sxs-lookup"><span data-stu-id="4b433-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="4b433-132">取得指定之檔案的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="4b433-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="4b433-133">GetManifestResourceProps 方法</span><span class="sxs-lookup"><span data-stu-id="4b433-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="4b433-134">取得指定的資訊清單資源的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="4b433-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4b433-135">需求</span><span class="sxs-lookup"><span data-stu-id="4b433-135">Requirements</span></span>  
 <span data-ttu-id="4b433-136">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4b433-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b433-137">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4b433-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4b433-138">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4b433-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4b433-139">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b433-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b433-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b433-140">See Also</span></span>  
 [<span data-ttu-id="4b433-141">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="4b433-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="4b433-142">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="4b433-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
