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
ms.openlocfilehash: ddb5af486ab6fb1c8c4fabf3ccf7b43d037e1eeb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789325"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="7043d-102">CorDebugIlToNativeMappingTypes 列舉</span><span class="sxs-lookup"><span data-stu-id="7043d-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="7043d-103">指出特定的原生指令範圍（由 COR_DEBUG_IL_TO_NATIVE_MAP 結構的實例所表示）是否對應到特殊的程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="7043d-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7043d-104">語法</span><span class="sxs-lookup"><span data-stu-id="7043d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="7043d-105">Members</span><span class="sxs-lookup"><span data-stu-id="7043d-105">Members</span></span>  
  
|<span data-ttu-id="7043d-106">成員</span><span class="sxs-lookup"><span data-stu-id="7043d-106">Member</span></span>|<span data-ttu-id="7043d-107">描述</span><span class="sxs-lookup"><span data-stu-id="7043d-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="7043d-108">原生指令的範圍不會對應到任何特殊的程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="7043d-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="7043d-109">原生指令的範圍會對應至初構。</span><span class="sxs-lookup"><span data-stu-id="7043d-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="7043d-110">原生指令的範圍會對應到終解。</span><span class="sxs-lookup"><span data-stu-id="7043d-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7043d-111">需求</span><span class="sxs-lookup"><span data-stu-id="7043d-111">Requirements</span></span>  
 <span data-ttu-id="7043d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7043d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7043d-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7043d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7043d-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7043d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7043d-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7043d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7043d-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="7043d-116">See also</span></span>

- [<span data-ttu-id="7043d-117">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="7043d-117">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="7043d-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="7043d-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
