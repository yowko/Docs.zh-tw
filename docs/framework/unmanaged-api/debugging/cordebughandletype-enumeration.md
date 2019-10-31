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
ms.openlocfilehash: 5a957a042875b546a18a17422f355b712756e91c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098176"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="30998-102">CorDebugHandleType 列舉</span><span class="sxs-lookup"><span data-stu-id="30998-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="30998-103">指出控制代碼類型。</span><span class="sxs-lookup"><span data-stu-id="30998-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30998-104">語法</span><span class="sxs-lookup"><span data-stu-id="30998-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="30998-105">Members</span><span class="sxs-lookup"><span data-stu-id="30998-105">Members</span></span>  
  
|<span data-ttu-id="30998-106">成員</span><span class="sxs-lookup"><span data-stu-id="30998-106">Member</span></span>|<span data-ttu-id="30998-107">描述</span><span class="sxs-lookup"><span data-stu-id="30998-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="30998-108">此控制碼為強式，可防止垃圾收集回收物件。</span><span class="sxs-lookup"><span data-stu-id="30998-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="30998-109">控制碼為弱式，不會防止垃圾收集回收物件。</span><span class="sxs-lookup"><span data-stu-id="30998-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="30998-110">收集物件時，控制碼會變成無效。</span><span class="sxs-lookup"><span data-stu-id="30998-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="30998-111">需求</span><span class="sxs-lookup"><span data-stu-id="30998-111">Requirements</span></span>  
 <span data-ttu-id="30998-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30998-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30998-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30998-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30998-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30998-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30998-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30998-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30998-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="30998-116">See also</span></span>

- [<span data-ttu-id="30998-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="30998-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
