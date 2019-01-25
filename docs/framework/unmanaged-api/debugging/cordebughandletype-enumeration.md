---
title: CorDebugHandleType 列舉
ms.date: 03/30/2017
api_name:
- CorDebugHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugHandleType
helpviewer_keywords:
- CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ca7508c675ccc4c4ee0c07a2d7790bb5de7a668
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594586"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="089e5-102">CorDebugHandleType 列舉</span><span class="sxs-lookup"><span data-stu-id="089e5-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="089e5-103">指出控制代碼類型。</span><span class="sxs-lookup"><span data-stu-id="089e5-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="089e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="089e5-104">Syntax</span></span>  
  
```  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="089e5-105">成員</span><span class="sxs-lookup"><span data-stu-id="089e5-105">Members</span></span>  
  
|<span data-ttu-id="089e5-106">成員</span><span class="sxs-lookup"><span data-stu-id="089e5-106">Member</span></span>|<span data-ttu-id="089e5-107">描述</span><span class="sxs-lookup"><span data-stu-id="089e5-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="089e5-108">控制代碼為強式，這可防止物件被記憶體回收所回收。</span><span class="sxs-lookup"><span data-stu-id="089e5-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="089e5-109">控制代碼是弱式，這不會防止物件被記憶體回收所回收。</span><span class="sxs-lookup"><span data-stu-id="089e5-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="089e5-110">回收物件，此控制代碼就會變成無效。</span><span class="sxs-lookup"><span data-stu-id="089e5-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="089e5-111">需求</span><span class="sxs-lookup"><span data-stu-id="089e5-111">Requirements</span></span>  
 <span data-ttu-id="089e5-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="089e5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="089e5-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="089e5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="089e5-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="089e5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="089e5-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="089e5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="089e5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="089e5-116">See also</span></span>
- [<span data-ttu-id="089e5-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="089e5-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
