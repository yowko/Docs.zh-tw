---
title: ICorDebugValueBreakpoint Interface
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
ms.openlocfilehash: cf0a87afd1c0057c054205432fea7aa5844afb53
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684404"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="d08af-102">ICorDebugValueBreakpoint Interface</span><span class="sxs-lookup"><span data-stu-id="d08af-102">ICorDebugValueBreakpoint Interface</span></span>

<span data-ttu-id="d08af-103">擴充 ICorDebugBreakpoint 介面，以提供特定值的存取權。</span><span class="sxs-lookup"><span data-stu-id="d08af-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d08af-104">方法</span><span class="sxs-lookup"><span data-stu-id="d08af-104">Methods</span></span>  
  
|<span data-ttu-id="d08af-105">方法</span><span class="sxs-lookup"><span data-stu-id="d08af-105">Method</span></span>|<span data-ttu-id="d08af-106">描述</span><span class="sxs-lookup"><span data-stu-id="d08af-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d08af-107">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="d08af-107">GetValue Method</span></span>](icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="d08af-108">取得 ICorDebugValue 物件的介面指標，該物件表示設定中斷點時所依據的物件值。</span><span class="sxs-lookup"><span data-stu-id="d08af-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d08af-109">備註</span><span class="sxs-lookup"><span data-stu-id="d08af-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d08af-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="d08af-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d08af-111">需求</span><span class="sxs-lookup"><span data-stu-id="d08af-111">Requirements</span></span>  

 <span data-ttu-id="d08af-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d08af-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d08af-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d08af-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d08af-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d08af-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d08af-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d08af-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d08af-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d08af-116">See also</span></span>

- [<span data-ttu-id="d08af-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d08af-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
