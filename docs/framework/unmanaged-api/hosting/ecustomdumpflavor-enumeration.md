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
ms.openlocfilehash: 9b4c1187945b4c243375a3096c3a8a3b22599aef
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616277"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="2f99e-102">ECustomDumpFlavor 列舉</span><span class="sxs-lookup"><span data-stu-id="2f99e-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="2f99e-103">包含值，指出報告錯誤時，要包含在堆積傾印的自訂子集中的專案。</span><span class="sxs-lookup"><span data-stu-id="2f99e-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f99e-104">語法</span><span class="sxs-lookup"><span data-stu-id="2f99e-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="2f99e-105">成員</span><span class="sxs-lookup"><span data-stu-id="2f99e-105">Members</span></span>  
  
|<span data-ttu-id="2f99e-106">成員</span><span class="sxs-lookup"><span data-stu-id="2f99e-106">Member</span></span>|<span data-ttu-id="2f99e-107">說明</span><span class="sxs-lookup"><span data-stu-id="2f99e-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="2f99e-108">指定自訂堆積傾印應啟動為小型傾印，並包含傳遞至相同方法之任何[CustomDumpItem](customdumpitem-structure.md)實例所指定的額外資料。</span><span class="sxs-lookup"><span data-stu-id="2f99e-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="2f99e-109">指定自訂堆積傾印應收集所有未動態配置的執行時間狀態資料。</span><span class="sxs-lookup"><span data-stu-id="2f99e-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f99e-110">備註</span><span class="sxs-lookup"><span data-stu-id="2f99e-110">Remarks</span></span>  
 <span data-ttu-id="2f99e-111">類型的參數 `ECustomDumpFlavor` 會傳遞至[ICLRErrorReportingManager：： BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="2f99e-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f99e-112">需求</span><span class="sxs-lookup"><span data-stu-id="2f99e-112">Requirements</span></span>  
 <span data-ttu-id="2f99e-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2f99e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f99e-114">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="2f99e-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f99e-115">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="2f99e-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f99e-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f99e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f99e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f99e-117">See also</span></span>

- [<span data-ttu-id="2f99e-118">ECustomDumpItemKind 列舉</span><span class="sxs-lookup"><span data-stu-id="2f99e-118">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="2f99e-119">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="2f99e-119">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="2f99e-120">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="2f99e-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
