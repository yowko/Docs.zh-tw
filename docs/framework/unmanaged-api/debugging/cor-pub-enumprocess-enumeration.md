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
ms.openlocfilehash: fcdb5883e109d7e0c73c8fb76ee61b52cf23091f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406997"
---
# <a name="corpubenumprocess-enumeration"></a><span data-ttu-id="ace7f-102">COR_PUB_ENUMPROCESS 列舉</span><span class="sxs-lookup"><span data-stu-id="ace7f-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="ace7f-103">識別所要列舉的類型。</span><span class="sxs-lookup"><span data-stu-id="ace7f-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ace7f-104">語法</span><span class="sxs-lookup"><span data-stu-id="ace7f-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="ace7f-105">成員</span><span class="sxs-lookup"><span data-stu-id="ace7f-105">Members</span></span>  
  
|<span data-ttu-id="ace7f-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="ace7f-106">Member name</span></span>|<span data-ttu-id="ace7f-107">描述</span><span class="sxs-lookup"><span data-stu-id="ace7f-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="ace7f-108">受管理的程序。</span><span class="sxs-lookup"><span data-stu-id="ace7f-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ace7f-109">備註</span><span class="sxs-lookup"><span data-stu-id="ace7f-109">Remarks</span></span>  
 <span data-ttu-id="ace7f-110">目前版本的 unmanaged 偵錯 API 列舉只受管理的處理程序。</span><span class="sxs-lookup"><span data-stu-id="ace7f-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ace7f-111">需求</span><span class="sxs-lookup"><span data-stu-id="ace7f-111">Requirements</span></span>  
 <span data-ttu-id="ace7f-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ace7f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ace7f-113">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="ace7f-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ace7f-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ace7f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ace7f-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ace7f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ace7f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ace7f-116">See Also</span></span>  
 [<span data-ttu-id="ace7f-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="ace7f-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
