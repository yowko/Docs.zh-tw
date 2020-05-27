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
ms.openlocfilehash: 941093b9a0856c2b716ba359c854473f3c9ea26a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006515"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="d6185-102">StackOverflowInfo 結構</span><span class="sxs-lookup"><span data-stu-id="d6185-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="d6185-103">儲存發生的溢位類型，以及因溢位而擲回之例外狀況的資訊。</span><span class="sxs-lookup"><span data-stu-id="d6185-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6185-104">語法</span><span class="sxs-lookup"><span data-stu-id="d6185-104">Syntax</span></span>  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="d6185-105">成員</span><span class="sxs-lookup"><span data-stu-id="d6185-105">Members</span></span>  
  
|<span data-ttu-id="d6185-106">成員</span><span class="sxs-lookup"><span data-stu-id="d6185-106">Member</span></span>|<span data-ttu-id="d6185-107">描述</span><span class="sxs-lookup"><span data-stu-id="d6185-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="d6185-108">指定溢位類型的[StackOverflowType](stackoverflowtype-enumeration.md)列舉值。</span><span class="sxs-lookup"><span data-stu-id="d6185-108">A value of the [StackOverflowType](stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="d6185-109">Win32 物件的指標 `EXCEPTION_POINTERS` ，其中包含例外狀況記錄，其中含有與電腦無關的例外狀況描述，以及具有在例外狀況時的處理器內容之電腦相依描述的內容記錄。</span><span class="sxs-lookup"><span data-stu-id="d6185-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6185-110">備註</span><span class="sxs-lookup"><span data-stu-id="d6185-110">Remarks</span></span>  
 <span data-ttu-id="d6185-111">`StackOverflowInfo`物件會傳遞至事件的[IActionOnCLREvent：： OnEvent](iactiononclrevent-onevent-method.md)方法 `Event_StackOverflow` 。</span><span class="sxs-lookup"><span data-stu-id="d6185-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6185-112">需求</span><span class="sxs-lookup"><span data-stu-id="d6185-112">Requirements</span></span>  
 <span data-ttu-id="d6185-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6185-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6185-114">**標頭：** Mscoree.dll .idl</span><span class="sxs-lookup"><span data-stu-id="d6185-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="d6185-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d6185-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6185-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6185-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6185-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6185-117">See also</span></span>

- [<span data-ttu-id="d6185-118">裝載結構</span><span class="sxs-lookup"><span data-stu-id="d6185-118">Hosting Structures</span></span>](hosting-structures.md)
