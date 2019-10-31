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
ms.openlocfilehash: de4ac1f39ea9cfb4b616bd4e2c85e5de530dbb0b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132223"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="f0946-102">CorDebugDebugEventKind 列舉</span><span class="sxs-lookup"><span data-stu-id="f0946-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="f0946-103">表示[DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)方法解碼其資訊的事件種類。</span><span class="sxs-lookup"><span data-stu-id="f0946-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0946-104">語法</span><span class="sxs-lookup"><span data-stu-id="f0946-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f0946-105">Members</span><span class="sxs-lookup"><span data-stu-id="f0946-105">Members</span></span>  
  
|<span data-ttu-id="f0946-106">成員</span><span class="sxs-lookup"><span data-stu-id="f0946-106">Member</span></span>|<span data-ttu-id="f0946-107">描述</span><span class="sxs-lookup"><span data-stu-id="f0946-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="f0946-108">模組載入事件。</span><span class="sxs-lookup"><span data-stu-id="f0946-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="f0946-109">模組卸載事件。</span><span class="sxs-lookup"><span data-stu-id="f0946-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="f0946-110">第一個可能發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f0946-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="f0946-111">第一個可能發生的使用者例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f0946-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="f0946-112">存在 `catch` 處理常式的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f0946-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="f0946-113">未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f0946-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0946-114">備註</span><span class="sxs-lookup"><span data-stu-id="f0946-114">Remarks</span></span>  
 <span data-ttu-id="f0946-115">呼叫[ICorDebugDebugEvent：： GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)方法會傳回 `CorDebugDebugEventKind` 列舉的成員。</span><span class="sxs-lookup"><span data-stu-id="f0946-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0946-116">這個列舉僅適用於 .NET Native 偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="f0946-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0946-117">需求</span><span class="sxs-lookup"><span data-stu-id="f0946-117">Requirements</span></span>  
 <span data-ttu-id="f0946-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f0946-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0946-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0946-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0946-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0946-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0946-121">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0946-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0946-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="f0946-122">See also</span></span>

- [<span data-ttu-id="f0946-123">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="f0946-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
