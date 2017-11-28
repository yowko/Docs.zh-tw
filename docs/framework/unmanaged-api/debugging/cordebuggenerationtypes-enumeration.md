---
title: "CorDebugGenerationTypes 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugGenerationTypes
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugGenerationTypes
helpviewer_keywords: CorDebugGenerationTypes enumeration [.NET Framework debugging]
ms.assetid: 9f25b64f-eedd-4ae5-8b0e-cfdfb9b6c5d8
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: adefc0de4ba09419660c214df75365c90ec2c66e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="bb487-102">CorDebugGenerationTypes 列舉</span><span class="sxs-lookup"><span data-stu-id="bb487-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="bb487-103">指定 Managed 堆積上的記憶體區域產生方式。</span><span class="sxs-lookup"><span data-stu-id="bb487-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb487-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb487-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="bb487-105">成員</span><span class="sxs-lookup"><span data-stu-id="bb487-105">Members</span></span>  
  
|<span data-ttu-id="bb487-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="bb487-106">Member name</span></span>|<span data-ttu-id="bb487-107">說明</span><span class="sxs-lookup"><span data-stu-id="bb487-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="bb487-108">層代 0。</span><span class="sxs-lookup"><span data-stu-id="bb487-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="bb487-109">層代 1。</span><span class="sxs-lookup"><span data-stu-id="bb487-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="bb487-110">層代 2。</span><span class="sxs-lookup"><span data-stu-id="bb487-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="bb487-111">大型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="bb487-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb487-112">備註</span><span class="sxs-lookup"><span data-stu-id="bb487-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb487-113">需求</span><span class="sxs-lookup"><span data-stu-id="bb487-113">Requirements</span></span>  
 <span data-ttu-id="bb487-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb487-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb487-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb487-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb487-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb487-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb487-117">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb487-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb487-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb487-118">See Also</span></span>  
 [<span data-ttu-id="bb487-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="bb487-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
