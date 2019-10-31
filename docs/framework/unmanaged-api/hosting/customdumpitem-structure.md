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
ms.openlocfilehash: ae64edd8a3a628100d4c51d0b78be1bc8d49fc17
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138287"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="66951-102">CustomDumpItem 結構</span><span class="sxs-lookup"><span data-stu-id="66951-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="66951-103">描述要在錯誤報表中新增至自訂傾印的專案。</span><span class="sxs-lookup"><span data-stu-id="66951-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66951-104">語法</span><span class="sxs-lookup"><span data-stu-id="66951-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="66951-105">Members</span><span class="sxs-lookup"><span data-stu-id="66951-105">Members</span></span>  
  
|<span data-ttu-id="66951-106">成員</span><span class="sxs-lookup"><span data-stu-id="66951-106">Member</span></span>|<span data-ttu-id="66951-107">描述</span><span class="sxs-lookup"><span data-stu-id="66951-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="66951-108">[ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)值，表示要新增的專案類型。</span><span class="sxs-lookup"><span data-stu-id="66951-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="66951-109">目前未使用。</span><span class="sxs-lookup"><span data-stu-id="66951-109">Not currently used.</span></span> <span data-ttu-id="66951-110">加入至聯集的任何專案都不能大於指標大小。</span><span class="sxs-lookup"><span data-stu-id="66951-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="66951-111">如果需要 `struct`，您必須分別加以配置並指向它。</span><span class="sxs-lookup"><span data-stu-id="66951-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66951-112">備註</span><span class="sxs-lookup"><span data-stu-id="66951-112">Remarks</span></span>  
 <span data-ttu-id="66951-113">[ICLRErrorReportingManager：： BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)接受 `CustomDumpItem`類型的參數。</span><span class="sxs-lookup"><span data-stu-id="66951-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66951-114">需求</span><span class="sxs-lookup"><span data-stu-id="66951-114">Requirements</span></span>  
 <span data-ttu-id="66951-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="66951-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66951-116">**標頭：** Mscoree.dll .idl</span><span class="sxs-lookup"><span data-stu-id="66951-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="66951-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="66951-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66951-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66951-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66951-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="66951-119">See also</span></span>

- [<span data-ttu-id="66951-120">裝載結構</span><span class="sxs-lookup"><span data-stu-id="66951-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
