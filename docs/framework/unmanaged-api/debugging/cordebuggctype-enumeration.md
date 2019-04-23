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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 315d6dd522f3c6be2d36b1eb411d9f471350df60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182919"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="f7198-102">CorDebugGCType 列舉</span><span class="sxs-lookup"><span data-stu-id="f7198-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="f7198-103">指出記憶體回收行程是在工作站或伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="f7198-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7198-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7198-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7198-105">參數</span><span class="sxs-lookup"><span data-stu-id="f7198-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="f7198-106">成員</span><span class="sxs-lookup"><span data-stu-id="f7198-106">Members</span></span>  
  
|<span data-ttu-id="f7198-107">成員名稱</span><span class="sxs-lookup"><span data-stu-id="f7198-107">Member name</span></span>|<span data-ttu-id="f7198-108">描述</span><span class="sxs-lookup"><span data-stu-id="f7198-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="f7198-109">記憶體回收行程在工作站上執行。</span><span class="sxs-lookup"><span data-stu-id="f7198-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="f7198-110">記憶體回收行程在伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="f7198-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7198-111">備註</span><span class="sxs-lookup"><span data-stu-id="f7198-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7198-112">需求</span><span class="sxs-lookup"><span data-stu-id="f7198-112">Requirements</span></span>  
 <span data-ttu-id="f7198-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7198-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7198-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7198-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7198-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7198-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7198-116">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7198-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7198-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7198-117">See also</span></span>

- [<span data-ttu-id="f7198-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="f7198-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
