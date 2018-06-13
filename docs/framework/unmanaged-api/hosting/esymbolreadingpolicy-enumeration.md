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
ms.openlocfilehash: 28f6bdbc3e382f82b7fdd632b9fc8c4d422629c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429727"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="5b163-102">ESymbolReadingPolicy 列舉</span><span class="sxs-lookup"><span data-stu-id="5b163-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="5b163-103">包含值，設定原則的讀取程式資料庫 (PDB) 檔案。</span><span class="sxs-lookup"><span data-stu-id="5b163-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b163-104">語法</span><span class="sxs-lookup"><span data-stu-id="5b163-104">Syntax</span></span>  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="5b163-105">成員</span><span class="sxs-lookup"><span data-stu-id="5b163-105">Members</span></span>  
  
|<span data-ttu-id="5b163-106">成員</span><span class="sxs-lookup"><span data-stu-id="5b163-106">Member</span></span>|<span data-ttu-id="5b163-107">描述</span><span class="sxs-lookup"><span data-stu-id="5b163-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="5b163-108">指定偵錯工具應該一律讀取 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="5b163-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="5b163-109">指定偵錯工具應該讀取與完全信任組件相關聯的 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="5b163-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="5b163-110">指定偵錯工具應該永遠不會讀取 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="5b163-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b163-111">備註</span><span class="sxs-lookup"><span data-stu-id="5b163-111">Remarks</span></span>  
 <span data-ttu-id="5b163-112">`ESymbolReadingPolicy`列舉會搭配[iclrdebugmanager:: Setsymbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="5b163-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b163-113">需求</span><span class="sxs-lookup"><span data-stu-id="5b163-113">Requirements</span></span>  
 <span data-ttu-id="5b163-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5b163-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b163-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5b163-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b163-116">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5b163-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b163-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b163-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b163-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b163-118">See Also</span></span>  
 [<span data-ttu-id="5b163-119">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="5b163-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
