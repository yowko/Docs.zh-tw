---
title: COR_PUB_ENUMPROCESS 列舉
ms.date: 03/30/2017
api_name:
- COR_PUB_ENUMPROCESS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_PUB_ENUMPROCESS
helpviewer_keywords:
- COR_PUB_ENUMPROCESS enumeration [.NET Framework debugging]
ms.assetid: 5d3ada6e-feea-47da-a7ed-b664107c137f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 412e2bb7da7b5b3396342df169d56d2724ddb466
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740557"
---
# <a name="corpubenumprocess-enumeration"></a><span data-ttu-id="9608d-102">COR_PUB_ENUMPROCESS 列舉</span><span class="sxs-lookup"><span data-stu-id="9608d-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="9608d-103">識別所要列舉的類型。</span><span class="sxs-lookup"><span data-stu-id="9608d-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9608d-104">語法</span><span class="sxs-lookup"><span data-stu-id="9608d-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="9608d-105">成員</span><span class="sxs-lookup"><span data-stu-id="9608d-105">Members</span></span>  
  
|<span data-ttu-id="9608d-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="9608d-106">Member name</span></span>|<span data-ttu-id="9608d-107">描述</span><span class="sxs-lookup"><span data-stu-id="9608d-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="9608d-108">受管理的程序。</span><span class="sxs-lookup"><span data-stu-id="9608d-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9608d-109">備註</span><span class="sxs-lookup"><span data-stu-id="9608d-109">Remarks</span></span>  
 <span data-ttu-id="9608d-110">目前版本的 unmanaged 偵錯 API 列舉只受管理的程序。</span><span class="sxs-lookup"><span data-stu-id="9608d-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9608d-111">需求</span><span class="sxs-lookup"><span data-stu-id="9608d-111">Requirements</span></span>  
 <span data-ttu-id="9608d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9608d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9608d-113">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="9608d-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9608d-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9608d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9608d-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9608d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9608d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9608d-116">See also</span></span>

- [<span data-ttu-id="9608d-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="9608d-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
