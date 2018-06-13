---
title: FLockClrVersionCallback 函式指標
ms.date: 03/30/2017
api_name:
- FLockClrVersionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FLockClrVersionCallback
helpviewer_keywords:
- FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c884d07fa35c053b1a3b65c04426ac0e3712621
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429669"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="7161f-102">FLockClrVersionCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="7161f-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="7161f-103">指向以 common language runtime (CLR) 呼叫表示初始設定已啟動，或是已完成的函式。</span><span class="sxs-lookup"><span data-stu-id="7161f-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="7161f-104">此函式指標中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7161f-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7161f-105">語法</span><span class="sxs-lookup"><span data-stu-id="7161f-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="7161f-106">備註</span><span class="sxs-lookup"><span data-stu-id="7161f-106">Remarks</span></span>  
 <span data-ttu-id="7161f-107">此函式是由主機實作。</span><span class="sxs-lookup"><span data-stu-id="7161f-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7161f-108">需求</span><span class="sxs-lookup"><span data-stu-id="7161f-108">Requirements</span></span>  
 <span data-ttu-id="7161f-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7161f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7161f-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7161f-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7161f-111">**程式庫：** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="7161f-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="7161f-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7161f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7161f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7161f-113">See Also</span></span>  
 [<span data-ttu-id="7161f-114">LockClrVersion 函式</span><span class="sxs-lookup"><span data-stu-id="7161f-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 [<span data-ttu-id="7161f-115">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="7161f-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
