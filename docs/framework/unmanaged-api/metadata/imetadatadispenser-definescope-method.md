---
title: IMetaDataDispenser::DefineScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76a439effad9cb3f6dcdd232590cf2196ee7ab99
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101402"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="68952-102">IMetaDataDispenser::DefineScope 方法</span><span class="sxs-lookup"><span data-stu-id="68952-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="68952-103">您可以在其中建立新的中繼資料的記憶體中建立新的區域。</span><span class="sxs-lookup"><span data-stu-id="68952-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68952-104">語法</span><span class="sxs-lookup"><span data-stu-id="68952-104">Syntax</span></span>  
  
```  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68952-105">參數</span><span class="sxs-lookup"><span data-stu-id="68952-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="68952-106">[in]若要建立的中繼資料結構版本 CLSID。</span><span class="sxs-lookup"><span data-stu-id="68952-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="68952-107">此值必須是 CLSID_CorMetaDataRuntime 適用於.NET Framework 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="68952-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="68952-108">[in]指定選項的旗標。</span><span class="sxs-lookup"><span data-stu-id="68952-108">[in] Flags that specify options.</span></span> <span data-ttu-id="68952-109">此值必須是針對.NET Framework 2.0 的零。</span><span class="sxs-lookup"><span data-stu-id="68952-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="68952-110">[in]要傳回; 所需的中繼資料介面的 IID呼叫端會使用介面來建立新的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="68952-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="68952-111">值`riid`必須指定其中一個 「 發出 」 的介面。</span><span class="sxs-lookup"><span data-stu-id="68952-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="68952-112">有效值為 IID_IMetaDataEmit、 IID_IMetaDataAssemblyEmit 或 IID_IMetaDataEmit2。</span><span class="sxs-lookup"><span data-stu-id="68952-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="68952-113">[out]要傳回的介面的指標。</span><span class="sxs-lookup"><span data-stu-id="68952-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68952-114">備註</span><span class="sxs-lookup"><span data-stu-id="68952-114">Remarks</span></span>  
 <span data-ttu-id="68952-115">`DefineScope` 會建立一組記憶體中的中繼資料資料表、 產生的中繼資料的唯一 GUID （模組版本識別碼或 MVID） 和 「 模組 」 資料表中建立的項目，發出編譯單元。</span><span class="sxs-lookup"><span data-stu-id="68952-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="68952-116">您可以將屬性附加至中繼資料範圍為整個利用[imetadataemit:: Setmoduleprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)或是[imetadataemit:: Definecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)方法，視需要。</span><span class="sxs-lookup"><span data-stu-id="68952-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68952-117">需求</span><span class="sxs-lookup"><span data-stu-id="68952-117">Requirements</span></span>  
 <span data-ttu-id="68952-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="68952-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68952-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="68952-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68952-120">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="68952-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="68952-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68952-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68952-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68952-122">See also</span></span>

- [<span data-ttu-id="68952-123">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="68952-123">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="68952-124">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="68952-124">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="68952-125">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="68952-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="68952-126">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="68952-126">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="68952-127">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="68952-127">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
