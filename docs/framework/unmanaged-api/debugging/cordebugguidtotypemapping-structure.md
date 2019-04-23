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
ms.openlocfilehash: 9dc7093edaf12e801a1e1adc52b0be823ff92b91
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079912"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="fc42c-102">CorDebugGuidToTypeMapping 結構</span><span class="sxs-lookup"><span data-stu-id="fc42c-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="fc42c-103">對應[!INCLUDE[wrt](../../../../includes/wrt-md.md)]及其對應的 ICorDebugType 物件的 GUID。</span><span class="sxs-lookup"><span data-stu-id="fc42c-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc42c-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc42c-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="fc42c-105">成員</span><span class="sxs-lookup"><span data-stu-id="fc42c-105">Members</span></span>  
  
|<span data-ttu-id="fc42c-106">成員</span><span class="sxs-lookup"><span data-stu-id="fc42c-106">Member</span></span>|<span data-ttu-id="fc42c-107">描述</span><span class="sxs-lookup"><span data-stu-id="fc42c-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="fc42c-108">快取的 GUID[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型別。</span><span class="sxs-lookup"><span data-stu-id="fc42c-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="fc42c-109">提供有關快取的類型資訊 ICorDebugType 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="fc42c-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc42c-110">需求</span><span class="sxs-lookup"><span data-stu-id="fc42c-110">Requirements</span></span>  
 <span data-ttu-id="fc42c-111">**平台：** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="fc42c-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="fc42c-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc42c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc42c-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc42c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc42c-114">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc42c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc42c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc42c-115">See also</span></span>

- [<span data-ttu-id="fc42c-116">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="fc42c-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="fc42c-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="fc42c-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
