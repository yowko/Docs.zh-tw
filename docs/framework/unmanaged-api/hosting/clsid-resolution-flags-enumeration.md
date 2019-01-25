---
title: CLSID_RESOLUTION_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- CLSID_RESOLUTION_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLSID_RESOLUTION_FLAGS
helpviewer_keywords:
- CLSID_RESOLUTION_FLAGS enumeration [.NET Framework hosting]
ms.assetid: cd8b9879-962a-4811-aa46-2e2b6bae0d84
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bee25122920a6fcec3bbd4e9e53bbdad008d5304
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514098"
---
# <a name="clsidresolutionflags-enumeration"></a><span data-ttu-id="7f9e9-102">CLSID_RESOLUTION_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="7f9e9-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="7f9e9-103">包含值，表示 common language runtime (CLR) 應該要如何解決`CLSID`。</span><span class="sxs-lookup"><span data-stu-id="7f9e9-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f9e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f9e9-104">Syntax</span></span>  
  
```  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="7f9e9-105">成員</span><span class="sxs-lookup"><span data-stu-id="7f9e9-105">Members</span></span>  
  
|<span data-ttu-id="7f9e9-106">成員</span><span class="sxs-lookup"><span data-stu-id="7f9e9-106">Member</span></span>|<span data-ttu-id="7f9e9-107">描述</span><span class="sxs-lookup"><span data-stu-id="7f9e9-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="7f9e9-108">表示預設行為。</span><span class="sxs-lookup"><span data-stu-id="7f9e9-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="7f9e9-109">表示執行階段會搜尋登錄，並套用填充碼原則。</span><span class="sxs-lookup"><span data-stu-id="7f9e9-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f9e9-110">需求</span><span class="sxs-lookup"><span data-stu-id="7f9e9-110">Requirements</span></span>  
 <span data-ttu-id="7f9e9-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f9e9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f9e9-112">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7f9e9-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f9e9-113">**.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f9e9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f9e9-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f9e9-114">See also</span></span>
- [<span data-ttu-id="7f9e9-115">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="7f9e9-115">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
