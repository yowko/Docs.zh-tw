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
ms.openlocfilehash: 42ce1f02294db98c5c593a5f16de5226703d5f9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733707"
---
# <a name="esymbolreadingpolicy-enumeration"></a><span data-ttu-id="6e563-102">ESymbolReadingPolicy 列舉</span><span class="sxs-lookup"><span data-stu-id="6e563-102">ESymbolReadingPolicy Enumeration</span></span>

<span data-ttu-id="6e563-103">包含值，這些值會設定用來讀取程式資料庫 (PDB) 檔的原則。</span><span class="sxs-lookup"><span data-stu-id="6e563-103">Contains values that set the policy for reading program database (PDB) files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e563-104">語法</span><span class="sxs-lookup"><span data-stu-id="6e563-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="6e563-105">成員</span><span class="sxs-lookup"><span data-stu-id="6e563-105">Members</span></span>  
  
|<span data-ttu-id="6e563-106">member</span><span class="sxs-lookup"><span data-stu-id="6e563-106">Member</span></span>|<span data-ttu-id="6e563-107">描述</span><span class="sxs-lookup"><span data-stu-id="6e563-107">Description</span></span>|  
|------------|-----------------|  
|`eSymbolReadingAlways`|<span data-ttu-id="6e563-108">指定偵錯工具應一律讀取 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="6e563-108">Specifies that the debugger should always read PDB files.</span></span>|  
|`eSymbolReadingFullTrustOnly`|<span data-ttu-id="6e563-109">指定偵錯工具應該唯讀取與完全信任元件相關聯的 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="6e563-109">Specifies that the debugger should read only PDB files that are associated with full-trust assemblies.</span></span>|  
|`eSymbolReadingNever`|<span data-ttu-id="6e563-110">指定偵錯工具絕對不應讀取 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="6e563-110">Specifies that the debugger should never read PDB files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e563-111">備註</span><span class="sxs-lookup"><span data-stu-id="6e563-111">Remarks</span></span>  

 <span data-ttu-id="6e563-112">`ESymbolReadingPolicy`列舉會搭配[ICLRDebugManager：： SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md)方法使用。</span><span class="sxs-lookup"><span data-stu-id="6e563-112">The `ESymbolReadingPolicy` enumeration is used with the [ICLRDebugManager::SetSymbolReadingPolicy](iclrdebugmanager-setsymbolreadingpolicy-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e563-113">需求</span><span class="sxs-lookup"><span data-stu-id="6e563-113">Requirements</span></span>  

 <span data-ttu-id="6e563-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6e563-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e563-115">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6e563-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e563-116">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6e563-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e563-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e563-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e563-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e563-118">See also</span></span>

- [<span data-ttu-id="6e563-119">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="6e563-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
