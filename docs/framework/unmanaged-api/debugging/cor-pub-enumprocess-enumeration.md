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
ms.openlocfilehash: bfc576e1b4f0bf1666dcd585a24dbfa398e9abde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715851"
---
# <a name="corpubenumprocess-enumeration"></a><span data-ttu-id="6fcf5-102">COR_PUB_ENUMPROCESS 列舉</span><span class="sxs-lookup"><span data-stu-id="6fcf5-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="6fcf5-103">識別所要列舉的類型。</span><span class="sxs-lookup"><span data-stu-id="6fcf5-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fcf5-104">語法</span><span class="sxs-lookup"><span data-stu-id="6fcf5-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="6fcf5-105">成員</span><span class="sxs-lookup"><span data-stu-id="6fcf5-105">Members</span></span>  
  
|<span data-ttu-id="6fcf5-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="6fcf5-106">Member name</span></span>|<span data-ttu-id="6fcf5-107">描述</span><span class="sxs-lookup"><span data-stu-id="6fcf5-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="6fcf5-108">受管理的程序。</span><span class="sxs-lookup"><span data-stu-id="6fcf5-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fcf5-109">備註</span><span class="sxs-lookup"><span data-stu-id="6fcf5-109">Remarks</span></span>  
 <span data-ttu-id="6fcf5-110">目前版本的 unmanaged 偵錯 API 列舉只受管理的程序。</span><span class="sxs-lookup"><span data-stu-id="6fcf5-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fcf5-111">需求</span><span class="sxs-lookup"><span data-stu-id="6fcf5-111">Requirements</span></span>  
 <span data-ttu-id="6fcf5-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6fcf5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fcf5-113">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="6fcf5-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6fcf5-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fcf5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fcf5-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fcf5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fcf5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fcf5-116">See also</span></span>
- [<span data-ttu-id="6fcf5-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="6fcf5-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
