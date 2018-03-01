---
title: "ESymbolReadingPolicy 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ESymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ESymbolReadingPolicy
helpviewer_keywords:
- ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4fdb18a343f91e85619f6d62e466fdd558044727
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="d1430-102">ESymbolReadingPolicy 列舉</span><span class="sxs-lookup"><span data-stu-id="d1430-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="d1430-103">包含值，設定原則的讀取程式資料庫 (PDB) 檔案。</span><span class="sxs-lookup"><span data-stu-id="d1430-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1430-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1430-104">Syntax</span></span>  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="d1430-105">成員</span><span class="sxs-lookup"><span data-stu-id="d1430-105">Members</span></span>  
  
|<span data-ttu-id="d1430-106">成員</span><span class="sxs-lookup"><span data-stu-id="d1430-106">Member</span></span>|<span data-ttu-id="d1430-107">描述</span><span class="sxs-lookup"><span data-stu-id="d1430-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="d1430-108">指定偵錯工具應該一律讀取 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="d1430-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="d1430-109">指定偵錯工具應該讀取與完全信任組件相關聯的 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="d1430-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="d1430-110">指定偵錯工具應該永遠不會讀取 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="d1430-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1430-111">備註</span><span class="sxs-lookup"><span data-stu-id="d1430-111">Remarks</span></span>  
 <span data-ttu-id="d1430-112">`ESymbolReadingPolicy`列舉會搭配[iclrdebugmanager:: Setsymbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d1430-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1430-113">需求</span><span class="sxs-lookup"><span data-stu-id="d1430-113">Requirements</span></span>  
 <span data-ttu-id="d1430-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1430-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1430-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d1430-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1430-116">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1430-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1430-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1430-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1430-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="d1430-118">See Also</span></span>  
 [<span data-ttu-id="d1430-119">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="d1430-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
