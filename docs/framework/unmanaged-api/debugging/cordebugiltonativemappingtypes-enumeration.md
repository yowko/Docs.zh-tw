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
ms.openlocfilehash: 949d04fe8d9ce492fb320fb4732677ffb35302ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132818"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="6e006-102">CorDebugIlToNativeMappingTypes 列舉</span><span class="sxs-lookup"><span data-stu-id="6e006-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="6e006-103">指出特定範圍的原生指令（由 COR_DEBUG_IL_TO_NATIVE_MAP 結構的實例所代表）是否對應到特殊的程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="6e006-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e006-104">語法</span><span class="sxs-lookup"><span data-stu-id="6e006-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="6e006-105">Members</span><span class="sxs-lookup"><span data-stu-id="6e006-105">Members</span></span>  
  
|<span data-ttu-id="6e006-106">成員</span><span class="sxs-lookup"><span data-stu-id="6e006-106">Member</span></span>|<span data-ttu-id="6e006-107">描述</span><span class="sxs-lookup"><span data-stu-id="6e006-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="6e006-108">原生指令的範圍不會對應到任何特殊的程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="6e006-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="6e006-109">原生指令的範圍會對應至初構。</span><span class="sxs-lookup"><span data-stu-id="6e006-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="6e006-110">原生指令的範圍會對應到終解。</span><span class="sxs-lookup"><span data-stu-id="6e006-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e006-111">需求</span><span class="sxs-lookup"><span data-stu-id="6e006-111">Requirements</span></span>  
 <span data-ttu-id="6e006-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6e006-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e006-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e006-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e006-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e006-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e006-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e006-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e006-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="6e006-116">See also</span></span>

- [<span data-ttu-id="6e006-117">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="6e006-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="6e006-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="6e006-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
