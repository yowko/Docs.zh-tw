---
title: "CorDebugIlToNativeMappingTypes 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugIlToNativeMappingTypes
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugIlToNativeMappingTypes
helpviewer_keywords: CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03046ebb678df64ad3d151aaadba313645417979
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="10908-102">CorDebugIlToNativeMappingTypes 列舉</span><span class="sxs-lookup"><span data-stu-id="10908-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="10908-103">指出特定範圍的 COR_DEBUG_IL_TO_NATIVE_MAP 結構的執行個體所代表的原生指令是否對應於特殊程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="10908-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10908-104">語法</span><span class="sxs-lookup"><span data-stu-id="10908-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="10908-105">成員</span><span class="sxs-lookup"><span data-stu-id="10908-105">Members</span></span>  
  
|<span data-ttu-id="10908-106">成員</span><span class="sxs-lookup"><span data-stu-id="10908-106">Member</span></span>|<span data-ttu-id="10908-107">說明</span><span class="sxs-lookup"><span data-stu-id="10908-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="10908-108">原生指令的範圍不是對應至任何特殊的程式碼區域。</span><span class="sxs-lookup"><span data-stu-id="10908-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="10908-109">原生指令的範圍會對應至初構。</span><span class="sxs-lookup"><span data-stu-id="10908-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="10908-110">原生指令的範圍會對應至終解。</span><span class="sxs-lookup"><span data-stu-id="10908-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10908-111">需求</span><span class="sxs-lookup"><span data-stu-id="10908-111">Requirements</span></span>  
 <span data-ttu-id="10908-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10908-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10908-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10908-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10908-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10908-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10908-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10908-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10908-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10908-116">See Also</span></span>  
 [<span data-ttu-id="10908-117">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="10908-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)  
 [<span data-ttu-id="10908-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="10908-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
