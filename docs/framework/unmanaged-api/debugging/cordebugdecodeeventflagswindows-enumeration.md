---
title: CorDebugDecodeEventFlagsWindows 列舉
ms.date: 03/30/2017
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
ms.openlocfilehash: da3a100bd552eaa3233642b006e0265adbcac1ca
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132219"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="85f5a-102">CorDebugDecodeEventFlagsWindows 列舉</span><span class="sxs-lookup"><span data-stu-id="85f5a-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="85f5a-103">提供 Windows 平台上之偵錯事件的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="85f5a-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85f5a-104">語法</span><span class="sxs-lookup"><span data-stu-id="85f5a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="85f5a-105">Members</span><span class="sxs-lookup"><span data-stu-id="85f5a-105">Members</span></span>  
  
|<span data-ttu-id="85f5a-106">成員</span><span class="sxs-lookup"><span data-stu-id="85f5a-106">Member</span></span>|<span data-ttu-id="85f5a-107">描述</span><span class="sxs-lookup"><span data-stu-id="85f5a-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="85f5a-108">表示偵錯事件是第一個可能發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="85f5a-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85f5a-109">備註</span><span class="sxs-lookup"><span data-stu-id="85f5a-109">Remarks</span></span>  
 <span data-ttu-id="85f5a-110">[ICorDebugProcess6：:D ecodeevent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)方法包含一個 `dwFlags` 參數，它會提供有關 debug 事件的其他資訊，以及其值相依于目標架構的資料。</span><span class="sxs-lookup"><span data-stu-id="85f5a-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="85f5a-111">`CorDebugDecodeEventFlagsWindows` 列舉可搭配 Windows 平台上的偵錯事件使用。</span><span class="sxs-lookup"><span data-stu-id="85f5a-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85f5a-112">這個列舉僅適用於 .NET Native 偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="85f5a-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85f5a-113">需求</span><span class="sxs-lookup"><span data-stu-id="85f5a-113">Requirements</span></span>  
 <span data-ttu-id="85f5a-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="85f5a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85f5a-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85f5a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85f5a-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85f5a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85f5a-117">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85f5a-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85f5a-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="85f5a-118">See also</span></span>

- [<span data-ttu-id="85f5a-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="85f5a-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
