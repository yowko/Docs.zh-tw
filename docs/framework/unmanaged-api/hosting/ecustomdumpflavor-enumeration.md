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
ms.openlocfilehash: 057794fe524a0ee01f6f090ca7e11a4a4b523047
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124921"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="ac4ac-102">ECustomDumpFlavor 列舉</span><span class="sxs-lookup"><span data-stu-id="ac4ac-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="ac4ac-103">包含值，指出報告錯誤時，要包含在堆積傾印的自訂子集中的專案。</span><span class="sxs-lookup"><span data-stu-id="ac4ac-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac4ac-104">語法</span><span class="sxs-lookup"><span data-stu-id="ac4ac-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="ac4ac-105">Members</span><span class="sxs-lookup"><span data-stu-id="ac4ac-105">Members</span></span>  
  
|<span data-ttu-id="ac4ac-106">成員</span><span class="sxs-lookup"><span data-stu-id="ac4ac-106">Member</span></span>|<span data-ttu-id="ac4ac-107">描述</span><span class="sxs-lookup"><span data-stu-id="ac4ac-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="ac4ac-108">指定自訂堆積傾印應啟動為小型傾印，並包含傳遞至相同方法之任何[CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)實例所指定的額外資料。</span><span class="sxs-lookup"><span data-stu-id="ac4ac-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="ac4ac-109">指定自訂堆積傾印應收集所有未動態配置的執行時間狀態資料。</span><span class="sxs-lookup"><span data-stu-id="ac4ac-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac4ac-110">備註</span><span class="sxs-lookup"><span data-stu-id="ac4ac-110">Remarks</span></span>  
 <span data-ttu-id="ac4ac-111">`ECustomDumpFlavor` 類型的參數會傳遞至[ICLRErrorReportingManager：： BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ac4ac-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac4ac-112">需求</span><span class="sxs-lookup"><span data-stu-id="ac4ac-112">Requirements</span></span>  
 <span data-ttu-id="ac4ac-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ac4ac-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac4ac-114">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="ac4ac-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac4ac-115">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="ac4ac-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac4ac-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac4ac-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac4ac-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="ac4ac-117">See also</span></span>

- [<span data-ttu-id="ac4ac-118">ECustomDumpItemKind 列舉</span><span class="sxs-lookup"><span data-stu-id="ac4ac-118">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="ac4ac-119">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="ac4ac-119">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="ac4ac-120">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="ac4ac-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
