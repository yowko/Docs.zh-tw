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
ms.openlocfilehash: f789105751ae2d498740ab60f326f9c0597483b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099204"
---
# <a name="cor_pub_enumprocess-enumeration"></a><span data-ttu-id="08429-102">COR_PUB_ENUMPROCESS 列舉</span><span class="sxs-lookup"><span data-stu-id="08429-102">COR_PUB_ENUMPROCESS Enumeration</span></span>
<span data-ttu-id="08429-103">識別所要列舉的類型。</span><span class="sxs-lookup"><span data-stu-id="08429-103">Identifies the type of process to be enumerated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08429-104">語法</span><span class="sxs-lookup"><span data-stu-id="08429-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PUB_MANAGEDONLY    = 0x00000001  
} COR_PUB_ENUMPROCESS;  
```  
  
## <a name="members"></a><span data-ttu-id="08429-105">Members</span><span class="sxs-lookup"><span data-stu-id="08429-105">Members</span></span>  
  
|<span data-ttu-id="08429-106">成員名稱</span><span class="sxs-lookup"><span data-stu-id="08429-106">Member name</span></span>|<span data-ttu-id="08429-107">描述</span><span class="sxs-lookup"><span data-stu-id="08429-107">Description</span></span>|  
|-----------------|-----------------|  
|`COR_PUB_MANAGEDONLY`|<span data-ttu-id="08429-108">Managed 進程。</span><span class="sxs-lookup"><span data-stu-id="08429-108">A managed process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08429-109">備註</span><span class="sxs-lookup"><span data-stu-id="08429-109">Remarks</span></span>  
 <span data-ttu-id="08429-110">目前版本的非受控偵錯工具開發介面只會列舉受管理的進程。</span><span class="sxs-lookup"><span data-stu-id="08429-110">The current version of the unmanaged debugging API enumerates only managed processes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08429-111">需求</span><span class="sxs-lookup"><span data-stu-id="08429-111">Requirements</span></span>  
 <span data-ttu-id="08429-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="08429-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08429-113">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="08429-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="08429-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08429-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08429-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08429-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08429-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="08429-116">See also</span></span>

- [<span data-ttu-id="08429-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="08429-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
