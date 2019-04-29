---
title: CorDebugIlToNativeMappingTypes 列舉
ms.date: 03/30/2017
api_name:
- CorDebugIlToNativeMappingTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIlToNativeMappingTypes
helpviewer_keywords:
- CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f62707fb1e52a96cf3f131e9c11fee82ab03f4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651762"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="5f626-102">CorDebugIlToNativeMappingTypes 列舉</span><span class="sxs-lookup"><span data-stu-id="5f626-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="5f626-103">指出特定範圍的 COR_DEBUG_IL_TO_NATIVE_MAP 結構的執行個體所表示的原生指令是否對應至特殊的程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="5f626-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f626-104">語法</span><span class="sxs-lookup"><span data-stu-id="5f626-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="5f626-105">成員</span><span class="sxs-lookup"><span data-stu-id="5f626-105">Members</span></span>  
  
|<span data-ttu-id="5f626-106">成員</span><span class="sxs-lookup"><span data-stu-id="5f626-106">Member</span></span>|<span data-ttu-id="5f626-107">描述</span><span class="sxs-lookup"><span data-stu-id="5f626-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="5f626-108">原生指令的範圍並未對應到任何特殊的程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="5f626-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="5f626-109">原生指令的範圍對應至初構中。</span><span class="sxs-lookup"><span data-stu-id="5f626-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="5f626-110">原生指令的範圍對應至終解。</span><span class="sxs-lookup"><span data-stu-id="5f626-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5f626-111">需求</span><span class="sxs-lookup"><span data-stu-id="5f626-111">Requirements</span></span>  
 <span data-ttu-id="5f626-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f626-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f626-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f626-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f626-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f626-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f626-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f626-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f626-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f626-116">See also</span></span>

- [<span data-ttu-id="5f626-117">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="5f626-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="5f626-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="5f626-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
