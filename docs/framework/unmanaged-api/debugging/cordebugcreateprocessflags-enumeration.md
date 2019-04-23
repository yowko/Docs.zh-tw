---
title: CorDebugCreateProcessFlags 列舉
ms.date: 03/30/2017
api_name:
- CorDebugCreateProcessFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugCreateProcessFlags
helpviewer_keywords:
- CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae3ba480e208762f5a80f9f1b78dd008f02b6df4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089371"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="6af5d-102">CorDebugCreateProcessFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="6af5d-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="6af5d-103">提供可用的呼叫中的其他偵錯選項[icordebug:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="6af5d-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6af5d-104">語法</span><span class="sxs-lookup"><span data-stu-id="6af5d-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="6af5d-105">成員</span><span class="sxs-lookup"><span data-stu-id="6af5d-105">Members</span></span>  
  
|<span data-ttu-id="6af5d-106">成員</span><span class="sxs-lookup"><span data-stu-id="6af5d-106">Member</span></span>|<span data-ttu-id="6af5d-107">描述</span><span class="sxs-lookup"><span data-stu-id="6af5d-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="6af5d-108">不為任何特殊選項。</span><span class="sxs-lookup"><span data-stu-id="6af5d-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6af5d-109">需求</span><span class="sxs-lookup"><span data-stu-id="6af5d-109">Requirements</span></span>  
 <span data-ttu-id="6af5d-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6af5d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6af5d-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6af5d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6af5d-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6af5d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6af5d-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6af5d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af5d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6af5d-114">See also</span></span>

- [<span data-ttu-id="6af5d-115">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="6af5d-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
