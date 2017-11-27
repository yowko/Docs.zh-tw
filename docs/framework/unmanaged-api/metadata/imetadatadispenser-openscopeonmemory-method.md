---
title: "IMetaDataDispenser::OpenScopeOnMemory 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenser.OpenScopeOnMemory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0c6cfc21a5aecfc043a7720959610210df1d15ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="85385-102">IMetaDataDispenser::OpenScopeOnMemory 方法</span><span class="sxs-lookup"><span data-stu-id="85385-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="85385-103">開啟包含現有的中繼資料的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="85385-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="85385-104">也就是說，這個方法會開啟指定的現有資料會被視為中繼資料的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="85385-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85385-105">語法</span><span class="sxs-lookup"><span data-stu-id="85385-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85385-106">參數</span><span class="sxs-lookup"><span data-stu-id="85385-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="85385-107">[in]指定的記憶體區域的起始位址指標。</span><span class="sxs-lookup"><span data-stu-id="85385-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="85385-108">[in]記憶體區域，以位元組為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="85385-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="85385-109">[in]值為[CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)列舉來指定 （讀取、 寫入和等等） 的模式開啟。</span><span class="sxs-lookup"><span data-stu-id="85385-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="85385-110">[in]要傳回; 所需的中繼資料介面的 IID呼叫端會使用介面來匯入 （讀取），或發出 （寫入） 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="85385-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="85385-111">值`riid`必須指定其中一個 「 匯入 」 或 「 發出"介面。</span><span class="sxs-lookup"><span data-stu-id="85385-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="85385-112">有效值為 IID_IMetaDataEmit、 IID_IMetaDataImport、 IID_IMetaDataAssemblyEmit、 IID_IMetaDataAssemblyImport、 IID_IMetaDataEmit2 或 IID_IMetaDataImport2。</span><span class="sxs-lookup"><span data-stu-id="85385-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="85385-113">[out]要傳回的介面的指標。</span><span class="sxs-lookup"><span data-stu-id="85385-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85385-114">備註</span><span class="sxs-lookup"><span data-stu-id="85385-114">Remarks</span></span>  
 <span data-ttu-id="85385-115">您可以查詢中繼資料的記憶體中複本，使用其中一個，「 匯入 」 的介面方法，或加入至一個 「 發出"介面的使用方法。</span><span class="sxs-lookup"><span data-stu-id="85385-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="85385-116">`OpenScopeOnMemory`方法很類似[imetadatadispenser:: Openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)方法，不同之處在於感興趣的中繼資料已存在的記憶體，而不是磁碟上的檔案。</span><span class="sxs-lookup"><span data-stu-id="85385-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="85385-117">如果記憶體目標區域不包含 common language runtime (CLR) 中繼資料，`OpenScopeOnMemory`方法將會失敗。</span><span class="sxs-lookup"><span data-stu-id="85385-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85385-118">需求</span><span class="sxs-lookup"><span data-stu-id="85385-118">Requirements</span></span>  
 <span data-ttu-id="85385-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="85385-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85385-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="85385-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85385-121">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="85385-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85385-122">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85385-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85385-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85385-123">See Also</span></span>  
 [<span data-ttu-id="85385-124">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="85385-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="85385-125">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="85385-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="85385-126">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="85385-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="85385-127">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="85385-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="85385-128">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="85385-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="85385-129">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="85385-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="85385-130">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="85385-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="85385-131">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="85385-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
