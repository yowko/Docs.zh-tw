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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651791"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="b4419-102">CorDebugGuidToTypeMapping 結構</span><span class="sxs-lookup"><span data-stu-id="b4419-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="b4419-103">對應[!INCLUDE[wrt](../../../../includes/wrt-md.md)]及其對應的 ICorDebugType 物件的 GUID。</span><span class="sxs-lookup"><span data-stu-id="b4419-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4419-104">語法</span><span class="sxs-lookup"><span data-stu-id="b4419-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="b4419-105">成員</span><span class="sxs-lookup"><span data-stu-id="b4419-105">Members</span></span>  
  
|<span data-ttu-id="b4419-106">成員</span><span class="sxs-lookup"><span data-stu-id="b4419-106">Member</span></span>|<span data-ttu-id="b4419-107">描述</span><span class="sxs-lookup"><span data-stu-id="b4419-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="b4419-108">快取的 GUID[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型別。</span><span class="sxs-lookup"><span data-stu-id="b4419-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="b4419-109">提供有關快取的類型資訊 ICorDebugType 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="b4419-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b4419-110">需求</span><span class="sxs-lookup"><span data-stu-id="b4419-110">Requirements</span></span>  
 <span data-ttu-id="b4419-111">**平台：** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b4419-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="b4419-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4419-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4419-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4419-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4419-114">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4419-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4419-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4419-115">See also</span></span>

- [<span data-ttu-id="b4419-116">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="b4419-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="b4419-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="b4419-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
