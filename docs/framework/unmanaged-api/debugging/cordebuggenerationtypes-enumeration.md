---
title: CorDebugGenerationTypes 列舉
ms.date: 03/30/2017
api_name:
- CorDebugGenerationTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGenerationTypes
helpviewer_keywords:
- CorDebugGenerationTypes enumeration [.NET Framework debugging]
ms.assetid: 9f25b64f-eedd-4ae5-8b0e-cfdfb9b6c5d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 193f5ffe96e89a00bed8a3c88ee346ba3ea9f2b4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740025"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="e9916-102">CorDebugGenerationTypes 列舉</span><span class="sxs-lookup"><span data-stu-id="e9916-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="e9916-103">指定 Managed 堆積上的記憶體區域產生方式。</span><span class="sxs-lookup"><span data-stu-id="e9916-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9916-104">語法</span><span class="sxs-lookup"><span data-stu-id="e9916-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="e9916-105">成員</span><span class="sxs-lookup"><span data-stu-id="e9916-105">Members</span></span>  
  
|<span data-ttu-id="e9916-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="e9916-106">Member name</span></span>|<span data-ttu-id="e9916-107">描述</span><span class="sxs-lookup"><span data-stu-id="e9916-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="e9916-108">層代 0。</span><span class="sxs-lookup"><span data-stu-id="e9916-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="e9916-109">層代 1。</span><span class="sxs-lookup"><span data-stu-id="e9916-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="e9916-110">層代 2。</span><span class="sxs-lookup"><span data-stu-id="e9916-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="e9916-111">大型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="e9916-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9916-112">備註</span><span class="sxs-lookup"><span data-stu-id="e9916-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9916-113">需求</span><span class="sxs-lookup"><span data-stu-id="e9916-113">Requirements</span></span>  
 <span data-ttu-id="e9916-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9916-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9916-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9916-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9916-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9916-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9916-117">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9916-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9916-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9916-118">See also</span></span>

- [<span data-ttu-id="e9916-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="e9916-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
