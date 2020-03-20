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
ms.openlocfilehash: 2f9325f3795262a0c33af02f87fc5d3a020658cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177646"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="50735-102">IMetaDataDispenser::DefineScope 方法</span><span class="sxs-lookup"><span data-stu-id="50735-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="50735-103">在記憶體中創建一個新區域，您可以在其中創建新中繼資料。</span><span class="sxs-lookup"><span data-stu-id="50735-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50735-104">語法</span><span class="sxs-lookup"><span data-stu-id="50735-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50735-105">參數</span><span class="sxs-lookup"><span data-stu-id="50735-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="50735-106">[在]要創建的元資料結構版本的 CLSID。</span><span class="sxs-lookup"><span data-stu-id="50735-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="50735-107">此值必須CLSID_CorMetaDataRuntime .NET 框架版本 2.0。</span><span class="sxs-lookup"><span data-stu-id="50735-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="50735-108">[在]指定選項的標誌。</span><span class="sxs-lookup"><span data-stu-id="50735-108">[in] Flags that specify options.</span></span> <span data-ttu-id="50735-109">此值對於 .NET 框架 2.0 必須為零。</span><span class="sxs-lookup"><span data-stu-id="50735-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="50735-110">[在]要返回的所需中繼資料介面的 IID;調用方將使用介面創建新中繼資料。</span><span class="sxs-lookup"><span data-stu-id="50735-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="50735-111">的值`riid`必須指定其中一個"emit"介面。</span><span class="sxs-lookup"><span data-stu-id="50735-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="50735-112">有效值IID_IMetaDataEmit、IID_IMetaDataAssemblyEmit 或IID_IMetaDataEmit2。</span><span class="sxs-lookup"><span data-stu-id="50735-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="50735-113">[出]指向返回介面的指標。</span><span class="sxs-lookup"><span data-stu-id="50735-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50735-114">備註</span><span class="sxs-lookup"><span data-stu-id="50735-114">Remarks</span></span>  
 <span data-ttu-id="50735-115">`DefineScope`創建一組記憶體中中繼資料表，為中繼資料生成唯一 GUID（模組版本識別碼或 MVID），並在模組表中為發出的編譯單元創建一個條目。</span><span class="sxs-lookup"><span data-stu-id="50735-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="50735-116">您可以根據需要使用[IMetaDataEmit：setModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md)或[IMetaDataEmit：:DefineCustom屬性](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)方法將屬性附加到整個中繼資料範圍。</span><span class="sxs-lookup"><span data-stu-id="50735-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50735-117">需求</span><span class="sxs-lookup"><span data-stu-id="50735-117">Requirements</span></span>  
 <span data-ttu-id="50735-118">**平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="50735-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50735-119">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="50735-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50735-120">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="50735-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50735-121">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50735-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50735-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50735-122">See also</span></span>

- [<span data-ttu-id="50735-123">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="50735-123">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="50735-124">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="50735-124">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="50735-125">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="50735-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="50735-126">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="50735-126">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="50735-127">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="50735-127">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
