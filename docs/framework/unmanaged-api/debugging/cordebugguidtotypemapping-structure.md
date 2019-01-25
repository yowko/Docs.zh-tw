---
title: CorDebugGuidToTypeMapping 結構
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugGuidToTypeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGuidToTypeMapping
helpviewer_keywords:
- CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49290a37ca7ea101e3c8b458a5daa4995cb3beee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610041"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="3a899-102">CorDebugGuidToTypeMapping 結構</span><span class="sxs-lookup"><span data-stu-id="3a899-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="3a899-103">對應[!INCLUDE[wrt](../../../../includes/wrt-md.md)]及其對應的 ICorDebugType 物件的 GUID。</span><span class="sxs-lookup"><span data-stu-id="3a899-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a899-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a899-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="3a899-105">成員</span><span class="sxs-lookup"><span data-stu-id="3a899-105">Members</span></span>  
  
|<span data-ttu-id="3a899-106">成員</span><span class="sxs-lookup"><span data-stu-id="3a899-106">Member</span></span>|<span data-ttu-id="3a899-107">描述</span><span class="sxs-lookup"><span data-stu-id="3a899-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="3a899-108">快取的 GUID[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型別。</span><span class="sxs-lookup"><span data-stu-id="3a899-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="3a899-109">提供有關快取的類型資訊 ICorDebugType 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="3a899-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a899-110">需求</span><span class="sxs-lookup"><span data-stu-id="3a899-110">Requirements</span></span>  
 <span data-ttu-id="3a899-111">**平台：** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3a899-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="3a899-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a899-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a899-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a899-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a899-114">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a899-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a899-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a899-115">See also</span></span>
- [<span data-ttu-id="3a899-116">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="3a899-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="3a899-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="3a899-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
