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
ms.openlocfilehash: 30a522fbf96aebaa96f33f4a1dc381683f183871
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726414"
---
# <a name="cor_pub_enumprocess-enumeration"></a><span data-ttu-id="cd25e-102">COR_PUB_ENUMPROCESS 列舉</span><span class="sxs-lookup"><span data-stu-id="cd25e-102">COR_PUB_ENUMPROCESS Enumeration</span></span>

<span data-ttu-id="cd25e-103">識別所要列舉的類型。</span><span class="sxs-lookup"><span data-stu-id="cd25e-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd25e-104">語法</span><span class="sxs-lookup"><span data-stu-id="cd25e-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="cd25e-105">成員</span><span class="sxs-lookup"><span data-stu-id="cd25e-105">Members</span></span>  
  
|<span data-ttu-id="cd25e-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="cd25e-106">Member name</span></span>|<span data-ttu-id="cd25e-107">描述</span><span class="sxs-lookup"><span data-stu-id="cd25e-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="cd25e-108">Managed 進程。</span><span class="sxs-lookup"><span data-stu-id="cd25e-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd25e-109">備註</span><span class="sxs-lookup"><span data-stu-id="cd25e-109">Remarks</span></span>  

 <span data-ttu-id="cd25e-110">目前版本的未受管理的偵錯工具 API 只會列舉 managed 進程。</span><span class="sxs-lookup"><span data-stu-id="cd25e-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd25e-111">需求</span><span class="sxs-lookup"><span data-stu-id="cd25e-111">Requirements</span></span>  

 <span data-ttu-id="cd25e-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd25e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd25e-113">**標頭：** CorPub .idl、CorPub。h</span><span class="sxs-lookup"><span data-stu-id="cd25e-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="cd25e-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd25e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd25e-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd25e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd25e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd25e-116">See also</span></span>

- [<span data-ttu-id="cd25e-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="cd25e-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
