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
ms.openlocfilehash: 154beef9398029f31dcb4d081019b9f292238af4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176470"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="6d449-102">CustomDumpItem 結構</span><span class="sxs-lookup"><span data-stu-id="6d449-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="6d449-103">描述要在錯誤報表中添加到自訂轉儲的項。</span><span class="sxs-lookup"><span data-stu-id="6d449-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d449-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d449-104">Syntax</span></span>  
  
```cpp  
struct {  
    ECustomDumpItemKind itemKind;
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="6d449-105">成員</span><span class="sxs-lookup"><span data-stu-id="6d449-105">Members</span></span>  
  
|<span data-ttu-id="6d449-106">member</span><span class="sxs-lookup"><span data-stu-id="6d449-106">Member</span></span>|<span data-ttu-id="6d449-107">描述</span><span class="sxs-lookup"><span data-stu-id="6d449-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="6d449-108">[ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)值，指示要添加的項類型。</span><span class="sxs-lookup"><span data-stu-id="6d449-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="6d449-109">目前無法使用。</span><span class="sxs-lookup"><span data-stu-id="6d449-109">Not currently used.</span></span> <span data-ttu-id="6d449-110">添加到聯合的任何項必須不大於指標大小。</span><span class="sxs-lookup"><span data-stu-id="6d449-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="6d449-111">如果需要`struct`， 必須單獨分配並指向它。</span><span class="sxs-lookup"><span data-stu-id="6d449-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d449-112">備註</span><span class="sxs-lookup"><span data-stu-id="6d449-112">Remarks</span></span>  
 <span data-ttu-id="6d449-113">[ICLR錯誤報表管理器：開始自訂轉儲](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)採用類型的`CustomDumpItem`參數。</span><span class="sxs-lookup"><span data-stu-id="6d449-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d449-114">需求</span><span class="sxs-lookup"><span data-stu-id="6d449-114">Requirements</span></span>  
 <span data-ttu-id="6d449-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6d449-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d449-116">**標題：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="6d449-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="6d449-117">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="6d449-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d449-118">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d449-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d449-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d449-119">See also</span></span>

- [<span data-ttu-id="6d449-120">裝載結構</span><span class="sxs-lookup"><span data-stu-id="6d449-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
