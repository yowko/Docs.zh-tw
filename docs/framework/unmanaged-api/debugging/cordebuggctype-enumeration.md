---
title: "CorDebugGCType 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugGCType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugGCType
helpviewer_keywords: CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2045c2edd129c2e4154d24b43d96f6ea8ad64cab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="88273-102">CorDebugGCType 列舉</span><span class="sxs-lookup"><span data-stu-id="88273-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="88273-103">指出記憶體回收行程是在工作站或伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="88273-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88273-104">語法</span><span class="sxs-lookup"><span data-stu-id="88273-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88273-105">參數</span><span class="sxs-lookup"><span data-stu-id="88273-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="88273-106">成員</span><span class="sxs-lookup"><span data-stu-id="88273-106">Members</span></span>  
  
|<span data-ttu-id="88273-107">成員名稱</span><span class="sxs-lookup"><span data-stu-id="88273-107">Member name</span></span>|<span data-ttu-id="88273-108">描述</span><span class="sxs-lookup"><span data-stu-id="88273-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="88273-109">在工作站上執行記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="88273-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="88273-110">記憶體回收行程在伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="88273-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88273-111">備註</span><span class="sxs-lookup"><span data-stu-id="88273-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88273-112">需求</span><span class="sxs-lookup"><span data-stu-id="88273-112">Requirements</span></span>  
 <span data-ttu-id="88273-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="88273-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88273-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88273-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88273-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88273-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88273-116">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88273-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88273-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="88273-117">See Also</span></span>  
 [<span data-ttu-id="88273-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="88273-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
