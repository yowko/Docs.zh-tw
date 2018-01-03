---
title: "CorDebugHandleType 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugHandleType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugHandleType
helpviewer_keywords: CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 408c66bd33ba12b2c674dd6c4a049acfb8c4c986
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="f2bc9-102">CorDebugHandleType 列舉</span><span class="sxs-lookup"><span data-stu-id="f2bc9-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="f2bc9-103">指出控制代碼類型。</span><span class="sxs-lookup"><span data-stu-id="f2bc9-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2bc9-104">語法</span><span class="sxs-lookup"><span data-stu-id="f2bc9-104">Syntax</span></span>  
  
```  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="f2bc9-105">成員</span><span class="sxs-lookup"><span data-stu-id="f2bc9-105">Members</span></span>  
  
|<span data-ttu-id="f2bc9-106">成員</span><span class="sxs-lookup"><span data-stu-id="f2bc9-106">Member</span></span>|<span data-ttu-id="f2bc9-107">描述</span><span class="sxs-lookup"><span data-stu-id="f2bc9-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="f2bc9-108">控制代碼為強式，它可防止物件被記憶體回收所回收。</span><span class="sxs-lookup"><span data-stu-id="f2bc9-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="f2bc9-109">控制代碼很弱，這不會防止物件被記憶體回收所回收。</span><span class="sxs-lookup"><span data-stu-id="f2bc9-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="f2bc9-110">收集物件時，控制代碼會變成無效。</span><span class="sxs-lookup"><span data-stu-id="f2bc9-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f2bc9-111">需求</span><span class="sxs-lookup"><span data-stu-id="f2bc9-111">Requirements</span></span>  
 <span data-ttu-id="f2bc9-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2bc9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2bc9-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2bc9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2bc9-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2bc9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2bc9-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2bc9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2bc9-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="f2bc9-116">See Also</span></span>  
 [<span data-ttu-id="f2bc9-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="f2bc9-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
