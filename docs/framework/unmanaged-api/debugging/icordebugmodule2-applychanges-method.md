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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab0e28bd21b66f370a1a1e82359fe474574fd7bb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481570"
---
# <a name="icordebugmodule2applychanges-method"></a><span data-ttu-id="48f4d-102">ICorDebugModule2::ApplyChanges 方法</span><span class="sxs-lookup"><span data-stu-id="48f4d-102">ICorDebugModule2::ApplyChanges Method</span></span>
<span data-ttu-id="48f4d-103">適用於執行中處理序在中繼資料中的變更和 Microsoft intermediate language (MSIL) 程式碼中的變更。</span><span class="sxs-lookup"><span data-stu-id="48f4d-103">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48f4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="48f4d-104">Syntax</span></span>  
  
```  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48f4d-105">參數</span><span class="sxs-lookup"><span data-stu-id="48f4d-105">Parameters</span></span>  
 `cbMetadata`  
 <span data-ttu-id="48f4d-106">[in]以位元組為單位的差異中繼資料的大小。</span><span class="sxs-lookup"><span data-stu-id="48f4d-106">[in] Size, in bytes, of the delta metadata.</span></span>  
  
 `pbMetadata`  
 <span data-ttu-id="48f4d-107">[in]包含差異中繼資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="48f4d-107">[in] Buffer that contains the delta metadata.</span></span> <span data-ttu-id="48f4d-108">從傳回的緩衝區位址[IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="48f4d-108">The address of the buffer is returned from the [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) method.</span></span>  
  
 <span data-ttu-id="48f4d-109">中繼資料中的相對虛擬位址 (Rva) 應該是相對於 MSIL 程式碼的開頭。</span><span class="sxs-lookup"><span data-stu-id="48f4d-109">The relative virtual addresses (RVAs) in the metadata should be relative to the start of the MSIL code.</span></span>  
  
 `cbIL`  
 <span data-ttu-id="48f4d-110">[in]大小，以位元組為單位的 MSIL 程式碼的差異。</span><span class="sxs-lookup"><span data-stu-id="48f4d-110">[in] Size, in bytes, of the delta MSIL code.</span></span>  
  
 `pbIL`  
 <span data-ttu-id="48f4d-111">[in]包含更新的 MSIL 程式碼的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="48f4d-111">[in] Buffer that contains the updated MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48f4d-112">備註</span><span class="sxs-lookup"><span data-stu-id="48f4d-112">Remarks</span></span>  
 <span data-ttu-id="48f4d-113">`pbMetadata`參數的特殊差異中繼資料格式 (如輸出所[IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md))。</span><span class="sxs-lookup"><span data-stu-id="48f4d-113">The `pbMetadata` parameter is in a special delta metadata format (as output by [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)).</span></span> <span data-ttu-id="48f4d-114">`pbMetadata` 接受做為基底的上一個中繼資料，並描述要套用至該基底的個別變更。</span><span class="sxs-lookup"><span data-stu-id="48f4d-114">`pbMetadata` takes previous metadata as a base and describes individual changes to apply to that base.</span></span>  
  
 <span data-ttu-id="48f4d-115">相反地， `pbIL[`] 參數包含更新的方法，新的 MSIL，而且完全取代該方法的先前 MSIL</span><span class="sxs-lookup"><span data-stu-id="48f4d-115">In contrast, the `pbIL[`] parameter contains the new MSIL for the updated method, and is meant to completely replace the previous MSIL for that method</span></span>  
  
 <span data-ttu-id="48f4d-116">當差異 MSIL 和中繼資料中已建立偵錯工具的記憶體時，偵錯工具就會呼叫`ApplyChanges`傳送到 common language runtime (CLR) 的變更。</span><span class="sxs-lookup"><span data-stu-id="48f4d-116">When the delta MSIL and the metadata have been created in the debugger’s memory, the debugger calls `ApplyChanges` to send the changes into the common language runtime (CLR).</span></span> <span data-ttu-id="48f4d-117">執行階段更新及其中繼資料資料表、 將新的 MSIL 放到程序，並設定新的 MSIL-just-in-time (JIT) 編譯。</span><span class="sxs-lookup"><span data-stu-id="48f4d-117">The runtime updates its metadata tables, places the new MSIL into the process, and sets up a just-in-time (JIT) compilation of the new MSIL.</span></span> <span data-ttu-id="48f4d-118">偵錯工具時已套用所做的變更，應該呼叫[IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)準備的下一個編輯工作階段。</span><span class="sxs-lookup"><span data-stu-id="48f4d-118">When the changes have been applied, the debugger should call [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) to prepare for the next editing session.</span></span> <span data-ttu-id="48f4d-119">偵錯工具就可以繼續處理程序。</span><span class="sxs-lookup"><span data-stu-id="48f4d-119">The debugger may then continue the process.</span></span>  
  
 <span data-ttu-id="48f4d-120">每當偵錯工具會呼叫`ApplyChanges`上有差異的中繼資料的模組，它也應該呼叫[imetadataemit:: Applyeditandcontinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)與該模組的中繼資料，但複本的其複本的所有相同的差異中繼資料用來發出所做的變更。</span><span class="sxs-lookup"><span data-stu-id="48f4d-120">Whenever the debugger calls `ApplyChanges` on a module that has delta metadata, it should also call [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) with the same delta metadata on all of its copies of that module’s metadata except for the copy used to emit the changes.</span></span> <span data-ttu-id="48f4d-121">如果中繼資料的複本以某種方式變得同步處理與實際的中繼資料，偵錯工具可以一律擲出該複本，並取得新的複本。</span><span class="sxs-lookup"><span data-stu-id="48f4d-121">If a copy of the metadata somehow becomes out-of-sync with the actual metadata, the debugger can always throw away that copy and obtain a new copy.</span></span>  
  
 <span data-ttu-id="48f4d-122">如果`ApplyChanges`方法失敗，偵錯工作階段處於無效的狀態，必須重新啟動。</span><span class="sxs-lookup"><span data-stu-id="48f4d-122">If the `ApplyChanges` method fails, the debug session is in an invalid state and must be restarted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48f4d-123">需求</span><span class="sxs-lookup"><span data-stu-id="48f4d-123">Requirements</span></span>  
 <span data-ttu-id="48f4d-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="48f4d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48f4d-125">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48f4d-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48f4d-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48f4d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48f4d-127">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48f4d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
