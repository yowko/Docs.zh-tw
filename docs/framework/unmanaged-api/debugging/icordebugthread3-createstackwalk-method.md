---
title: ICorDebugThread3::CreateStackWalk 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.CreateStackWalk Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7969d8482970b13951938203262f6ce8f9bf574a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229299"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="62988-102">ICorDebugThread3::CreateStackWalk 方法</span><span class="sxs-lookup"><span data-stu-id="62988-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="62988-103">會建立[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)執行緒要回溯的堆疊的物件。</span><span class="sxs-lookup"><span data-stu-id="62988-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62988-104">語法</span><span class="sxs-lookup"><span data-stu-id="62988-104">Syntax</span></span>  
  
```  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62988-105">參數</span><span class="sxs-lookup"><span data-stu-id="62988-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="62988-106">[out]位址的指標[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)執行緒要回溯的堆疊的物件。</span><span class="sxs-lookup"><span data-stu-id="62988-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62988-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="62988-107">Return Value</span></span>  
 <span data-ttu-id="62988-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="62988-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="62988-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="62988-109">HRESULT</span></span>|<span data-ttu-id="62988-110">描述</span><span class="sxs-lookup"><span data-stu-id="62988-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62988-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="62988-111">S_OK</span></span>|<span data-ttu-id="62988-112">`ICorDebugStackWalk`物件已成功建立。</span><span class="sxs-lookup"><span data-stu-id="62988-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="62988-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="62988-113">E_FAIL</span></span>|<span data-ttu-id="62988-114">`ICorDebugStackWalk`未建立物件。</span><span class="sxs-lookup"><span data-stu-id="62988-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="62988-115">例外狀況</span><span class="sxs-lookup"><span data-stu-id="62988-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62988-116">備註</span><span class="sxs-lookup"><span data-stu-id="62988-116">Remarks</span></span>  
 <span data-ttu-id="62988-117">如果`CreateStackWalk`方法成功，傳回`ICorDebugStackWalk`物件的內容會設定為執行緒的目前內容。</span><span class="sxs-lookup"><span data-stu-id="62988-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62988-118">需求</span><span class="sxs-lookup"><span data-stu-id="62988-118">Requirements</span></span>  
 <span data-ttu-id="62988-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62988-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62988-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62988-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62988-121">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62988-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="62988-122">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="62988-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="62988-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62988-123">See also</span></span>

- [<span data-ttu-id="62988-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="62988-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="62988-125">偵錯</span><span class="sxs-lookup"><span data-stu-id="62988-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
