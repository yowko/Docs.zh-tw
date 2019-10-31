---
title: StackOverflowType 列舉
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
ms.openlocfilehash: f09c6bb79d7bd28f4d8b74237b6f343a07b79062
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141479"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="2ee82-102">StackOverflowType 列舉</span><span class="sxs-lookup"><span data-stu-id="2ee82-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="2ee82-103">包含值，指出堆疊溢位事件的根本原因。</span><span class="sxs-lookup"><span data-stu-id="2ee82-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ee82-104">語法</span><span class="sxs-lookup"><span data-stu-id="2ee82-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="2ee82-105">Members</span><span class="sxs-lookup"><span data-stu-id="2ee82-105">Members</span></span>  
  
|<span data-ttu-id="2ee82-106">成員</span><span class="sxs-lookup"><span data-stu-id="2ee82-106">Member</span></span>|<span data-ttu-id="2ee82-107">描述</span><span class="sxs-lookup"><span data-stu-id="2ee82-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="2ee82-108">堆疊溢位是由執行引擎所造成。</span><span class="sxs-lookup"><span data-stu-id="2ee82-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="2ee82-109">堆疊溢位是由 managed 程式碼所造成。</span><span class="sxs-lookup"><span data-stu-id="2ee82-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="2ee82-110">堆疊溢位是由未受管理的程式碼所造成。</span><span class="sxs-lookup"><span data-stu-id="2ee82-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ee82-111">備註</span><span class="sxs-lookup"><span data-stu-id="2ee82-111">Remarks</span></span>  
 <span data-ttu-id="2ee82-112">此資訊會透過呼叫[IActionOnCLREvent：： OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)方法傳遞至主機。</span><span class="sxs-lookup"><span data-stu-id="2ee82-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ee82-113">需求</span><span class="sxs-lookup"><span data-stu-id="2ee82-113">Requirements</span></span>  
 <span data-ttu-id="2ee82-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2ee82-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ee82-115">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="2ee82-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ee82-116">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="2ee82-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ee82-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ee82-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ee82-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="2ee82-118">See also</span></span>

- [<span data-ttu-id="2ee82-119">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="2ee82-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
