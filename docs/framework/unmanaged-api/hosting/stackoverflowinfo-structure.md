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
ms.openlocfilehash: a8a57cfcaf36949d4d10c6ec267a5f55a2aee5eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729924"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="91922-102">StackOverflowInfo 結構</span><span class="sxs-lookup"><span data-stu-id="91922-102">StackOverflowInfo Structure</span></span>

<span data-ttu-id="91922-103">儲存發生溢位的型別，以及因為溢位所擲回之例外狀況的資訊。</span><span class="sxs-lookup"><span data-stu-id="91922-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91922-104">語法</span><span class="sxs-lookup"><span data-stu-id="91922-104">Syntax</span></span>  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="91922-105">成員</span><span class="sxs-lookup"><span data-stu-id="91922-105">Members</span></span>  
  
|<span data-ttu-id="91922-106">member</span><span class="sxs-lookup"><span data-stu-id="91922-106">Member</span></span>|<span data-ttu-id="91922-107">描述</span><span class="sxs-lookup"><span data-stu-id="91922-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="91922-108">[StackOverflowType](stackoverflowtype-enumeration.md)列舉的值，這個值會指定溢位的型別。</span><span class="sxs-lookup"><span data-stu-id="91922-108">A value of the [StackOverflowType](stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="91922-109">Win32 物件的指標 `EXCEPTION_POINTERS` ，其中包含例外狀況記錄與電腦無關的例外狀況記錄，以及在發生例外狀況時，具有電腦相依描述的內容記錄。</span><span class="sxs-lookup"><span data-stu-id="91922-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91922-110">備註</span><span class="sxs-lookup"><span data-stu-id="91922-110">Remarks</span></span>  

 <span data-ttu-id="91922-111">`StackOverflowInfo`物件會傳遞給事件的[IActionOnCLREvent：： OnEvent](iactiononclrevent-onevent-method.md)方法 `Event_StackOverflow` 。</span><span class="sxs-lookup"><span data-stu-id="91922-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91922-112">需求</span><span class="sxs-lookup"><span data-stu-id="91922-112">Requirements</span></span>  

 <span data-ttu-id="91922-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91922-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91922-114">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="91922-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="91922-115">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="91922-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91922-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91922-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91922-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91922-117">See also</span></span>

- [<span data-ttu-id="91922-118">裝載結構</span><span class="sxs-lookup"><span data-stu-id="91922-118">Hosting Structures</span></span>](hosting-structures.md)
