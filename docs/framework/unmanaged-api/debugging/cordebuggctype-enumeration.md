---
title: CorDebugGCType 列舉
ms.date: 03/30/2017
api_name:
- CorDebugGCType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGCType
helpviewer_keywords:
- CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type:
- apiref
ms.openlocfilehash: 8dd070d2c895a94ac996be81e672bd67f59b83b7
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795894"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="7c37c-102">CorDebugGCType 列舉</span><span class="sxs-lookup"><span data-stu-id="7c37c-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="7c37c-103">指出記憶體回收行程是在工作站或伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="7c37c-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c37c-104">語法</span><span class="sxs-lookup"><span data-stu-id="7c37c-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c37c-105">參數</span><span class="sxs-lookup"><span data-stu-id="7c37c-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="7c37c-106">成員</span><span class="sxs-lookup"><span data-stu-id="7c37c-106">Members</span></span>  
  
|<span data-ttu-id="7c37c-107">成員名稱</span><span class="sxs-lookup"><span data-stu-id="7c37c-107">Member name</span></span>|<span data-ttu-id="7c37c-108">說明</span><span class="sxs-lookup"><span data-stu-id="7c37c-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="7c37c-109">垃圾收集行程正在工作站上執行。</span><span class="sxs-lookup"><span data-stu-id="7c37c-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="7c37c-110">垃圾收集行程正在伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="7c37c-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c37c-111">備註</span><span class="sxs-lookup"><span data-stu-id="7c37c-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c37c-112">需求</span><span class="sxs-lookup"><span data-stu-id="7c37c-112">Requirements</span></span>  
 <span data-ttu-id="7c37c-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7c37c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c37c-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c37c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c37c-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c37c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c37c-116">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c37c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c37c-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="7c37c-117">See also</span></span>

- [<span data-ttu-id="7c37c-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="7c37c-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
