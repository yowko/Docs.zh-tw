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
ms.openlocfilehash: eab5fc13b74d8af4f0baaa3953c5c73ea255bfe6
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274026"
---
# <a name="cor_pub_enumprocess-enumeration"></a><span data-ttu-id="2fcab-102">COR_PUB_ENUMPROCESS 列舉</span><span class="sxs-lookup"><span data-stu-id="2fcab-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="2fcab-103">識別所要列舉的類型。</span><span class="sxs-lookup"><span data-stu-id="2fcab-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fcab-104">語法</span><span class="sxs-lookup"><span data-stu-id="2fcab-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="2fcab-105">成員</span><span class="sxs-lookup"><span data-stu-id="2fcab-105">Members</span></span>  
  
|<span data-ttu-id="2fcab-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="2fcab-106">Member name</span></span>|<span data-ttu-id="2fcab-107">描述</span><span class="sxs-lookup"><span data-stu-id="2fcab-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="2fcab-108">Managed 進程。</span><span class="sxs-lookup"><span data-stu-id="2fcab-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fcab-109">備註</span><span class="sxs-lookup"><span data-stu-id="2fcab-109">Remarks</span></span>  
 <span data-ttu-id="2fcab-110">目前版本的非受控偵錯工具開發介面只會列舉受管理的進程。</span><span class="sxs-lookup"><span data-stu-id="2fcab-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fcab-111">需求</span><span class="sxs-lookup"><span data-stu-id="2fcab-111">Requirements</span></span>  
 <span data-ttu-id="2fcab-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2fcab-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fcab-113">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="2fcab-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2fcab-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fcab-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fcab-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fcab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fcab-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2fcab-116">See also</span></span>

- [<span data-ttu-id="2fcab-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="2fcab-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
