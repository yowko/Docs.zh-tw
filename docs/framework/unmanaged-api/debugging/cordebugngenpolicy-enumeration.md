---
title: "CorDebugNGenPolicy 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugNGenPolicy
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugNGenPolicy
helpviewer_keywords: CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6042d5232995e68a4f59dfa68093446a03badfd6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="3d9af-102">CorDebugNGenPolicy 列舉</span><span class="sxs-lookup"><span data-stu-id="3d9af-102">CorDebugNGenPolicy Enumeration</span></span>
<span data-ttu-id="3d9af-103">提供用來判定偵錯工具是否從原生影像快取載入原生 (NGen) 影像的值。</span><span class="sxs-lookup"><span data-stu-id="3d9af-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d9af-104">語法</span><span class="sxs-lookup"><span data-stu-id="3d9af-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="3d9af-105">成員</span><span class="sxs-lookup"><span data-stu-id="3d9af-105">Members</span></span>  
  
|<span data-ttu-id="3d9af-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="3d9af-106">Member name</span></span>|<span data-ttu-id="3d9af-107">說明</span><span class="sxs-lookup"><span data-stu-id="3d9af-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="3d9af-108">在[!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)]應用程式中，使用影像，從本機原生映像快取已停用。</span><span class="sxs-lookup"><span data-stu-id="3d9af-108">In a [!INCLUDE[win8_appname_long](../../../../includes/win8-appname-long-md.md)] app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="3d9af-109">在傳統型應用程式，這項設定沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="3d9af-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d9af-110">備註</span><span class="sxs-lookup"><span data-stu-id="3d9af-110">Remarks</span></span>  
 <span data-ttu-id="3d9af-111">`CorDebugNGENPolicy`項列舉供[icordebugprocess5:: Enablengenpolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="3d9af-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="3d9af-112">停用映像從本機原生映像快取的使用方法是確保偵錯工具載入偵錯 JIT 編譯的影像，而不是最佳化的原生映像提供一致的偵錯經驗。</span><span class="sxs-lookup"><span data-stu-id="3d9af-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d9af-113">需求</span><span class="sxs-lookup"><span data-stu-id="3d9af-113">Requirements</span></span>  
 <span data-ttu-id="3d9af-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3d9af-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d9af-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d9af-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d9af-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d9af-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d9af-117">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d9af-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d9af-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d9af-118">See Also</span></span>  
 [<span data-ttu-id="3d9af-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="3d9af-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
