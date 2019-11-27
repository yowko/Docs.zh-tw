---
title: IMetaDataAssemblyImport 介面
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
ms.openlocfilehash: 289e26868ff2eb9e1d97cf084e9a888815062ea4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436301"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="032dc-102">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="032dc-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="032dc-103">提供存取及檢查組件資訊清單內容的方法。</span><span class="sxs-lookup"><span data-stu-id="032dc-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="032dc-104">方法</span><span class="sxs-lookup"><span data-stu-id="032dc-104">Methods</span></span>  
  
|<span data-ttu-id="032dc-105">方法</span><span class="sxs-lookup"><span data-stu-id="032dc-105">Method</span></span>|<span data-ttu-id="032dc-106">描述</span><span class="sxs-lookup"><span data-stu-id="032dc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="032dc-107">CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="032dc-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="032dc-108">釋放指定列舉值的控制碼。</span><span class="sxs-lookup"><span data-stu-id="032dc-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="032dc-109">EnumAssemblyRefs 方法</span><span class="sxs-lookup"><span data-stu-id="032dc-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="032dc-110">取得列舉值的介面指標，其中包含目前中繼資料範圍內元件所參考之元件的 `mdAssemblyRef` token。</span><span class="sxs-lookup"><span data-stu-id="032dc-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="032dc-111">EnumExportedTypes 方法</span><span class="sxs-lookup"><span data-stu-id="032dc-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="032dc-112">取得列舉值的介面指標，其中包含目前中繼資料範圍內元件所參考之 COM 類型的 `mdExportedType` token。</span><span class="sxs-lookup"><span data-stu-id="032dc-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="032dc-113">EnumFiles 方法</span><span class="sxs-lookup"><span data-stu-id="032dc-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="032dc-114">取得列舉值的介面指標，其中包含目前中繼資料範圍內元件所參考之檔案的 `mdFile` token。</span><span class="sxs-lookup"><span data-stu-id="032dc-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="032dc-115">EnumManifestResources 方法</span><span class="sxs-lookup"><span data-stu-id="032dc-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="032dc-116">取得列舉值的介面指標，其中包含目前中繼資料範圍內元件所參考之資源的 `mdManifestResource` token。</span><span class="sxs-lookup"><span data-stu-id="032dc-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="032dc-117">FindAssembliesByName 方法</span><span class="sxs-lookup"><span data-stu-id="032dc-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="032dc-118">取得具有指定名稱之元件的 `mdAssemblyRef` token 陣列。</span><span class="sxs-lookup"><span data-stu-id="032dc-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="032dc-119">FindExportedTypeByName 方法</span><span class="sxs-lookup"><span data-stu-id="032dc-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="032dc-120">取得具有指定名稱之 COM 類型的 `mdExportedType` token。</span><span class="sxs-lookup"><span data-stu-id="032dc-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="032dc-121">FindManifestResourceByName 方法</span><span class="sxs-lookup"><span data-stu-id="032dc-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="032dc-122">取得具有指定名稱之資源的 `mdManifestResource` token。</span><span class="sxs-lookup"><span data-stu-id="032dc-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="032dc-123">GetAssemblyFromScope 方法</span><span class="sxs-lookup"><span data-stu-id="032dc-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="032dc-124">取得目前中繼資料範圍中元件的 token。</span><span class="sxs-lookup"><span data-stu-id="032dc-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="032dc-125">GetAssemblyProps 方法</span><span class="sxs-lookup"><span data-stu-id="032dc-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="032dc-126">取得指定元件的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="032dc-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="032dc-127">GetAssemblyRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="032dc-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="032dc-128">取得指定 `mdAssemblyRef` token 的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="032dc-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="032dc-129">GetExportedTypeProps 方法</span><span class="sxs-lookup"><span data-stu-id="032dc-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="032dc-130">取得指定 COM 類型的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="032dc-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="032dc-131">GetFileProps 方法</span><span class="sxs-lookup"><span data-stu-id="032dc-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="032dc-132">取得指定檔案的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="032dc-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="032dc-133">GetManifestResourceProps 方法</span><span class="sxs-lookup"><span data-stu-id="032dc-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="032dc-134">取得指定之資訊清單資源的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="032dc-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="032dc-135">需求</span><span class="sxs-lookup"><span data-stu-id="032dc-135">Requirements</span></span>  
 <span data-ttu-id="032dc-136">**平臺：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="032dc-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="032dc-137">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="032dc-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="032dc-138">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="032dc-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="032dc-139">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="032dc-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="032dc-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="032dc-140">See also</span></span>

- [<span data-ttu-id="032dc-141">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="032dc-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="032dc-142">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="032dc-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
