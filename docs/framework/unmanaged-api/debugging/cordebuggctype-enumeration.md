---
title: CorDebugGCType 列舉
ms.date: 03/30/2017
api_name:
- CorDebugGCType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGCType
helpviewer_keywords:
- CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type:
- apiref
ms.openlocfilehash: 6b3075613af0403527ecf67d574c0f5733a5cd8b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712608"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="8ed89-102">CorDebugGCType 列舉</span><span class="sxs-lookup"><span data-stu-id="8ed89-102">CorDebugGCType Enumeration</span></span>

<span data-ttu-id="8ed89-103">指出記憶體回收行程是在工作站或伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="8ed89-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ed89-104">語法</span><span class="sxs-lookup"><span data-stu-id="8ed89-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ed89-105">參數</span><span class="sxs-lookup"><span data-stu-id="8ed89-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="8ed89-106">成員</span><span class="sxs-lookup"><span data-stu-id="8ed89-106">Members</span></span>  
  
|<span data-ttu-id="8ed89-107">成員名稱</span><span class="sxs-lookup"><span data-stu-id="8ed89-107">Member name</span></span>|<span data-ttu-id="8ed89-108">描述</span><span class="sxs-lookup"><span data-stu-id="8ed89-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="8ed89-109">垃圾收集行程正在工作站上執行。</span><span class="sxs-lookup"><span data-stu-id="8ed89-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="8ed89-110">垃圾收集行程正在伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="8ed89-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ed89-111">備註</span><span class="sxs-lookup"><span data-stu-id="8ed89-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ed89-112">需求</span><span class="sxs-lookup"><span data-stu-id="8ed89-112">Requirements</span></span>  

 <span data-ttu-id="8ed89-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8ed89-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ed89-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ed89-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ed89-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ed89-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ed89-116">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ed89-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ed89-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ed89-117">See also</span></span>

- [<span data-ttu-id="8ed89-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="8ed89-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
