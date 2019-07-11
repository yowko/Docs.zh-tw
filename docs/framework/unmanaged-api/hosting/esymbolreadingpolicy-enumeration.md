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
ms.openlocfilehash: 45b6b8593331801dd237d0a730afbd5a6a714bbf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774188"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="ce2e6-102">ESymbolReadingPolicy 列舉</span><span class="sxs-lookup"><span data-stu-id="ce2e6-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="ce2e6-103">包含讀取程式資料庫 (PDB) 檔案的原則設定的值。</span><span class="sxs-lookup"><span data-stu-id="ce2e6-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce2e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce2e6-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="ce2e6-105">成員</span><span class="sxs-lookup"><span data-stu-id="ce2e6-105">Members</span></span>  
  
|<span data-ttu-id="ce2e6-106">成員</span><span class="sxs-lookup"><span data-stu-id="ce2e6-106">Member</span></span>|<span data-ttu-id="ce2e6-107">描述</span><span class="sxs-lookup"><span data-stu-id="ce2e6-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="ce2e6-108">指定偵錯工具應該一律讀取 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="ce2e6-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="ce2e6-109">指定偵錯工具應該讀取與完全信任組件相關聯的 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="ce2e6-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="ce2e6-110">指定偵錯工具應該永遠不會讀取 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="ce2e6-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce2e6-111">備註</span><span class="sxs-lookup"><span data-stu-id="ce2e6-111">Remarks</span></span>  
 <span data-ttu-id="ce2e6-112">`ESymbolReadingPolicy`列舉型別會搭配[iclrdebugmanager:: Setsymbolreadingpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ce2e6-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce2e6-113">需求</span><span class="sxs-lookup"><span data-stu-id="ce2e6-113">Requirements</span></span>  
 <span data-ttu-id="ce2e6-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce2e6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce2e6-115">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ce2e6-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce2e6-116">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ce2e6-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce2e6-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce2e6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce2e6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce2e6-118">See also</span></span>

- [<span data-ttu-id="ce2e6-119">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="ce2e6-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
