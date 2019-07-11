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
ms.openlocfilehash: be8d860f508644e68bf69892a63e145e7ffd5b90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740241"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="37df8-102">CorDebugDebugEventKind 列舉</span><span class="sxs-lookup"><span data-stu-id="37df8-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="37df8-103">表示的事件解碼其資訊的型別[DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="37df8-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37df8-104">語法</span><span class="sxs-lookup"><span data-stu-id="37df8-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="37df8-105">成員</span><span class="sxs-lookup"><span data-stu-id="37df8-105">Members</span></span>  
  
|<span data-ttu-id="37df8-106">成員</span><span class="sxs-lookup"><span data-stu-id="37df8-106">Member</span></span>|<span data-ttu-id="37df8-107">描述</span><span class="sxs-lookup"><span data-stu-id="37df8-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="37df8-108">模組載入事件。</span><span class="sxs-lookup"><span data-stu-id="37df8-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="37df8-109">模組卸載事件。</span><span class="sxs-lookup"><span data-stu-id="37df8-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="37df8-110">第一個可能發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="37df8-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="37df8-111">第一個可能發生的使用者例外狀況。</span><span class="sxs-lookup"><span data-stu-id="37df8-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="37df8-112">存在 `catch` 處理常式的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="37df8-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="37df8-113">未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="37df8-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37df8-114">備註</span><span class="sxs-lookup"><span data-stu-id="37df8-114">Remarks</span></span>  
 <span data-ttu-id="37df8-115">成員`CorDebugDebugEventKind`列舉型別由呼叫[icordebugdebugevent:: Geteventkind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="37df8-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37df8-116">這個列舉僅適用於 .NET Native 偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="37df8-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37df8-117">需求</span><span class="sxs-lookup"><span data-stu-id="37df8-117">Requirements</span></span>  
 <span data-ttu-id="37df8-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="37df8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37df8-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37df8-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37df8-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37df8-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37df8-121">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37df8-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37df8-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37df8-122">See also</span></span>

- [<span data-ttu-id="37df8-123">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="37df8-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
