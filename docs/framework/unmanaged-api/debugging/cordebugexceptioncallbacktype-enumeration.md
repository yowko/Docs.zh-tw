---
title: "CorDebugExceptionCallbackType 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionCallbackType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionCallbackType
helpviewer_keywords: CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dfffea1044eb2c1e771fe86e5e9b431eb0ab9696
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="ac813-102">CorDebugExceptionCallbackType 列舉</span><span class="sxs-lookup"><span data-stu-id="ac813-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="ac813-103">表示從進行的回呼類型[icordebugmanagedcallback2:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)事件。</span><span class="sxs-lookup"><span data-stu-id="ac813-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac813-104">語法</span><span class="sxs-lookup"><span data-stu-id="ac813-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="ac813-105">成員</span><span class="sxs-lookup"><span data-stu-id="ac813-105">Members</span></span>  
  
|<span data-ttu-id="ac813-106">成員</span><span class="sxs-lookup"><span data-stu-id="ac813-106">Member</span></span>|<span data-ttu-id="ac813-107">說明</span><span class="sxs-lookup"><span data-stu-id="ac813-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="ac813-108">擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ac813-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="ac813-109">例外狀況結束處理序輸入的使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="ac813-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="ac813-110">例外狀況結束程序發現`catch`中使用者程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="ac813-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="ac813-111">未處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ac813-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac813-112">需求</span><span class="sxs-lookup"><span data-stu-id="ac813-112">Requirements</span></span>  
 <span data-ttu-id="ac813-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ac813-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac813-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac813-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac813-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac813-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac813-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac813-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac813-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac813-117">See Also</span></span>  
 [<span data-ttu-id="ac813-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="ac813-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
