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
ms.openlocfilehash: e4c829f4a74c3d2e84a070dfbe5d35d89b1b7ae6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="8d01b-102">CorDebugGuidToTypeMapping 結構</span><span class="sxs-lookup"><span data-stu-id="8d01b-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="8d01b-103">對應[!INCLUDE[wrt](../../../../includes/wrt-md.md)]對應 ICorDebugType 物件的 GUID。</span><span class="sxs-lookup"><span data-stu-id="8d01b-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d01b-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d01b-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="8d01b-105">成員</span><span class="sxs-lookup"><span data-stu-id="8d01b-105">Members</span></span>  
  
|<span data-ttu-id="8d01b-106">成員</span><span class="sxs-lookup"><span data-stu-id="8d01b-106">Member</span></span>|<span data-ttu-id="8d01b-107">說明</span><span class="sxs-lookup"><span data-stu-id="8d01b-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="8d01b-108">GUID 的快取[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型別。</span><span class="sxs-lookup"><span data-stu-id="8d01b-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="8d01b-109">ICorDebugType 物件，提供有關快取的類型指標。</span><span class="sxs-lookup"><span data-stu-id="8d01b-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d01b-110">需求</span><span class="sxs-lookup"><span data-stu-id="8d01b-110">Requirements</span></span>  
 <span data-ttu-id="8d01b-111">**平台：** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8d01b-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="8d01b-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d01b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d01b-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d01b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d01b-114">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d01b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d01b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d01b-115">See Also</span></span>  
 [<span data-ttu-id="8d01b-116">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="8d01b-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="8d01b-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="8d01b-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
