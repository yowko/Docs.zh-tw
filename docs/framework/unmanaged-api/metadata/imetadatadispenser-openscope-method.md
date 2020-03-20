---
title: IMetaDataDispenser::OpenScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
ms.openlocfilehash: 5185fb6663910c85ce5dae1225b9b10c5dd8bb28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175937"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="76bf5-102">IMetaDataDispenser::OpenScope 方法</span><span class="sxs-lookup"><span data-stu-id="76bf5-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="76bf5-103">打開現有的磁片檔並將其元資料對應到記憶體中。</span><span class="sxs-lookup"><span data-stu-id="76bf5-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76bf5-104">語法</span><span class="sxs-lookup"><span data-stu-id="76bf5-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76bf5-105">參數</span><span class="sxs-lookup"><span data-stu-id="76bf5-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="76bf5-106">[在]要打開的檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="76bf5-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="76bf5-107">該檔必須包含通用語言運行時 （CLR） 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="76bf5-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="76bf5-108">[在][CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)枚舉的值，用於指定打開的模式（讀取、寫入等）。</span><span class="sxs-lookup"><span data-stu-id="76bf5-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="76bf5-109">[在]要返回的所需中繼資料介面的 IID;調用方將使用介面導入（讀取）或發出（寫入）中繼資料。</span><span class="sxs-lookup"><span data-stu-id="76bf5-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="76bf5-110">的值`riid`必須指定其中一個"導入"或"發射"介面。</span><span class="sxs-lookup"><span data-stu-id="76bf5-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="76bf5-111">有效值IID_IMetaDataEmit、IID_IMetaDataImport、IID_IMetaDataAssemblyEmit、IID_IMetaDataAssemblyImport、IID_IMetaDataEmit2或IID_IMetaDataImport2。</span><span class="sxs-lookup"><span data-stu-id="76bf5-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="76bf5-112">[出]指向返回介面的指標。</span><span class="sxs-lookup"><span data-stu-id="76bf5-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76bf5-113">備註</span><span class="sxs-lookup"><span data-stu-id="76bf5-113">Remarks</span></span>  
 <span data-ttu-id="76bf5-114">可以使用"導入"介面之一的方法查詢中繼資料的記憶體副本，也可以添加到使用"emit"介面之一的方法。</span><span class="sxs-lookup"><span data-stu-id="76bf5-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="76bf5-115">如果目的檔案不包含 CLR 中繼資料，則`OpenScope`該方法將失敗。</span><span class="sxs-lookup"><span data-stu-id="76bf5-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="76bf5-116">在 .NET 框架版本 1.0 和版本 1.1 中，`dwOpenFlags`如果使用設置為 Read 打開作用域，則它有資格共用。</span><span class="sxs-lookup"><span data-stu-id="76bf5-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="76bf5-117">也就是說，如果後續調用以`OpenScope`以前打開的檔的名稱傳遞，則重用現有作用域，並且不會創建新的資料結構集。</span><span class="sxs-lookup"><span data-stu-id="76bf5-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="76bf5-118">但是，由於這種共用，可能會出現問題。</span><span class="sxs-lookup"><span data-stu-id="76bf5-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="76bf5-119">在 .NET 框架版本 2.0 中，`dwOpenFlags`不再共用使用設置為 Read 打開的作用域。</span><span class="sxs-lookup"><span data-stu-id="76bf5-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="76bf5-120">使用 ReadOnly 值允許共用作用域。</span><span class="sxs-lookup"><span data-stu-id="76bf5-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="76bf5-121">共用作用域時，使用"讀/寫"中繼資料介面的查詢將失敗。</span><span class="sxs-lookup"><span data-stu-id="76bf5-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76bf5-122">需求</span><span class="sxs-lookup"><span data-stu-id="76bf5-122">Requirements</span></span>  
 <span data-ttu-id="76bf5-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="76bf5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76bf5-124">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="76bf5-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="76bf5-125">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="76bf5-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="76bf5-126">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76bf5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76bf5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76bf5-127">See also</span></span>

- [<span data-ttu-id="76bf5-128">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="76bf5-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="76bf5-129">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="76bf5-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="76bf5-130">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="76bf5-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="76bf5-131">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="76bf5-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="76bf5-132">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="76bf5-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="76bf5-133">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="76bf5-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="76bf5-134">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="76bf5-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="76bf5-135">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="76bf5-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
