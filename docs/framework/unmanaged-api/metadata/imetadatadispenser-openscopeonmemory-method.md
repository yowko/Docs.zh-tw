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
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="1610c-102">IMetaDataDispenser::OpenScopeOnMemory 方法</span><span class="sxs-lookup"><span data-stu-id="1610c-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="1610c-103">開啟包含現有中繼資料的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="1610c-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="1610c-104">也就是說，這個方法會開啟指定的記憶體區域，其中現有的資料會被視為中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1610c-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1610c-105">語法</span><span class="sxs-lookup"><span data-stu-id="1610c-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1610c-106">參數</span><span class="sxs-lookup"><span data-stu-id="1610c-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="1610c-107">在指標，指定記憶體區域的起始位址。</span><span class="sxs-lookup"><span data-stu-id="1610c-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="1610c-108">在記憶體區域的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="1610c-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="1610c-109">在[CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)列舉的值，用來指定要開啟的模式（讀取、寫入等等）。</span><span class="sxs-lookup"><span data-stu-id="1610c-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="1610c-110">在要傳回之所需中繼資料介面的 IID;呼叫端會使用介面來匯入（讀取）或發出（寫入）中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1610c-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="1610c-111">`riid` 的值必須指定其中一個「匯入」或「發出」介面。</span><span class="sxs-lookup"><span data-stu-id="1610c-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="1610c-112">有效的值為 IID_IMetaDataEmit、IID_IMetaDataImport、IID_IMetaDataAssemblyEmit、IID_IMetaDataAssemblyImport、IID_IMetaDataEmit2 或 IID_IMetaDataImport2。</span><span class="sxs-lookup"><span data-stu-id="1610c-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="1610c-113">脫銷傳回之介面的指標。</span><span class="sxs-lookup"><span data-stu-id="1610c-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1610c-114">備註</span><span class="sxs-lookup"><span data-stu-id="1610c-114">Remarks</span></span>  
 <span data-ttu-id="1610c-115">您可以使用其中一個「匯入」介面的方法來查詢中繼資料的記憶體中複本，或使用其中一個「發出」介面中的方法將其新增至。</span><span class="sxs-lookup"><span data-stu-id="1610c-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="1610c-116">`OpenScopeOnMemory` 方法類似于[IMetaDataDispenser：： OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法，不同之處在于有興趣的中繼資料已存在於記憶體中，而不是磁片上的檔案中。</span><span class="sxs-lookup"><span data-stu-id="1610c-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="1610c-117">如果記憶體的目的地區域不包含 common language runtime （CLR）中繼資料，`OpenScopeOnMemory` 方法將會失敗。</span><span class="sxs-lookup"><span data-stu-id="1610c-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1610c-118">需求</span><span class="sxs-lookup"><span data-stu-id="1610c-118">Requirements</span></span>  
 <span data-ttu-id="1610c-119">**平臺：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1610c-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1610c-120">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="1610c-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1610c-121">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="1610c-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1610c-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1610c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1610c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1610c-123">See also</span></span>

- [<span data-ttu-id="1610c-124">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="1610c-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="1610c-125">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="1610c-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="1610c-126">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="1610c-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="1610c-127">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="1610c-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="1610c-128">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="1610c-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1610c-129">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="1610c-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="1610c-130">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="1610c-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1610c-131">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="1610c-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
