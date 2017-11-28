---
title: "CorDebugCreateProcessFlags 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugCreateProcessFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugCreateProcessFlags
helpviewer_keywords: CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 35503a89077b05d622ccc3f8e5cf1bb7d95ea9e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="80ec6-102">CorDebugCreateProcessFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="80ec6-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="80ec6-103">提供可用的呼叫中的其他偵錯選項[icordebug:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="80ec6-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80ec6-104">語法</span><span class="sxs-lookup"><span data-stu-id="80ec6-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="80ec6-105">成員</span><span class="sxs-lookup"><span data-stu-id="80ec6-105">Members</span></span>  
  
|<span data-ttu-id="80ec6-106">成員</span><span class="sxs-lookup"><span data-stu-id="80ec6-106">Member</span></span>|<span data-ttu-id="80ec6-107">說明</span><span class="sxs-lookup"><span data-stu-id="80ec6-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="80ec6-108">不設定任何特殊選項。</span><span class="sxs-lookup"><span data-stu-id="80ec6-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80ec6-109">需求</span><span class="sxs-lookup"><span data-stu-id="80ec6-109">Requirements</span></span>  
 <span data-ttu-id="80ec6-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="80ec6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80ec6-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80ec6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80ec6-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80ec6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80ec6-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80ec6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ec6-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80ec6-114">See Also</span></span>  
 [<span data-ttu-id="80ec6-115">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="80ec6-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
