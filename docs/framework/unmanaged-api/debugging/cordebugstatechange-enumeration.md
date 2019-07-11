---
title: CorDebugStateChange 列舉
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 676489880cb30ca540cb78d70797dbf4eedf7395
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739593"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="05f2c-102">CorDebugStateChange 列舉</span><span class="sxs-lookup"><span data-stu-id="05f2c-102">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="05f2c-103">描述依據處理序變更而必須捨棄的快取資料量。</span><span class="sxs-lookup"><span data-stu-id="05f2c-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="05f2c-104">語法</span><span class="sxs-lookup"><span data-stu-id="05f2c-104">Syntax</span></span>

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="05f2c-105">成員</span><span class="sxs-lookup"><span data-stu-id="05f2c-105">Members</span></span>

| <span data-ttu-id="05f2c-106">成員</span><span class="sxs-lookup"><span data-stu-id="05f2c-106">Member</span></span>            | <span data-ttu-id="05f2c-107">描述</span><span class="sxs-lookup"><span data-stu-id="05f2c-107">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="05f2c-108">處理序透過向前執行已達到新的記憶體狀態。</span><span class="sxs-lookup"><span data-stu-id="05f2c-108">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="05f2c-109">指定的處理序記憶體可能與先前的記憶體不同。</span><span class="sxs-lookup"><span data-stu-id="05f2c-109">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="05f2c-110">備註</span><span class="sxs-lookup"><span data-stu-id="05f2c-110">Remarks</span></span>

 <span data-ttu-id="05f2c-111">成員`CorDebugStateChange`列舉型別提供做為引數，當偵錯工具呼叫`ProcessStateChanged`方法使用[ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md)或[ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="05f2c-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="05f2c-112">需求</span><span class="sxs-lookup"><span data-stu-id="05f2c-112">Requirements</span></span>

 <span data-ttu-id="05f2c-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="05f2c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="05f2c-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05f2c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="05f2c-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05f2c-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="05f2c-116">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05f2c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="05f2c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05f2c-117">See also</span></span>

- [<span data-ttu-id="05f2c-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="05f2c-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="05f2c-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="05f2c-119">Debugging</span></span>](index.md)
