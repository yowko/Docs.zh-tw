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
ms.openlocfilehash: 5c3d1d0ebc56ee93c950afb4f015c8e10ec6a0f7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616171"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="15a0d-102">ESymbolReadingPolicy 列舉</span><span class="sxs-lookup"><span data-stu-id="15a0d-102">ESymbolReadingPolicy Enumeration</span></span>
<span data-ttu-id="15a0d-103">包含設定讀取程式資料庫（PDB）檔案之原則的值。</span><span class="sxs-lookup"><span data-stu-id="15a0d-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15a0d-104">語法</span><span class="sxs-lookup"><span data-stu-id="15a0d-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="15a0d-105">成員</span><span class="sxs-lookup"><span data-stu-id="15a0d-105">Members</span></span>  
  
|<span data-ttu-id="15a0d-106">成員</span><span class="sxs-lookup"><span data-stu-id="15a0d-106">Member</span></span>|<span data-ttu-id="15a0d-107">說明</span><span class="sxs-lookup"><span data-stu-id="15a0d-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="15a0d-108">指定偵錯工具應該一律讀取 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="15a0d-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="15a0d-109">指定偵錯工具應該唯讀取與完全信任元件相關聯的 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="15a0d-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="15a0d-110">指定偵錯工具絕對不應讀取 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="15a0d-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15a0d-111">備註</span><span class="sxs-lookup"><span data-stu-id="15a0d-111">Remarks</span></span>  
 <span data-ttu-id="15a0d-112">`ESymbolReadingPolicy`列舉會與[ICLRDebugManager：： SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md)方法搭配使用。</span><span class="sxs-lookup"><span data-stu-id="15a0d-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15a0d-113">需求</span><span class="sxs-lookup"><span data-stu-id="15a0d-113">Requirements</span></span>  
 <span data-ttu-id="15a0d-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15a0d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15a0d-115">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="15a0d-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15a0d-116">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="15a0d-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15a0d-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15a0d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a0d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15a0d-118">See also</span></span>

- [<span data-ttu-id="15a0d-119">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="15a0d-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
