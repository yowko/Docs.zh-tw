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
ms.openlocfilehash: e348e0070a5ce619f95dad9ebe4085d17f7ade6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733369"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="9ed9c-102">CorDebugDebugEventKind 列舉</span><span class="sxs-lookup"><span data-stu-id="9ed9c-102">CorDebugDebugEventKind Enumeration</span></span>

<span data-ttu-id="9ed9c-103">表示 [DecodeEvent](icordebugprocess6-decodeevent-method.md) 方法解碼其資訊的事件種類。</span><span class="sxs-lookup"><span data-stu-id="9ed9c-103">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ed9c-104">語法</span><span class="sxs-lookup"><span data-stu-id="9ed9c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="9ed9c-105">成員</span><span class="sxs-lookup"><span data-stu-id="9ed9c-105">Members</span></span>  
  
|<span data-ttu-id="9ed9c-106">member</span><span class="sxs-lookup"><span data-stu-id="9ed9c-106">Member</span></span>|<span data-ttu-id="9ed9c-107">描述</span><span class="sxs-lookup"><span data-stu-id="9ed9c-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="9ed9c-108">模組載入事件。</span><span class="sxs-lookup"><span data-stu-id="9ed9c-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="9ed9c-109">模組卸載事件。</span><span class="sxs-lookup"><span data-stu-id="9ed9c-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="9ed9c-110">第一個可能發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9ed9c-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="9ed9c-111">第一個可能發生的使用者例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9ed9c-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="9ed9c-112">存在 `catch` 處理常式的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9ed9c-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="9ed9c-113">未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9ed9c-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ed9c-114">備註</span><span class="sxs-lookup"><span data-stu-id="9ed9c-114">Remarks</span></span>  

 <span data-ttu-id="9ed9c-115">`CorDebugDebugEventKind`呼叫[ICorDebugDebugEvent：： GetEventKind](icordebugdebugevent-geteventkind-method.md)方法會傳回列舉的成員。</span><span class="sxs-lookup"><span data-stu-id="9ed9c-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ed9c-116">這個列舉僅適用於 .NET Native 偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="9ed9c-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ed9c-117">需求</span><span class="sxs-lookup"><span data-stu-id="9ed9c-117">Requirements</span></span>  

 <span data-ttu-id="9ed9c-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9ed9c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ed9c-119">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ed9c-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ed9c-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ed9c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ed9c-121">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ed9c-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed9c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ed9c-122">See also</span></span>

- [<span data-ttu-id="9ed9c-123">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="9ed9c-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
