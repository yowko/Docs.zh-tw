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
ms.openlocfilehash: 15572037940f7c45ec5dcb7e34599756e15fd3bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793903"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="b2778-102">CorDebugHandleType 列舉</span><span class="sxs-lookup"><span data-stu-id="b2778-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="b2778-103">指出控制代碼類型。</span><span class="sxs-lookup"><span data-stu-id="b2778-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2778-104">語法</span><span class="sxs-lookup"><span data-stu-id="b2778-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="b2778-105">Members</span><span class="sxs-lookup"><span data-stu-id="b2778-105">Members</span></span>  
  
|<span data-ttu-id="b2778-106">成員</span><span class="sxs-lookup"><span data-stu-id="b2778-106">Member</span></span>|<span data-ttu-id="b2778-107">描述</span><span class="sxs-lookup"><span data-stu-id="b2778-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="b2778-108">此控制碼為強式，可防止垃圾收集回收物件。</span><span class="sxs-lookup"><span data-stu-id="b2778-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="b2778-109">控制碼為弱式，不會防止垃圾收集回收物件。</span><span class="sxs-lookup"><span data-stu-id="b2778-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="b2778-110">收集物件時，控制碼會變成無效。</span><span class="sxs-lookup"><span data-stu-id="b2778-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2778-111">需求</span><span class="sxs-lookup"><span data-stu-id="b2778-111">Requirements</span></span>  
 <span data-ttu-id="b2778-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b2778-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2778-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2778-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2778-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2778-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2778-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2778-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2778-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="b2778-116">See also</span></span>

- [<span data-ttu-id="b2778-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="b2778-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
