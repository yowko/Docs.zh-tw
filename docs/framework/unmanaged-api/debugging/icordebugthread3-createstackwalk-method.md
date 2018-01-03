---
title: "ICorDebugThread3::CreateStackWalk 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread3.CreateStackWalk Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread3::CreateStackWalk
helpviewer_keywords:
- CreateStackWalk method [.NET Framework debugging]
- ICorDebugThread3::CreateStackWalk method [.NET Framework debugging]
ms.assetid: c55e35d9-f9aa-4268-94b5-dce44c61acf2
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3b587a69c7acc3115c282eac065d304dc892b80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="d47b9-102">ICorDebugThread3::CreateStackWalk 方法</span><span class="sxs-lookup"><span data-stu-id="d47b9-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="d47b9-103">建立[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)執行緒的堆疊回溯您想要的物件。</span><span class="sxs-lookup"><span data-stu-id="d47b9-103">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d47b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="d47b9-104">Syntax</span></span>  
  
```  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d47b9-105">參數</span><span class="sxs-lookup"><span data-stu-id="d47b9-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="d47b9-106">[out]位址的指標[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)執行緒的堆疊回溯您想要的物件。</span><span class="sxs-lookup"><span data-stu-id="d47b9-106">[out] A pointer to address of the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d47b9-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d47b9-107">Return Value</span></span>  
 <span data-ttu-id="d47b9-108">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="d47b9-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d47b9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d47b9-109">HRESULT</span></span>|<span data-ttu-id="d47b9-110">描述</span><span class="sxs-lookup"><span data-stu-id="d47b9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d47b9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d47b9-111">S_OK</span></span>|<span data-ttu-id="d47b9-112">`ICorDebugStackWalk`物件已建立成功。</span><span class="sxs-lookup"><span data-stu-id="d47b9-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="d47b9-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d47b9-113">E_FAIL</span></span>|<span data-ttu-id="d47b9-114">`ICorDebugStackWalk`未建立物件。</span><span class="sxs-lookup"><span data-stu-id="d47b9-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="d47b9-115">例外狀況</span><span class="sxs-lookup"><span data-stu-id="d47b9-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d47b9-116">備註</span><span class="sxs-lookup"><span data-stu-id="d47b9-116">Remarks</span></span>  
 <span data-ttu-id="d47b9-117">如果`CreateStackWalk`方法成功則傳回`ICorDebugStackWalk`物件的內容設為執行緒的目前內容。</span><span class="sxs-lookup"><span data-stu-id="d47b9-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d47b9-118">需求</span><span class="sxs-lookup"><span data-stu-id="d47b9-118">Requirements</span></span>  
 <span data-ttu-id="d47b9-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d47b9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d47b9-120">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d47b9-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d47b9-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d47b9-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d47b9-122">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d47b9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d47b9-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="d47b9-123">See Also</span></span>  
 [<span data-ttu-id="d47b9-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d47b9-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d47b9-125">偵錯</span><span class="sxs-lookup"><span data-stu-id="d47b9-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
