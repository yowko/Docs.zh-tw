---
title: ICorDebugModule2::ApplyChanges 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
ms.openlocfilehash: c324019e1e62701f4f2aaba1c00948b292ba6847
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127904"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="97727-102">ICorDebugModule2::ApplyChanges 方法</span><span class="sxs-lookup"><span data-stu-id="97727-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="97727-103">將中繼資料中的變更和 Microsoft 中繼語言（MSIL）程式碼中的變更套用至執行中的進程。</span><span class="sxs-lookup"><span data-stu-id="97727-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97727-104">語法</span><span class="sxs-lookup"><span data-stu-id="97727-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97727-105">參數</span><span class="sxs-lookup"><span data-stu-id="97727-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="97727-106">在差異中繼資料的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="97727-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="97727-107">在包含差異中繼資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="97727-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="97727-108">緩衝區的位址會從[IMetaDataEmit2：： SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)方法傳回。</span><span class="sxs-lookup"><span data-stu-id="97727-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="97727-109">中繼資料中的相對虛擬位址（Rva）應該相對於 MSIL 程式碼的開頭。</span><span class="sxs-lookup"><span data-stu-id="97727-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="97727-110">在差異 MSIL 程式碼的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="97727-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="97727-111">在包含更新的 MSIL 程式碼的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="97727-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97727-112">備註</span><span class="sxs-lookup"><span data-stu-id="97727-112">Remarks</span></span>  
 <span data-ttu-id="97727-113">`pbMetadata` 參數是特殊的差異元資料格式（如[IMetaDataEmit2：： SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)所輸出）。</span><span class="sxs-lookup"><span data-stu-id="97727-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="97727-114">`pbMetadata` 會將先前的中繼資料當做基底，並描述要套用至該基底的個別變更。</span><span class="sxs-lookup"><span data-stu-id="97727-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="97727-115">相反地，`pbIL[`] 參數包含新的 MSIL 做為已更新的方法，其目的是要完全取代該方法先前的 MSIL</span><span class="sxs-lookup"><span data-stu-id="97727-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="97727-116">在偵錯工具的記憶體中建立 delta MSIL 和中繼資料時，偵錯工具會呼叫 `ApplyChanges` 將變更傳送至 common language runtime （CLR）。</span><span class="sxs-lookup"><span data-stu-id="97727-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="97727-117">執行時間會更新其中繼資料資料表，將新的 MSIL 放在進程中，並設定新 MSIL 的即時（JIT）編譯。</span><span class="sxs-lookup"><span data-stu-id="97727-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="97727-118">套用變更之後，偵錯工具應該呼叫[IMetaDataEmit2：： ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)來準備下一個編輯會話。</span><span class="sxs-lookup"><span data-stu-id="97727-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="97727-119">偵錯工具可能會繼續處理。</span><span class="sxs-lookup"><span data-stu-id="97727-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="97727-120">每當偵錯工具在具有 delta 中繼資料的模組上呼叫 `ApplyChanges` 時，它也應該在該模組中繼資料的所有複本上，使用相同的差異中繼資料來呼叫[IMetaDataEmit：： ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) ，但用來發出變更的複本除外。</span><span class="sxs-lookup"><span data-stu-id="97727-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="97727-121">如果中繼資料的複本與實際的中繼資料有某種的同步，則偵錯工具一律會擲回該複本並取得新的複本。</span><span class="sxs-lookup"><span data-stu-id="97727-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="97727-122">如果 `ApplyChanges` 方法失敗，則 debug 會話會處於無效狀態，而且必須重新開機。</span><span class="sxs-lookup"><span data-stu-id="97727-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97727-123">需求</span><span class="sxs-lookup"><span data-stu-id="97727-123">Requirements</span></span>  
 <span data-ttu-id="97727-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97727-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97727-125">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97727-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97727-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97727-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97727-127">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97727-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
