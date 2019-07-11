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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44d5b7fdb2908678671505649bb906c0c5f740e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751140"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="3062b-102">StackOverflowType 列舉</span><span class="sxs-lookup"><span data-stu-id="3062b-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="3062b-103">包含值，表示堆疊溢位事件的根本原因。</span><span class="sxs-lookup"><span data-stu-id="3062b-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3062b-104">語法</span><span class="sxs-lookup"><span data-stu-id="3062b-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="3062b-105">成員</span><span class="sxs-lookup"><span data-stu-id="3062b-105">Members</span></span>  
  
|<span data-ttu-id="3062b-106">成員</span><span class="sxs-lookup"><span data-stu-id="3062b-106">Member</span></span>|<span data-ttu-id="3062b-107">描述</span><span class="sxs-lookup"><span data-stu-id="3062b-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="3062b-108">堆疊溢位所造成的執行引擎。</span><span class="sxs-lookup"><span data-stu-id="3062b-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="3062b-109">堆疊溢位所造成的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="3062b-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="3062b-110">堆疊溢位是 unmanaged 程式碼所造成。</span><span class="sxs-lookup"><span data-stu-id="3062b-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3062b-111">備註</span><span class="sxs-lookup"><span data-stu-id="3062b-111">Remarks</span></span>  
 <span data-ttu-id="3062b-112">這項資訊時，會傳遞至主機上，透過呼叫[iactiononclrevent:: Onevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="3062b-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3062b-113">需求</span><span class="sxs-lookup"><span data-stu-id="3062b-113">Requirements</span></span>  
 <span data-ttu-id="3062b-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3062b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3062b-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3062b-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3062b-116">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3062b-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3062b-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3062b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3062b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3062b-118">See also</span></span>

- [<span data-ttu-id="3062b-119">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="3062b-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
