---
title: CorDebugNGenPolicy 列舉
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca922d8b582c0608073d4fd0ba986167ae470e34
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599493"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="d14f3-102">CorDebugNGenPolicy 列舉</span><span class="sxs-lookup"><span data-stu-id="d14f3-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="d14f3-103">提供用來判定偵錯工具是否從原生影像快取載入原生 (NGen) 影像的值。</span><span class="sxs-lookup"><span data-stu-id="d14f3-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d14f3-104">語法</span><span class="sxs-lookup"><span data-stu-id="d14f3-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="d14f3-105">成員</span><span class="sxs-lookup"><span data-stu-id="d14f3-105">Members</span></span>  
  
|<span data-ttu-id="d14f3-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="d14f3-106">Member name</span></span>|<span data-ttu-id="d14f3-107">描述</span><span class="sxs-lookup"><span data-stu-id="d14f3-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="d14f3-108">在 [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)]已停用應用程式，從本機原生映像快取的影像之使用。</span><span class="sxs-lookup"><span data-stu-id="d14f3-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="d14f3-109">在桌面應用程式中，這項設定沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="d14f3-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d14f3-110">備註</span><span class="sxs-lookup"><span data-stu-id="d14f3-110">Remarks</span></span>  
 <span data-ttu-id="d14f3-111">`CorDebugNGENPolicy`列舉由[ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d14f3-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="d14f3-112">停用的本機原生映像快取中的映像使用一致的偵錯經驗可確保提供偵錯工具會載入可偵錯的 JIT 編譯映像，而不是最佳化的原生映像。</span><span class="sxs-lookup"><span data-stu-id="d14f3-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d14f3-113">需求</span><span class="sxs-lookup"><span data-stu-id="d14f3-113">Requirements</span></span>  
 <span data-ttu-id="d14f3-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d14f3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d14f3-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d14f3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d14f3-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d14f3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d14f3-117">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d14f3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d14f3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d14f3-118">See also</span></span>

- [<span data-ttu-id="d14f3-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="d14f3-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
