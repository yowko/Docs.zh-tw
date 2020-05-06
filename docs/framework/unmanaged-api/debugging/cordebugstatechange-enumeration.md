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
ms.openlocfilehash: d94422d25da91cd2a6653a95cbd852c3930a151a
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795686"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="bc639-102">CorDebugStateChange 列舉</span><span class="sxs-lookup"><span data-stu-id="bc639-102">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="bc639-103">描述依據處理序變更而必須捨棄的快取資料量。</span><span class="sxs-lookup"><span data-stu-id="bc639-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="bc639-104">語法</span><span class="sxs-lookup"><span data-stu-id="bc639-104">Syntax</span></span>

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="bc639-105">成員</span><span class="sxs-lookup"><span data-stu-id="bc639-105">Members</span></span>

| <span data-ttu-id="bc639-106">member</span><span class="sxs-lookup"><span data-stu-id="bc639-106">Member</span></span>            | <span data-ttu-id="bc639-107">說明</span><span class="sxs-lookup"><span data-stu-id="bc639-107">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="bc639-108">處理序透過向前執行已達到新的記憶體狀態。</span><span class="sxs-lookup"><span data-stu-id="bc639-108">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="bc639-109">指定的處理序記憶體可能與先前的記憶體不同。</span><span class="sxs-lookup"><span data-stu-id="bc639-109">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="bc639-110">備註</span><span class="sxs-lookup"><span data-stu-id="bc639-110">Remarks</span></span>

 <span data-ttu-id="bc639-111">當偵錯工具以`CorDebugStateChange` `ProcessStateChanged` [ICorDebugProcess4：:P rocessStateChanged](icordebugprocess4-processstatechanged-method.md)或[ICorDebugProcess6：:P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)呼叫方法時，會將列舉的成員當做引數提供。</span><span class="sxs-lookup"><span data-stu-id="bc639-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="bc639-112">需求</span><span class="sxs-lookup"><span data-stu-id="bc639-112">Requirements</span></span>

 <span data-ttu-id="bc639-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc639-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="bc639-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc639-114">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="bc639-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc639-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="bc639-116">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc639-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bc639-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="bc639-117">See also</span></span>

- [<span data-ttu-id="bc639-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="bc639-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="bc639-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="bc639-119">Debugging</span></span>](index.md)
