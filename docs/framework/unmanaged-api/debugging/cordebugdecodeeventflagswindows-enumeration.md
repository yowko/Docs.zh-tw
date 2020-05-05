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
ms.openlocfilehash: a90ddd27834e7614c1827d606a9955b4d6c53127
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795972"
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a><span data-ttu-id="bd6c2-102">CorDebugDecodeEventFlagsWindows 列舉</span><span class="sxs-lookup"><span data-stu-id="bd6c2-102">CorDebugDecodeEventFlagsWindows Enumeration</span></span>
<span data-ttu-id="bd6c2-103">提供 Windows 平台上之偵錯事件的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-103">Provides additional information about debug events on the Windows platform.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd6c2-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd6c2-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a><span data-ttu-id="bd6c2-105">成員</span><span class="sxs-lookup"><span data-stu-id="bd6c2-105">Members</span></span>  
  
|<span data-ttu-id="bd6c2-106">member</span><span class="sxs-lookup"><span data-stu-id="bd6c2-106">Member</span></span>|<span data-ttu-id="bd6c2-107">說明</span><span class="sxs-lookup"><span data-stu-id="bd6c2-107">Description</span></span>|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|<span data-ttu-id="bd6c2-108">表示偵錯事件是第一個可能發生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-108">Indicates that the debug event is a first-chance exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd6c2-109">備註</span><span class="sxs-lookup"><span data-stu-id="bd6c2-109">Remarks</span></span>  
 <span data-ttu-id="bd6c2-110">[ICorDebugProcess6：:D ecodeevent](icordebugprocess6-decodeevent-method.md)方法包含一個`dwFlags`參數，可提供有關 debug 事件的其他資訊，而且其值會相依于目標架構。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-110">The [ICorDebugProcess6::DecodeEvent](icordebugprocess6-decodeevent-method.md) method includes a `dwFlags` parameter that provides additional information about a debug event and whose value is dependent on the target architecture.</span></span> <span data-ttu-id="bd6c2-111">`CorDebugDecodeEventFlagsWindows` 列舉可搭配 Windows 平台上的偵錯事件使用。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-111">The `CorDebugDecodeEventFlagsWindows` enumeration can be used with debug events on the Windows platform.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd6c2-112">這個列舉僅適用於 .NET Native 偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd6c2-113">需求</span><span class="sxs-lookup"><span data-stu-id="bd6c2-113">Requirements</span></span>  
 <span data-ttu-id="bd6c2-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd6c2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd6c2-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd6c2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd6c2-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd6c2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd6c2-117">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd6c2-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd6c2-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="bd6c2-118">See also</span></span>

- [<span data-ttu-id="bd6c2-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="bd6c2-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
