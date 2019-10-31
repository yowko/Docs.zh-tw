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
ms.openlocfilehash: 239e3a82df0e6010278669f9f429bfad0d163319
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133716"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="e0887-102">CorDebugStateChange 列舉</span><span class="sxs-lookup"><span data-stu-id="e0887-102">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="e0887-103">描述依據處理序變更而必須捨棄的快取資料量。</span><span class="sxs-lookup"><span data-stu-id="e0887-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="e0887-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0887-104">Syntax</span></span>

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="e0887-105">Members</span><span class="sxs-lookup"><span data-stu-id="e0887-105">Members</span></span>

| <span data-ttu-id="e0887-106">成員</span><span class="sxs-lookup"><span data-stu-id="e0887-106">Member</span></span>            | <span data-ttu-id="e0887-107">描述</span><span class="sxs-lookup"><span data-stu-id="e0887-107">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="e0887-108">處理序透過向前執行已達到新的記憶體狀態。</span><span class="sxs-lookup"><span data-stu-id="e0887-108">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="e0887-109">指定的處理序記憶體可能與先前的記憶體不同。</span><span class="sxs-lookup"><span data-stu-id="e0887-109">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e0887-110">備註</span><span class="sxs-lookup"><span data-stu-id="e0887-110">Remarks</span></span>

 <span data-ttu-id="e0887-111">當偵錯工具以[ICorDebugProcess4：:P rocessstatechanged](icordebugprocess4-processstatechanged-method.md)或[ICorDebugProcess6：:P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)呼叫 `ProcessStateChanged` 方法時，會提供 `CorDebugStateChange` 列舉的成員做為引數。</span><span class="sxs-lookup"><span data-stu-id="e0887-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="e0887-112">需求</span><span class="sxs-lookup"><span data-stu-id="e0887-112">Requirements</span></span>

 <span data-ttu-id="e0887-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0887-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="e0887-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0887-114">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="e0887-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0887-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="e0887-116">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0887-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e0887-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="e0887-117">See also</span></span>

- [<span data-ttu-id="e0887-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="e0887-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="e0887-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="e0887-119">Debugging</span></span>](index.md)
