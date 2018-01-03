---
title: "ICorDebugProcess5::EnumerateGCReferences 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateGCReferences
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44975a7896c71ce8061dedde13d31c4fbb88d6a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="65926-102">ICorDebugProcess5::EnumerateGCReferences 方法</span><span class="sxs-lookup"><span data-stu-id="65926-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="65926-103">取得要進行記憶體回收處理序中的所有物件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="65926-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65926-104">語法</span><span class="sxs-lookup"><span data-stu-id="65926-104">Syntax</span></span>  
  
```  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65926-105">參數</span><span class="sxs-lookup"><span data-stu-id="65926-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="65926-106">[in]表示弱式參考是否也要列舉的布林值。</span><span class="sxs-lookup"><span data-stu-id="65926-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="65926-107">如果`enumerateWeakReferences`是`true`、`ppEnum`列舉值包含強式參考和弱式參考。</span><span class="sxs-lookup"><span data-stu-id="65926-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="65926-108">如果`enumerateWeakReferences`是`false`，此列舉值包含強式的參考。</span><span class="sxs-lookup"><span data-stu-id="65926-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="65926-109">[out]位址指標[ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)也就是列舉值物件以進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="65926-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65926-110">備註</span><span class="sxs-lookup"><span data-stu-id="65926-110">Remarks</span></span>  
 <span data-ttu-id="65926-111">這個方法會提供一個方式來判斷處理程序中的任何 managed 物件的完整將根鏈結，而且可用來判斷物件仍在執行的原因。</span><span class="sxs-lookup"><span data-stu-id="65926-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65926-112">需求</span><span class="sxs-lookup"><span data-stu-id="65926-112">Requirements</span></span>  
 <span data-ttu-id="65926-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="65926-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65926-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65926-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65926-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65926-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65926-116">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65926-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65926-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="65926-117">See Also</span></span>  
 [<span data-ttu-id="65926-118">ICorDebugProcess5 介面</span><span class="sxs-lookup"><span data-stu-id="65926-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="65926-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="65926-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
