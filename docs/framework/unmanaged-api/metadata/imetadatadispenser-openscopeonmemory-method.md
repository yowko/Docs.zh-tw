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
ms.openlocfilehash: 492c37540ad68b5b134520218eedc59013c68519
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175924"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="4333e-102">IMetaDataDispenser::OpenScopeOnMemory 方法</span><span class="sxs-lookup"><span data-stu-id="4333e-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="4333e-103">打開包含現有中繼資料的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="4333e-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="4333e-104">也就是說，此方法將打開指定記憶體區域，其中現有資料被視為中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4333e-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4333e-105">語法</span><span class="sxs-lookup"><span data-stu-id="4333e-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4333e-106">參數</span><span class="sxs-lookup"><span data-stu-id="4333e-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="4333e-107">[在]指定記憶體區域的起始位址的指標。</span><span class="sxs-lookup"><span data-stu-id="4333e-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="4333e-108">[在]記憶體區域的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="4333e-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="4333e-109">[在][CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)枚舉的值，用於指定打開的模式（讀取、寫入等）。</span><span class="sxs-lookup"><span data-stu-id="4333e-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="4333e-110">[在]要返回的所需中繼資料介面的 IID;調用方將使用介面導入（讀取）或發出（寫入）中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4333e-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="4333e-111">的值`riid`必須指定其中一個"導入"或"發射"介面。</span><span class="sxs-lookup"><span data-stu-id="4333e-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="4333e-112">有效值IID_IMetaDataEmit、IID_IMetaDataImport、IID_IMetaDataAssemblyEmit、IID_IMetaDataAssemblyImport、IID_IMetaDataEmit2或IID_IMetaDataImport2。</span><span class="sxs-lookup"><span data-stu-id="4333e-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="4333e-113">[出]指向返回介面的指標。</span><span class="sxs-lookup"><span data-stu-id="4333e-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4333e-114">備註</span><span class="sxs-lookup"><span data-stu-id="4333e-114">Remarks</span></span>  
 <span data-ttu-id="4333e-115">可以使用"導入"介面之一的方法查詢中繼資料的記憶體副本，也可以添加到使用"emit"介面之一的方法。</span><span class="sxs-lookup"><span data-stu-id="4333e-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="4333e-116">該方法`OpenScopeOnMemory`類似于[IMetaDataDispenser：：openScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法，只不過感興趣的中繼資料已存在於記憶體中，而不是磁片上的檔中。</span><span class="sxs-lookup"><span data-stu-id="4333e-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="4333e-117">如果記憶體的目的地區域不包含通用語言運行時 （CLR） 中繼資料，則`OpenScopeOnMemory`該方法將失敗。</span><span class="sxs-lookup"><span data-stu-id="4333e-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4333e-118">需求</span><span class="sxs-lookup"><span data-stu-id="4333e-118">Requirements</span></span>  
 <span data-ttu-id="4333e-119">**平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4333e-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4333e-120">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="4333e-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4333e-121">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4333e-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4333e-122">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4333e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4333e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4333e-123">See also</span></span>

- [<span data-ttu-id="4333e-124">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="4333e-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="4333e-125">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="4333e-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="4333e-126">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="4333e-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="4333e-127">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="4333e-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="4333e-128">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="4333e-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4333e-129">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="4333e-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="4333e-130">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="4333e-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4333e-131">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="4333e-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
