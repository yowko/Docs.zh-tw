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
ms.openlocfilehash: 2a67f50fa1042e8d3957a9a0394507f260a328c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009011"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="4293a-102">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="4293a-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="4293a-103">提供存取及檢查組件資訊清單內容的方法。</span><span class="sxs-lookup"><span data-stu-id="4293a-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4293a-104">方法</span><span class="sxs-lookup"><span data-stu-id="4293a-104">Methods</span></span>  
  
|<span data-ttu-id="4293a-105">方法</span><span class="sxs-lookup"><span data-stu-id="4293a-105">Method</span></span>|<span data-ttu-id="4293a-106">描述</span><span class="sxs-lookup"><span data-stu-id="4293a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4293a-107">CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="4293a-107">CloseEnum Method</span></span>](imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="4293a-108">釋放指定列舉值的控制碼。</span><span class="sxs-lookup"><span data-stu-id="4293a-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="4293a-109">EnumAssemblyRefs 方法</span><span class="sxs-lookup"><span data-stu-id="4293a-109">EnumAssemblyRefs Method</span></span>](imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="4293a-110">取得列舉值的介面指標，其中包含 `mdAssemblyRef` 目前中繼資料範圍內元件所參考之元件的標記。</span><span class="sxs-lookup"><span data-stu-id="4293a-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="4293a-111">EnumExportedTypes 方法</span><span class="sxs-lookup"><span data-stu-id="4293a-111">EnumExportedTypes Method</span></span>](imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="4293a-112">取得列舉值的介面指標，其中包含 `mdExportedType` 目前中繼資料範圍內元件所參考之 COM 類型的標記。</span><span class="sxs-lookup"><span data-stu-id="4293a-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="4293a-113">EnumFiles 方法</span><span class="sxs-lookup"><span data-stu-id="4293a-113">EnumFiles Method</span></span>](imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="4293a-114">取得列舉值的介面指標，其中包含 `mdFile` 目前中繼資料範圍內元件所參考之檔案的標記。</span><span class="sxs-lookup"><span data-stu-id="4293a-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="4293a-115">EnumManifestResources 方法</span><span class="sxs-lookup"><span data-stu-id="4293a-115">EnumManifestResources Method</span></span>](imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="4293a-116">取得列舉值的介面指標，其中包含 `mdManifestResource` 目前中繼資料範圍內元件所參考之資源的權杖。</span><span class="sxs-lookup"><span data-stu-id="4293a-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="4293a-117">FindAssembliesByName 方法</span><span class="sxs-lookup"><span data-stu-id="4293a-117">FindAssembliesByName Method</span></span>](imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="4293a-118">取得 `mdAssemblyRef` 具有指定名稱之元件的標記陣列。</span><span class="sxs-lookup"><span data-stu-id="4293a-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="4293a-119">FindExportedTypeByName 方法</span><span class="sxs-lookup"><span data-stu-id="4293a-119">FindExportedTypeByName Method</span></span>](imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="4293a-120">取得 `mdExportedType` 具有指定名稱之 COM 類型的 token。</span><span class="sxs-lookup"><span data-stu-id="4293a-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="4293a-121">FindManifestResourceByName 方法</span><span class="sxs-lookup"><span data-stu-id="4293a-121">FindManifestResourceByName Method</span></span>](imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="4293a-122">取得 `mdManifestResource` 具有指定名稱之資源的 token。</span><span class="sxs-lookup"><span data-stu-id="4293a-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="4293a-123">GetAssemblyFromScope 方法</span><span class="sxs-lookup"><span data-stu-id="4293a-123">GetAssemblyFromScope Method</span></span>](imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="4293a-124">取得目前中繼資料範圍中元件的 token。</span><span class="sxs-lookup"><span data-stu-id="4293a-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="4293a-125">GetAssemblyProps 方法</span><span class="sxs-lookup"><span data-stu-id="4293a-125">GetAssemblyProps Method</span></span>](imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="4293a-126">取得指定元件的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="4293a-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="4293a-127">GetAssemblyRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="4293a-127">GetAssemblyRefProps Method</span></span>](imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="4293a-128">取得指定之標記的屬性設定 `mdAssemblyRef` 。</span><span class="sxs-lookup"><span data-stu-id="4293a-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="4293a-129">GetExportedTypeProps 方法</span><span class="sxs-lookup"><span data-stu-id="4293a-129">GetExportedTypeProps Method</span></span>](imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="4293a-130">取得指定 COM 類型的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="4293a-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="4293a-131">GetFileProps 方法</span><span class="sxs-lookup"><span data-stu-id="4293a-131">GetFileProps Method</span></span>](imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="4293a-132">取得指定檔案的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="4293a-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="4293a-133">GetManifestResourceProps 方法</span><span class="sxs-lookup"><span data-stu-id="4293a-133">GetManifestResourceProps Method</span></span>](imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="4293a-134">取得指定之資訊清單資源的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="4293a-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4293a-135">需求</span><span class="sxs-lookup"><span data-stu-id="4293a-135">Requirements</span></span>  
 <span data-ttu-id="4293a-136">**平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4293a-136">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4293a-137">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="4293a-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4293a-138">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="4293a-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4293a-139">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4293a-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4293a-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4293a-140">See also</span></span>

- [<span data-ttu-id="4293a-141">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="4293a-141">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="4293a-142">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="4293a-142">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
