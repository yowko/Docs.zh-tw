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
ms.openlocfilehash: 930d56fcfe7cf0d2a128c2068e724b85a224b3fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568916"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="66768-102">CustomDumpItem 結構</span><span class="sxs-lookup"><span data-stu-id="66768-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="66768-103">描述要新增至自訂的傾印，錯誤報告中的項目。</span><span class="sxs-lookup"><span data-stu-id="66768-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66768-104">語法</span><span class="sxs-lookup"><span data-stu-id="66768-104">Syntax</span></span>  
  
```  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="66768-105">成員</span><span class="sxs-lookup"><span data-stu-id="66768-105">Members</span></span>  
  
|<span data-ttu-id="66768-106">成員</span><span class="sxs-lookup"><span data-stu-id="66768-106">Member</span></span>|<span data-ttu-id="66768-107">描述</span><span class="sxs-lookup"><span data-stu-id="66768-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="66768-108">[ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)值，指出要加入的項目種類。</span><span class="sxs-lookup"><span data-stu-id="66768-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="66768-109">目前無法使用。</span><span class="sxs-lookup"><span data-stu-id="66768-109">Not currently used.</span></span> <span data-ttu-id="66768-110">加入等位的任何項目必須是不能大於指標大小。</span><span class="sxs-lookup"><span data-stu-id="66768-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="66768-111">如果`struct`是有需要，您必須分別將其配置，並指向它。</span><span class="sxs-lookup"><span data-stu-id="66768-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66768-112">備註</span><span class="sxs-lookup"><span data-stu-id="66768-112">Remarks</span></span>  
 <span data-ttu-id="66768-113">[Iclrerrorreportingmanager:: Begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)採用參數的型別`CustomDumpItem`。</span><span class="sxs-lookup"><span data-stu-id="66768-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66768-114">需求</span><span class="sxs-lookup"><span data-stu-id="66768-114">Requirements</span></span>  
 <span data-ttu-id="66768-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="66768-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66768-116">**標頭：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="66768-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="66768-117">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="66768-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66768-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66768-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66768-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66768-119">See also</span></span>
- [<span data-ttu-id="66768-120">裝載結構</span><span class="sxs-lookup"><span data-stu-id="66768-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
