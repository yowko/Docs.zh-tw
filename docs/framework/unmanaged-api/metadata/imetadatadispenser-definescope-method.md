---
title: "IMetaDataDispenser::DefineScope 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenser.DefineScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 964e6df1b6aba7ca85b627cf19c38f5df600b6ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="15bef-102">IMetaDataDispenser::DefineScope 方法</span><span class="sxs-lookup"><span data-stu-id="15bef-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="15bef-103">您可以在其中建立新的中繼資料的記憶體中建立新的區域。</span><span class="sxs-lookup"><span data-stu-id="15bef-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15bef-104">語法</span><span class="sxs-lookup"><span data-stu-id="15bef-104">Syntax</span></span>  
  
```  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15bef-105">參數</span><span class="sxs-lookup"><span data-stu-id="15bef-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="15bef-106">[in]建立版本之中繼資料結構的 CLSID。</span><span class="sxs-lookup"><span data-stu-id="15bef-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="15bef-107">此值必須是 CLSID_CorMetaDataRuntime 適用於.NET Framework 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="15bef-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="15bef-108">[in]指定選項的旗標。</span><span class="sxs-lookup"><span data-stu-id="15bef-108">[in] Flags that specify options.</span></span> <span data-ttu-id="15bef-109">此值必須是針對.NET Framework 2.0 的零。</span><span class="sxs-lookup"><span data-stu-id="15bef-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="15bef-110">[in]要傳回; 所需的中繼資料介面的 IID呼叫端會使用介面來建立新的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="15bef-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="15bef-111">值`riid`必須指定其中一個 「 發出"介面。</span><span class="sxs-lookup"><span data-stu-id="15bef-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="15bef-112">有效值為 IID_IMetaDataEmit、 IID_IMetaDataAssemblyEmit 或 IID_IMetaDataEmit2。</span><span class="sxs-lookup"><span data-stu-id="15bef-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="15bef-113">[out]要傳回的介面的指標。</span><span class="sxs-lookup"><span data-stu-id="15bef-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15bef-114">備註</span><span class="sxs-lookup"><span data-stu-id="15bef-114">Remarks</span></span>  
 <span data-ttu-id="15bef-115">`DefineScope`建立一組的記憶體中中繼資料表，會產生唯一的 GUID （模組版本識別碼或 MVID） 的中繼資料，而且模組資料表中建立項目編譯單位所發出的。</span><span class="sxs-lookup"><span data-stu-id="15bef-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="15bef-116">您可以將屬性附加至中繼資料範圍為整個使用[imetadataemit:: Setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)或[imetadataemit:: Definecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)方法，視需要。</span><span class="sxs-lookup"><span data-stu-id="15bef-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15bef-117">需求</span><span class="sxs-lookup"><span data-stu-id="15bef-117">Requirements</span></span>  
 <span data-ttu-id="15bef-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15bef-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15bef-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="15bef-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15bef-120">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="15bef-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="15bef-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15bef-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15bef-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15bef-122">See Also</span></span>  
 [<span data-ttu-id="15bef-123">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="15bef-123">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="15bef-124">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="15bef-124">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="15bef-125">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="15bef-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="15bef-126">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="15bef-126">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="15bef-127">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="15bef-127">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
