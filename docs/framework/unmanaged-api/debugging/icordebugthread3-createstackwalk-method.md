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
ms.openlocfilehash: 64f6bc9abb8105cdfa942c2aaca71994e8a91765
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791408"
---
# <a name="icordebugthread3createstackwalk-method"></a><span data-ttu-id="1d80f-102">ICorDebugThread3::CreateStackWalk 方法</span><span class="sxs-lookup"><span data-stu-id="1d80f-102">ICorDebugThread3::CreateStackWalk Method</span></span>
<span data-ttu-id="1d80f-103">為您要回溯其堆疊的執行緒建立[ICorDebugStackWalk](icordebugstackwalk-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="1d80f-103">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d80f-104">語法</span><span class="sxs-lookup"><span data-stu-id="1d80f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateStackWalk([out] ICorDebugStackWalk **ppStackWalk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d80f-105">參數</span><span class="sxs-lookup"><span data-stu-id="1d80f-105">Parameters</span></span>  
 `ppStackWalk`  
 <span data-ttu-id="1d80f-106">脫銷要回溯其堆疊的執行緒之[ICorDebugStackWalk](icordebugstackwalk-interface.md)物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="1d80f-106">[out] A pointer to address of the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d80f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="1d80f-107">Return Value</span></span>  
 <span data-ttu-id="1d80f-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="1d80f-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1d80f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d80f-109">HRESULT</span></span>|<span data-ttu-id="1d80f-110">描述</span><span class="sxs-lookup"><span data-stu-id="1d80f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d80f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1d80f-111">S_OK</span></span>|<span data-ttu-id="1d80f-112">已成功建立 `ICorDebugStackWalk` 物件。</span><span class="sxs-lookup"><span data-stu-id="1d80f-112">The `ICorDebugStackWalk` object was successfully created.</span></span>|  
|<span data-ttu-id="1d80f-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1d80f-113">E_FAIL</span></span>|<span data-ttu-id="1d80f-114">未建立 `ICorDebugStackWalk` 物件。</span><span class="sxs-lookup"><span data-stu-id="1d80f-114">The `ICorDebugStackWalk` object was not created.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="1d80f-115">例外狀況</span><span class="sxs-lookup"><span data-stu-id="1d80f-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d80f-116">備註</span><span class="sxs-lookup"><span data-stu-id="1d80f-116">Remarks</span></span>  
 <span data-ttu-id="1d80f-117">如果 `CreateStackWalk` 方法成功，則傳回的 `ICorDebugStackWalk` 物件內容會設定為執行緒的目前內容。</span><span class="sxs-lookup"><span data-stu-id="1d80f-117">If the `CreateStackWalk` method succeeds, the returned `ICorDebugStackWalk` object's context is set to the thread's current context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d80f-118">需求</span><span class="sxs-lookup"><span data-stu-id="1d80f-118">Requirements</span></span>  
 <span data-ttu-id="1d80f-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d80f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d80f-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d80f-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d80f-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d80f-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d80f-122">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d80f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d80f-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="1d80f-123">See also</span></span>

- [<span data-ttu-id="1d80f-124">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1d80f-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1d80f-125">偵錯</span><span class="sxs-lookup"><span data-stu-id="1d80f-125">Debugging</span></span>](index.md)
