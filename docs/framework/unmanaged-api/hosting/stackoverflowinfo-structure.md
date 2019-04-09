---
title: StackOverflowInfo 結構
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac0f5d522a24394369583692f8c564254529bf13
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137342"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="e28a0-102">StackOverflowInfo 結構</span><span class="sxs-lookup"><span data-stu-id="e28a0-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="e28a0-103">因為溢位而擲回的例外狀況，會儲存發生溢位和資訊的類型。</span><span class="sxs-lookup"><span data-stu-id="e28a0-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e28a0-104">語法</span><span class="sxs-lookup"><span data-stu-id="e28a0-104">Syntax</span></span>  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="e28a0-105">成員</span><span class="sxs-lookup"><span data-stu-id="e28a0-105">Members</span></span>  
  
|<span data-ttu-id="e28a0-106">成員</span><span class="sxs-lookup"><span data-stu-id="e28a0-106">Member</span></span>|<span data-ttu-id="e28a0-107">描述</span><span class="sxs-lookup"><span data-stu-id="e28a0-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="e28a0-108">值為[StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md)列舉，指定的類型溢位。</span><span class="sxs-lookup"><span data-stu-id="e28a0-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="e28a0-109">Win32 指標`EXCEPTION_POINTERS`物件，其中包含與不受機器限制的描述例外狀況的例外狀況記錄，以及內容記錄例外狀況當時的處理器內容的電腦相關描述。</span><span class="sxs-lookup"><span data-stu-id="e28a0-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e28a0-110">備註</span><span class="sxs-lookup"><span data-stu-id="e28a0-110">Remarks</span></span>  
 <span data-ttu-id="e28a0-111">A`StackOverflowInfo`物件會傳遞給[iactiononclrevent:: Onevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)方法`Event_StackOverflow`事件。</span><span class="sxs-lookup"><span data-stu-id="e28a0-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e28a0-112">需求</span><span class="sxs-lookup"><span data-stu-id="e28a0-112">Requirements</span></span>  
 <span data-ttu-id="e28a0-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e28a0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e28a0-114">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="e28a0-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="e28a0-115">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e28a0-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e28a0-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="e28a0-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e28a0-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e28a0-117">See also</span></span>

- [<span data-ttu-id="e28a0-118">裝載結構</span><span class="sxs-lookup"><span data-stu-id="e28a0-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
