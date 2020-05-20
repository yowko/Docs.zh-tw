---
title: CustomDumpItem 結構
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
ms.openlocfilehash: 5c77a332593ba470d2e29b87cba182a770d5db7e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616433"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="a0eda-102">CustomDumpItem 結構</span><span class="sxs-lookup"><span data-stu-id="a0eda-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="a0eda-103">描述要在錯誤報表中新增至自訂傾印的專案。</span><span class="sxs-lookup"><span data-stu-id="a0eda-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0eda-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0eda-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="a0eda-105">成員</span><span class="sxs-lookup"><span data-stu-id="a0eda-105">Members</span></span>  
  
|<span data-ttu-id="a0eda-106">成員</span><span class="sxs-lookup"><span data-stu-id="a0eda-106">Member</span></span>|<span data-ttu-id="a0eda-107">說明</span><span class="sxs-lookup"><span data-stu-id="a0eda-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="a0eda-108">[ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md)值，表示要新增的專案類型。</span><span class="sxs-lookup"><span data-stu-id="a0eda-108">An [ECustomDumpItemKind](ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="a0eda-109">目前無法使用。</span><span class="sxs-lookup"><span data-stu-id="a0eda-109">Not currently used.</span></span> <span data-ttu-id="a0eda-110">加入至聯集的任何專案都不能大於指標大小。</span><span class="sxs-lookup"><span data-stu-id="a0eda-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="a0eda-111">如果 `struct` 需要，您必須分別加以配置並指向它。</span><span class="sxs-lookup"><span data-stu-id="a0eda-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0eda-112">備註</span><span class="sxs-lookup"><span data-stu-id="a0eda-112">Remarks</span></span>  
 <span data-ttu-id="a0eda-113">[ICLRErrorReportingManager：： BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md)接受類型為的參數 `CustomDumpItem` 。</span><span class="sxs-lookup"><span data-stu-id="a0eda-113">[ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0eda-114">需求</span><span class="sxs-lookup"><span data-stu-id="a0eda-114">Requirements</span></span>  
 <span data-ttu-id="a0eda-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0eda-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0eda-116">**標頭：** Mscoree.dll .idl</span><span class="sxs-lookup"><span data-stu-id="a0eda-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="a0eda-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a0eda-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0eda-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0eda-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0eda-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0eda-119">See also</span></span>

- [<span data-ttu-id="a0eda-120">裝載結構</span><span class="sxs-lookup"><span data-stu-id="a0eda-120">Hosting Structures</span></span>](hosting-structures.md)
