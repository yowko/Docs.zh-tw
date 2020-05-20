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
ms.openlocfilehash: 5ac015f958d9504bbd14a66ead86548b8df32764
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616771"
---
# <a name="clsid_resolution_flags-enumeration"></a><span data-ttu-id="abe9e-102">CLSID_RESOLUTION_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="abe9e-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="abe9e-103">包含表示 common language runtime （CLR）應如何解析的值 `CLSID` 。</span><span class="sxs-lookup"><span data-stu-id="abe9e-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abe9e-104">語法</span><span class="sxs-lookup"><span data-stu-id="abe9e-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="abe9e-105">成員</span><span class="sxs-lookup"><span data-stu-id="abe9e-105">Members</span></span>  
  
|<span data-ttu-id="abe9e-106">成員</span><span class="sxs-lookup"><span data-stu-id="abe9e-106">Member</span></span>|<span data-ttu-id="abe9e-107">說明</span><span class="sxs-lookup"><span data-stu-id="abe9e-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="abe9e-108">表示預設行為。</span><span class="sxs-lookup"><span data-stu-id="abe9e-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="abe9e-109">表示執行時間會搜尋登錄並套用填充碼原則。</span><span class="sxs-lookup"><span data-stu-id="abe9e-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="abe9e-110">需求</span><span class="sxs-lookup"><span data-stu-id="abe9e-110">Requirements</span></span>  
 <span data-ttu-id="abe9e-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abe9e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abe9e-112">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="abe9e-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="abe9e-113">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abe9e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe9e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abe9e-114">See also</span></span>

- [<span data-ttu-id="abe9e-115">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="abe9e-115">Hosting Enumerations</span></span>](hosting-enumerations.md)
