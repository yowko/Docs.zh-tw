---
title: IMetaDataDispenser::OpenScopeOnMemory 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
ms.openlocfilehash: 04e0fabfc0d70c9d922e0715f32bd07237ce8741
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442318"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="7bfc7-102">IMetaDataDispenser::OpenScopeOnMemory 方法</span><span class="sxs-lookup"><span data-stu-id="7bfc7-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="7bfc7-103">Opens an area of memory that contains existing metadata.</span><span class="sxs-lookup"><span data-stu-id="7bfc7-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="7bfc7-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span><span class="sxs-lookup"><span data-stu-id="7bfc7-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bfc7-105">語法</span><span class="sxs-lookup"><span data-stu-id="7bfc7-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bfc7-106">參數</span><span class="sxs-lookup"><span data-stu-id="7bfc7-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="7bfc7-107">[in] A pointer that specifies the starting address of the memory area.</span><span class="sxs-lookup"><span data-stu-id="7bfc7-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="7bfc7-108">[in] The size of the memory area, in bytes.</span><span class="sxs-lookup"><span data-stu-id="7bfc7-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="7bfc7-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span><span class="sxs-lookup"><span data-stu-id="7bfc7-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="7bfc7-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span><span class="sxs-lookup"><span data-stu-id="7bfc7-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="7bfc7-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span><span class="sxs-lookup"><span data-stu-id="7bfc7-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="7bfc7-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="7bfc7-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="7bfc7-113">[out] The pointer to the returned interface.</span><span class="sxs-lookup"><span data-stu-id="7bfc7-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bfc7-114">備註</span><span class="sxs-lookup"><span data-stu-id="7bfc7-114">Remarks</span></span>  
 <span data-ttu-id="7bfc7-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span><span class="sxs-lookup"><span data-stu-id="7bfc7-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="7bfc7-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span><span class="sxs-lookup"><span data-stu-id="7bfc7-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="7bfc7-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span><span class="sxs-lookup"><span data-stu-id="7bfc7-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bfc7-118">需求</span><span class="sxs-lookup"><span data-stu-id="7bfc7-118">Requirements</span></span>  
 <span data-ttu-id="7bfc7-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bfc7-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bfc7-120">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7bfc7-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7bfc7-121">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7bfc7-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7bfc7-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bfc7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bfc7-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="7bfc7-123">See also</span></span>

- [<span data-ttu-id="7bfc7-124">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="7bfc7-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="7bfc7-125">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="7bfc7-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="7bfc7-126">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="7bfc7-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="7bfc7-127">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="7bfc7-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="7bfc7-128">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="7bfc7-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7bfc7-129">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="7bfc7-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="7bfc7-130">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="7bfc7-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7bfc7-131">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="7bfc7-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
