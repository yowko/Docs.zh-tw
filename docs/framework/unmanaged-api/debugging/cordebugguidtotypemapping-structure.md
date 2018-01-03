---
title: "CorDebugGuidToTypeMapping 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugGuidToTypeMapping
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugGuidToTypeMapping
helpviewer_keywords: CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecdadc96c0fb850fef13ba978fc97eef91dadd65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="9f21d-102">CorDebugGuidToTypeMapping 結構</span><span class="sxs-lookup"><span data-stu-id="9f21d-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="9f21d-103">對應[!INCLUDE[wrt](../../../../includes/wrt-md.md)]對應 ICorDebugType 物件的 GUID。</span><span class="sxs-lookup"><span data-stu-id="9f21d-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f21d-104">語法</span><span class="sxs-lookup"><span data-stu-id="9f21d-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="9f21d-105">成員</span><span class="sxs-lookup"><span data-stu-id="9f21d-105">Members</span></span>  
  
|<span data-ttu-id="9f21d-106">成員</span><span class="sxs-lookup"><span data-stu-id="9f21d-106">Member</span></span>|<span data-ttu-id="9f21d-107">描述</span><span class="sxs-lookup"><span data-stu-id="9f21d-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="9f21d-108">GUID 的快取[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型別。</span><span class="sxs-lookup"><span data-stu-id="9f21d-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="9f21d-109">ICorDebugType 物件，提供有關快取的類型指標。</span><span class="sxs-lookup"><span data-stu-id="9f21d-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9f21d-110">需求</span><span class="sxs-lookup"><span data-stu-id="9f21d-110">Requirements</span></span>  
 <span data-ttu-id="9f21d-111">**平台：** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9f21d-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="9f21d-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f21d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f21d-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f21d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f21d-114">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f21d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f21d-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="9f21d-115">See Also</span></span>  
 [<span data-ttu-id="9f21d-116">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="9f21d-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="9f21d-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="9f21d-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
