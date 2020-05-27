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
ms.openlocfilehash: f399d33dbe05cb5768aa45533ef30d28409e18e2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006463"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="5a501-102">StackOverflowType 列舉</span><span class="sxs-lookup"><span data-stu-id="5a501-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="5a501-103">包含值，指出堆疊溢位事件的根本原因。</span><span class="sxs-lookup"><span data-stu-id="5a501-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a501-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a501-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="5a501-105">成員</span><span class="sxs-lookup"><span data-stu-id="5a501-105">Members</span></span>  
  
|<span data-ttu-id="5a501-106">成員</span><span class="sxs-lookup"><span data-stu-id="5a501-106">Member</span></span>|<span data-ttu-id="5a501-107">描述</span><span class="sxs-lookup"><span data-stu-id="5a501-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="5a501-108">堆疊溢位是由執行引擎所造成。</span><span class="sxs-lookup"><span data-stu-id="5a501-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="5a501-109">堆疊溢位是由 managed 程式碼所造成。</span><span class="sxs-lookup"><span data-stu-id="5a501-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="5a501-110">堆疊溢位是由未受管理的程式碼所造成。</span><span class="sxs-lookup"><span data-stu-id="5a501-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a501-111">備註</span><span class="sxs-lookup"><span data-stu-id="5a501-111">Remarks</span></span>  
 <span data-ttu-id="5a501-112">此資訊會透過呼叫[IActionOnCLREvent：： OnEvent](iactiononclrevent-onevent-method.md)方法傳遞至主機。</span><span class="sxs-lookup"><span data-stu-id="5a501-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a501-113">需求</span><span class="sxs-lookup"><span data-stu-id="5a501-113">Requirements</span></span>  
 <span data-ttu-id="5a501-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a501-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a501-115">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="5a501-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a501-116">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="5a501-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a501-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a501-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a501-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a501-118">See also</span></span>

- [<span data-ttu-id="5a501-119">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="5a501-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
