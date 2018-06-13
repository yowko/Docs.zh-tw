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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f742d219d603488bbade091f7a8192785d3e84f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433092"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="9beac-102">CustomDumpItem 結構</span><span class="sxs-lookup"><span data-stu-id="9beac-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="9beac-103">描述要加入至自訂的傾印在錯誤報告中的項目。</span><span class="sxs-lookup"><span data-stu-id="9beac-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9beac-104">語法</span><span class="sxs-lookup"><span data-stu-id="9beac-104">Syntax</span></span>  
  
```  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="9beac-105">成員</span><span class="sxs-lookup"><span data-stu-id="9beac-105">Members</span></span>  
  
|<span data-ttu-id="9beac-106">成員</span><span class="sxs-lookup"><span data-stu-id="9beac-106">Member</span></span>|<span data-ttu-id="9beac-107">描述</span><span class="sxs-lookup"><span data-stu-id="9beac-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="9beac-108">[ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)值，指出要加入項目的類型。</span><span class="sxs-lookup"><span data-stu-id="9beac-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="9beac-109">目前無法使用。</span><span class="sxs-lookup"><span data-stu-id="9beac-109">Not currently used.</span></span> <span data-ttu-id="9beac-110">任何加入的 union 項目必須是不能大於指標大小。</span><span class="sxs-lookup"><span data-stu-id="9beac-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="9beac-111">如果`struct`是必要，您必須分別將其配置並指向它。</span><span class="sxs-lookup"><span data-stu-id="9beac-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9beac-112">備註</span><span class="sxs-lookup"><span data-stu-id="9beac-112">Remarks</span></span>  
 <span data-ttu-id="9beac-113">[Iclrerrorreportingmanager:: Begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)採用參數的型別`CustomDumpItem`。</span><span class="sxs-lookup"><span data-stu-id="9beac-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9beac-114">需求</span><span class="sxs-lookup"><span data-stu-id="9beac-114">Requirements</span></span>  
 <span data-ttu-id="9beac-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9beac-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9beac-116">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="9beac-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="9beac-117">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9beac-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9beac-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9beac-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9beac-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9beac-119">See Also</span></span>  
 [<span data-ttu-id="9beac-120">裝載結構</span><span class="sxs-lookup"><span data-stu-id="9beac-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
