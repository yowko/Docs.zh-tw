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
ms.openlocfilehash: 87a39350986cb7bb62f76b0d9a6a9aae8f82e2f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726089"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="9c11c-102">IMetaDataDispenser::DefineScope 方法</span><span class="sxs-lookup"><span data-stu-id="9c11c-102">IMetaDataDispenser::DefineScope Method</span></span>

<span data-ttu-id="9c11c-103">在記憶體中建立新的區域，您可以在其中建立新的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9c11c-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c11c-104">語法</span><span class="sxs-lookup"><span data-stu-id="9c11c-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c11c-105">參數</span><span class="sxs-lookup"><span data-stu-id="9c11c-105">Parameters</span></span>  

 `rclsid`  
 <span data-ttu-id="9c11c-106">在要建立之元資料結構版本的 CLSID。</span><span class="sxs-lookup"><span data-stu-id="9c11c-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="9c11c-107">此值必須是 .NET Framework 2.0 版的 CLSID_CorMetaDataRuntime。</span><span class="sxs-lookup"><span data-stu-id="9c11c-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="9c11c-108">在指定選項的旗標。</span><span class="sxs-lookup"><span data-stu-id="9c11c-108">[in] Flags that specify options.</span></span> <span data-ttu-id="9c11c-109">.NET Framework 2.0 的這個值必須是零。</span><span class="sxs-lookup"><span data-stu-id="9c11c-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="9c11c-110">在要傳回之所需中繼資料介面的 IID;呼叫端會使用介面來建立新的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9c11c-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="9c11c-111">的值 `riid` 必須指定其中一個「發出」介面。</span><span class="sxs-lookup"><span data-stu-id="9c11c-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="9c11c-112">有效的值為 IID_IMetaDataEmit、IID_IMetaDataAssemblyEmit 或 IID_IMetaDataEmit2。</span><span class="sxs-lookup"><span data-stu-id="9c11c-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="9c11c-113">擴展傳回之介面的指標。</span><span class="sxs-lookup"><span data-stu-id="9c11c-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c11c-114">備註</span><span class="sxs-lookup"><span data-stu-id="9c11c-114">Remarks</span></span>  

 <span data-ttu-id="9c11c-115">`DefineScope` 建立一組記憶體中的中繼資料資料表、產生唯一 GUID (模組版本識別碼，或中繼資料的 MVID) ，然後在模組資料表中為所發出的編譯單位建立一個專案。</span><span class="sxs-lookup"><span data-stu-id="9c11c-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="9c11c-116">您可以視需要使用 [IMetaDataEmit：： SetModuleProps](imetadataemit-setmoduleprops-method.md) 或 [IMetaDataEmit：:D efinecustomattribute](imetadataemit-definecustomattribute-method.md) 方法，將屬性附加至整個中繼資料範圍。</span><span class="sxs-lookup"><span data-stu-id="9c11c-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c11c-117">需求</span><span class="sxs-lookup"><span data-stu-id="9c11c-117">Requirements</span></span>  

 <span data-ttu-id="9c11c-118">**平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9c11c-118">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c11c-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="9c11c-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c11c-120">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="9c11c-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c11c-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c11c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c11c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c11c-122">See also</span></span>

- [<span data-ttu-id="9c11c-123">IMetaDataDispenser 介面</span><span class="sxs-lookup"><span data-stu-id="9c11c-123">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="9c11c-124">IMetaDataDispenserEx 介面</span><span class="sxs-lookup"><span data-stu-id="9c11c-124">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="9c11c-125">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="9c11c-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="9c11c-126">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="9c11c-126">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9c11c-127">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="9c11c-127">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
