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
ms.openlocfilehash: 2d4e006a03db5b16de93dfd07ec7b964db4bfc1d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207730"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="8e2fe-102">CorDebugDecodeEventFlagsWindows 列舉</span><span class="sxs-lookup"><span data-stu-id="8e2fe-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="8e2fe-103">提供 Windows 平台上之偵錯事件的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="8e2fe-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e2fe-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e2fe-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="8e2fe-105">成員</span><span class="sxs-lookup"><span data-stu-id="8e2fe-105">Members</span></span>  
  
|<span data-ttu-id="8e2fe-106">成員</span><span class="sxs-lookup"><span data-stu-id="8e2fe-106">Member</span></span>|<span data-ttu-id="8e2fe-107">描述</span><span class="sxs-lookup"><span data-stu-id="8e2fe-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="8e2fe-108">表示偵錯事件是第一個可能發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8e2fe-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e2fe-109">備註</span><span class="sxs-lookup"><span data-stu-id="8e2fe-109">Remarks</span></span>  
 <span data-ttu-id="8e2fe-110">[ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)方法包含`dwFlags`參數提供偵錯事件的其他資訊，而其值為相依於目標架構。</span><span class="sxs-lookup"><span data-stu-id="8e2fe-110">The [ICorDebugProcess6::DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="8e2fe-111">`CorDebugDecodeEventFlagsWindows` 列舉可搭配 Windows 平台上的偵錯事件使用。</span><span class="sxs-lookup"><span data-stu-id="8e2fe-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e2fe-112">這個列舉僅適用於 .NET Native 偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="8e2fe-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e2fe-113">需求</span><span class="sxs-lookup"><span data-stu-id="8e2fe-113">Requirements</span></span>  
 <span data-ttu-id="8e2fe-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e2fe-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e2fe-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e2fe-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e2fe-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e2fe-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8e2fe-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="8e2fe-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8e2fe-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e2fe-118">See also</span></span>

- [<span data-ttu-id="8e2fe-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="8e2fe-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
