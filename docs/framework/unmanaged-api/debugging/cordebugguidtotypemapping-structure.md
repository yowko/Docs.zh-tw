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
ms.openlocfilehash: c803a805da605bd52fd50eb1e292c0e277143d7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405255"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="7cefa-102">CorDebugGuidToTypeMapping 結構</span><span class="sxs-lookup"><span data-stu-id="7cefa-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="7cefa-103">對應[!INCLUDE[wrt](../../../../includes/wrt-md.md)]對應 ICorDebugType 物件的 GUID。</span><span class="sxs-lookup"><span data-stu-id="7cefa-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cefa-104">語法</span><span class="sxs-lookup"><span data-stu-id="7cefa-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="7cefa-105">成員</span><span class="sxs-lookup"><span data-stu-id="7cefa-105">Members</span></span>  
  
|<span data-ttu-id="7cefa-106">成員</span><span class="sxs-lookup"><span data-stu-id="7cefa-106">Member</span></span>|<span data-ttu-id="7cefa-107">描述</span><span class="sxs-lookup"><span data-stu-id="7cefa-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="7cefa-108">GUID 的快取[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型別。</span><span class="sxs-lookup"><span data-stu-id="7cefa-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="7cefa-109">ICorDebugType 物件，提供有關快取的類型指標。</span><span class="sxs-lookup"><span data-stu-id="7cefa-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7cefa-110">需求</span><span class="sxs-lookup"><span data-stu-id="7cefa-110">Requirements</span></span>  
 <span data-ttu-id="7cefa-111">**平台：** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7cefa-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="7cefa-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7cefa-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cefa-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cefa-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cefa-114">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cefa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cefa-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cefa-115">See Also</span></span>  
 [<span data-ttu-id="7cefa-116">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="7cefa-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="7cefa-117">偵錯</span><span class="sxs-lookup"><span data-stu-id="7cefa-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
