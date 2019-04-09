---
title: ESymbolReadingPolicy 列舉
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ba29952fe4a6edfc6e9e80ec02f82de65ef0064
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208419"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="28dfb-102">ESymbolReadingPolicy 列舉</span><span class="sxs-lookup"><span data-stu-id="28dfb-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="28dfb-103">包含讀取程式資料庫 (PDB) 檔案的原則設定的值。</span><span class="sxs-lookup"><span data-stu-id="28dfb-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28dfb-104">語法</span><span class="sxs-lookup"><span data-stu-id="28dfb-104">Syntax</span></span>  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="28dfb-105">成員</span><span class="sxs-lookup"><span data-stu-id="28dfb-105">Members</span></span>  
  
|<span data-ttu-id="28dfb-106">成員</span><span class="sxs-lookup"><span data-stu-id="28dfb-106">Member</span></span>|<span data-ttu-id="28dfb-107">描述</span><span class="sxs-lookup"><span data-stu-id="28dfb-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="28dfb-108">指定偵錯工具應該一律讀取 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="28dfb-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="28dfb-109">指定偵錯工具應該讀取與完全信任組件相關聯的 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="28dfb-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="28dfb-110">指定偵錯工具應該永遠不會讀取 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="28dfb-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28dfb-111">備註</span><span class="sxs-lookup"><span data-stu-id="28dfb-111">Remarks</span></span>  
 <span data-ttu-id="28dfb-112">`ESymbolReadingPolicy`列舉型別會搭配[iclrdebugmanager:: Setsymbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="28dfb-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28dfb-113">需求</span><span class="sxs-lookup"><span data-stu-id="28dfb-113">Requirements</span></span>  
 <span data-ttu-id="28dfb-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="28dfb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28dfb-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="28dfb-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28dfb-116">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="28dfb-116">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="28dfb-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="28dfb-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="28dfb-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28dfb-118">See also</span></span>

- [<span data-ttu-id="28dfb-119">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="28dfb-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
