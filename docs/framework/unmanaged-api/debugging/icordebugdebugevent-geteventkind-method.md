---
title: ICorDebugDebugEvent::GetEventKind 方法
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a87dda8d8a263df1989a685d94c5163212f41382
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911344"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="68f3b-102">ICorDebugDebugEvent::GetEventKind 方法</span><span class="sxs-lookup"><span data-stu-id="68f3b-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="68f3b-103">指出這個 `ICorDebugDebugEvent` 物件所代表的事件類型。</span><span class="sxs-lookup"><span data-stu-id="68f3b-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68f3b-104">語法</span><span class="sxs-lookup"><span data-stu-id="68f3b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68f3b-105">參數</span><span class="sxs-lookup"><span data-stu-id="68f3b-105">Parameters</span></span>  
 <span data-ttu-id="68f3b-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="68f3b-106">pDebugEventKind</span></span>  
 <span data-ttu-id="68f3b-107">表示事件種類之[CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)列舉成員的指標。</span><span class="sxs-lookup"><span data-stu-id="68f3b-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68f3b-108">備註</span><span class="sxs-lookup"><span data-stu-id="68f3b-108">Remarks</span></span>  
 <span data-ttu-id="68f3b-109">根據 `pDebugEventKind` 的值，您可以呼叫 `QueryInterface` 以取得包含其他資料的更精確偵錯事件介面。</span><span class="sxs-lookup"><span data-stu-id="68f3b-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68f3b-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="68f3b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68f3b-111">需求</span><span class="sxs-lookup"><span data-stu-id="68f3b-111">Requirements</span></span>  
 <span data-ttu-id="68f3b-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="68f3b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68f3b-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68f3b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68f3b-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68f3b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68f3b-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68f3b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f3b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68f3b-116">See also</span></span>

- [<span data-ttu-id="68f3b-117">ICorDebugDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="68f3b-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="68f3b-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="68f3b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
