---
title: ECustomDumpFlavor 列舉
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1e69d9cbf39049e82803d2f7bc795cc9fd0b368
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154436"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="72f01-102">ECustomDumpFlavor 列舉</span><span class="sxs-lookup"><span data-stu-id="72f01-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="72f01-103">包含值，表示要包含在自訂的子集的堆積中的項目在報告錯誤時傾印。</span><span class="sxs-lookup"><span data-stu-id="72f01-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72f01-104">語法</span><span class="sxs-lookup"><span data-stu-id="72f01-104">Syntax</span></span>  
  
```  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="72f01-105">成員</span><span class="sxs-lookup"><span data-stu-id="72f01-105">Members</span></span>  
  
|<span data-ttu-id="72f01-106">成員</span><span class="sxs-lookup"><span data-stu-id="72f01-106">Member</span></span>|<span data-ttu-id="72f01-107">描述</span><span class="sxs-lookup"><span data-stu-id="72f01-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="72f01-108">指定自訂的堆積傾印應該啟動小型傾印，並包含指定的任何額外的資料[CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)執行個體會傳遞至相同的方法。</span><span class="sxs-lookup"><span data-stu-id="72f01-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="72f01-109">指定自訂的堆積傾印應該收集不以動態方式配置的所有執行階段狀態資料。</span><span class="sxs-lookup"><span data-stu-id="72f01-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72f01-110">備註</span><span class="sxs-lookup"><span data-stu-id="72f01-110">Remarks</span></span>  
 <span data-ttu-id="72f01-111">類型的參數`ECustomDumpFlavor`傳遞給[iclrerrorreportingmanager:: Begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="72f01-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72f01-112">需求</span><span class="sxs-lookup"><span data-stu-id="72f01-112">Requirements</span></span>  
 <span data-ttu-id="72f01-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72f01-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72f01-114">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="72f01-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72f01-115">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="72f01-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72f01-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72f01-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72f01-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72f01-117">See also</span></span>

- [<span data-ttu-id="72f01-118">ECustomDumpItemKind 列舉</span><span class="sxs-lookup"><span data-stu-id="72f01-118">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="72f01-119">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="72f01-119">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="72f01-120">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="72f01-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
