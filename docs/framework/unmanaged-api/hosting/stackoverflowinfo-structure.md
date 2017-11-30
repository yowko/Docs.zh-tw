---
title: "StackOverflowInfo 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackOverflowInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: StackOverflowInfo
helpviewer_keywords: StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 102f744ecc769a10161cd20767e8e49c838252a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="23ee3-102">StackOverflowInfo 結構</span><span class="sxs-lookup"><span data-stu-id="23ee3-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="23ee3-103">因為溢位而擲回的例外狀況會儲存發生溢位和資訊的類型。</span><span class="sxs-lookup"><span data-stu-id="23ee3-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23ee3-104">語法</span><span class="sxs-lookup"><span data-stu-id="23ee3-104">Syntax</span></span>  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="23ee3-105">成員</span><span class="sxs-lookup"><span data-stu-id="23ee3-105">Members</span></span>  
  
|<span data-ttu-id="23ee3-106">成員</span><span class="sxs-lookup"><span data-stu-id="23ee3-106">Member</span></span>|<span data-ttu-id="23ee3-107">說明</span><span class="sxs-lookup"><span data-stu-id="23ee3-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="23ee3-108">值為[StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md)列舉，指定的類型溢位。</span><span class="sxs-lookup"><span data-stu-id="23ee3-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="23ee3-109">對 win32 指標`EXCEPTION_POINTERS`物件，其中包含機器無關描述例外狀況的例外狀況記錄，以及內容記錄例外狀況的時間的處理器內容的電腦相關描述。</span><span class="sxs-lookup"><span data-stu-id="23ee3-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23ee3-110">備註</span><span class="sxs-lookup"><span data-stu-id="23ee3-110">Remarks</span></span>  
 <span data-ttu-id="23ee3-111">A`StackOverflowInfo`物件傳遞至[iactiononclrevent:: Onevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)方法`Event_StackOverflow`事件。</span><span class="sxs-lookup"><span data-stu-id="23ee3-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23ee3-112">需求</span><span class="sxs-lookup"><span data-stu-id="23ee3-112">Requirements</span></span>  
 <span data-ttu-id="23ee3-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23ee3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23ee3-114">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="23ee3-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="23ee3-115">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="23ee3-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23ee3-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23ee3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23ee3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23ee3-117">See Also</span></span>  
 [<span data-ttu-id="23ee3-118">裝載結構</span><span class="sxs-lookup"><span data-stu-id="23ee3-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
