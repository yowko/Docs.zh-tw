---
title: CorDebugDebugEventKind 列舉
ms.date: 03/30/2017
api_name:
- CorDebugDebugEventKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2e01a5cf2b2aa25e91ebf0f8e3927858b12bea3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967560"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="3345b-102">CorDebugDebugEventKind 列舉</span><span class="sxs-lookup"><span data-stu-id="3345b-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="3345b-103">表示[DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)方法解碼其資訊的事件種類。</span><span class="sxs-lookup"><span data-stu-id="3345b-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3345b-104">語法</span><span class="sxs-lookup"><span data-stu-id="3345b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="3345b-105">成員</span><span class="sxs-lookup"><span data-stu-id="3345b-105">Members</span></span>  
  
|<span data-ttu-id="3345b-106">成員</span><span class="sxs-lookup"><span data-stu-id="3345b-106">Member</span></span>|<span data-ttu-id="3345b-107">說明</span><span class="sxs-lookup"><span data-stu-id="3345b-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="3345b-108">模組載入事件。</span><span class="sxs-lookup"><span data-stu-id="3345b-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="3345b-109">模組卸載事件。</span><span class="sxs-lookup"><span data-stu-id="3345b-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="3345b-110">第一個可能發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3345b-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="3345b-111">第一個可能發生的使用者例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3345b-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="3345b-112">存在 `catch` 處理常式的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3345b-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="3345b-113">未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3345b-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3345b-114">備註</span><span class="sxs-lookup"><span data-stu-id="3345b-114">Remarks</span></span>  
 <span data-ttu-id="3345b-115">`CorDebugDebugEventKind`列舉的成員會藉由呼叫[ICorDebugDebugEvent:: GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)方法來傳回。</span><span class="sxs-lookup"><span data-stu-id="3345b-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3345b-116">這個列舉僅適用於 .NET Native 偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="3345b-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3345b-117">需求</span><span class="sxs-lookup"><span data-stu-id="3345b-117">Requirements</span></span>  
 <span data-ttu-id="3345b-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3345b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3345b-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3345b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3345b-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3345b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3345b-121">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3345b-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3345b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3345b-122">See also</span></span>

- [<span data-ttu-id="3345b-123">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="3345b-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
