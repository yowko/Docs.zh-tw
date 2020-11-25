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
ms.openlocfilehash: 19731f34d259757e6de62dd4b4f0d4735d1c2e61
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706160"
---
# <a name="clsid_resolution_flags-enumeration"></a><span data-ttu-id="0ea52-102">CLSID_RESOLUTION_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="0ea52-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>

<span data-ttu-id="0ea52-103">包含值，指出 common language runtime (CLR) 應該如何解析 `CLSID` 。</span><span class="sxs-lookup"><span data-stu-id="0ea52-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ea52-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ea52-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="0ea52-105">成員</span><span class="sxs-lookup"><span data-stu-id="0ea52-105">Members</span></span>  
  
|<span data-ttu-id="0ea52-106">member</span><span class="sxs-lookup"><span data-stu-id="0ea52-106">Member</span></span>|<span data-ttu-id="0ea52-107">描述</span><span class="sxs-lookup"><span data-stu-id="0ea52-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="0ea52-108">表示預設行為。</span><span class="sxs-lookup"><span data-stu-id="0ea52-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="0ea52-109">指出執行時間會搜尋登錄並套用填充碼原則。</span><span class="sxs-lookup"><span data-stu-id="0ea52-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ea52-110">需求</span><span class="sxs-lookup"><span data-stu-id="0ea52-110">Requirements</span></span>  

 <span data-ttu-id="0ea52-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ea52-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ea52-112">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0ea52-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ea52-113">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ea52-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ea52-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ea52-114">See also</span></span>

- [<span data-ttu-id="0ea52-115">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="0ea52-115">Hosting Enumerations</span></span>](hosting-enumerations.md)
