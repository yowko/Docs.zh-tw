---
title: "IMetaDataDispenser::OpenScope 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenser.OpenScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09c057f42bb849b89d78d2d32af6637640ad22ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="9b844-102">IMetaDataDispenser::OpenScope 方法</span><span class="sxs-lookup"><span data-stu-id="9b844-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="9b844-103">開啟現有磁碟上的檔案，並將它的中繼資料對應到記憶體中。</span><span class="sxs-lookup"><span data-stu-id="9b844-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b844-104">語法</span><span class="sxs-lookup"><span data-stu-id="9b844-104">Syntax</span></span>  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b844-105">參數</span><span class="sxs-lookup"><span data-stu-id="9b844-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="9b844-106">[in]要開啟的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="9b844-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="9b844-107">這個檔案必須包含 common language runtime (CLR) 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9b844-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="9b844-108">[in]值為[CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)列舉來指定 （讀取、 寫入和等等） 的模式開啟。</span><span class="sxs-lookup"><span data-stu-id="9b844-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="9b844-109">[in]要傳回; 所需的中繼資料介面的 IID呼叫端會使用介面來匯入 （讀取），或發出 （寫入） 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9b844-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="9b844-110">值`riid`必須指定其中一個 「 匯入 」 或 「 發出"介面。</span><span class="sxs-lookup"><span data-stu-id="9b844-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="9b844-111">有效值為 IID_IMetaDataEmit、 IID_IMetaDataImport、 IID_IMetaDataAssemblyEmit、 IID_IMetaDataAssemblyImport、 IID_IMetaDataEmit2 或 IID_IMetaDataImport2。</span><span class="sxs-lookup"><span data-stu-id="9b844-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="9b844-112">[out]要傳回的介面的指標。</span><span class="sxs-lookup"><span data-stu-id="9b844-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b844-113">備註</span><span class="sxs-lookup"><span data-stu-id="9b844-113">Remarks</span></span>  
 <span data-ttu-id="9b844-114">您可以查詢中繼資料的記憶體中複本，使用其中一個，「 匯入 」 的介面方法，或加入至一個 「 發出"介面的使用方法。</span><span class="sxs-lookup"><span data-stu-id="9b844-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="9b844-115">如果目標檔案未包含 CLR 中繼資料，`OpenScope`方法將會失敗。</span><span class="sxs-lookup"><span data-stu-id="9b844-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="9b844-116">在.NET Framework 1.0 和 1.1 中，如果範圍以開啟`dwOpenFlags`設 ofRead，很適合用於共用。</span><span class="sxs-lookup"><span data-stu-id="9b844-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="9b844-117">也就是說，如果後續呼叫`OpenScope`傳入先前開啟的檔案的名稱，會重複使用現有的範圍，並不會建立一組新的資料結構。</span><span class="sxs-lookup"><span data-stu-id="9b844-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="9b844-118">不過，由於這個共用可能會發生問題。</span><span class="sxs-lookup"><span data-stu-id="9b844-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="9b844-119">在.NET Framework 2.0 版中，範圍則是以開啟`dwOpenFlags`ofRead 設不會再共用。</span><span class="sxs-lookup"><span data-stu-id="9b844-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="9b844-120">共用範圍，以便使用 ofReadOnly 值。</span><span class="sxs-lookup"><span data-stu-id="9b844-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="9b844-121">共用範圍時，使用 「 讀取/寫入 」 中繼資料介面的查詢將會失敗。</span><span class="sxs-lookup"><span data-stu-id="9b844-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b844-122">需求</span><span class="sxs-lookup"><span data-stu-id="9b844-122">Requirements</span></span>  
 <span data-ttu-id="9b844-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b844-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b844-124">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9b844-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b844-125">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9b844-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9b844-126">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b844-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b844-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b844-127">See Also</span></span>  
 [<span data-ttu-id="9b844-128">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="9b844-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="9b844-129">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="9b844-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="9b844-130">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="9b844-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="9b844-131">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="9b844-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="9b844-132">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="9b844-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="9b844-133">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="9b844-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="9b844-134">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="9b844-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9b844-135">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="9b844-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
