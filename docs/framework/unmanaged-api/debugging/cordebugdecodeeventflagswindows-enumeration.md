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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec23e0f272852088987fcc74767d3645778eab45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955689"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="56d30-102">CorDebugDecodeEventFlagsWindows 列舉</span><span class="sxs-lookup"><span data-stu-id="56d30-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="56d30-103">提供 Windows 平台上之偵錯事件的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="56d30-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56d30-104">語法</span><span class="sxs-lookup"><span data-stu-id="56d30-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="56d30-105">成員</span><span class="sxs-lookup"><span data-stu-id="56d30-105">Members</span></span>  
  
|<span data-ttu-id="56d30-106">成員</span><span class="sxs-lookup"><span data-stu-id="56d30-106">Member</span></span>|<span data-ttu-id="56d30-107">描述</span><span class="sxs-lookup"><span data-stu-id="56d30-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="56d30-108">表示偵錯事件是第一個可能發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="56d30-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56d30-109">備註</span><span class="sxs-lookup"><span data-stu-id="56d30-109">Remarks</span></span>  
 <span data-ttu-id="56d30-110">[ICorDebugProcess6::D ecodeevent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)方法包含一個`dwFlags`參數, 可提供有關 debug 事件的其他資訊, 而且其值會相依于目標架構。</span><span class="sxs-lookup"><span data-stu-id="56d30-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="56d30-111">`CorDebugDecodeEventFlagsWindows` 列舉可搭配 Windows 平台上的偵錯事件使用。</span><span class="sxs-lookup"><span data-stu-id="56d30-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56d30-112">這個列舉僅適用於 .NET Native 偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="56d30-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56d30-113">需求</span><span class="sxs-lookup"><span data-stu-id="56d30-113">Requirements</span></span>  
 <span data-ttu-id="56d30-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="56d30-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56d30-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56d30-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56d30-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56d30-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56d30-117">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56d30-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d30-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56d30-118">See also</span></span>

- [<span data-ttu-id="56d30-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="56d30-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
