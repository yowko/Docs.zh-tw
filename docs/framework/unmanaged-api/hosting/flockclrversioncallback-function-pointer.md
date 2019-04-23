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
ms.openlocfilehash: 8062ab151efc6175aa68cb0563cd2ad042ee9cd8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189049"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="24b5b-102">FLockClrVersionCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="24b5b-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="24b5b-103">函式的一般語言執行平台 (CLR) 呼叫，表示初始設定啟動或完成的點。</span><span class="sxs-lookup"><span data-stu-id="24b5b-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="24b5b-104">中已被取代此函式指標[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="24b5b-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24b5b-105">語法</span><span class="sxs-lookup"><span data-stu-id="24b5b-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="24b5b-106">備註</span><span class="sxs-lookup"><span data-stu-id="24b5b-106">Remarks</span></span>  
 <span data-ttu-id="24b5b-107">此函式是由主應用程式實作。</span><span class="sxs-lookup"><span data-stu-id="24b5b-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24b5b-108">需求</span><span class="sxs-lookup"><span data-stu-id="24b5b-108">Requirements</span></span>  
 <span data-ttu-id="24b5b-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="24b5b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24b5b-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="24b5b-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="24b5b-111">**LIBRARY:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="24b5b-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="24b5b-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24b5b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b5b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24b5b-113">See also</span></span>

- [<span data-ttu-id="24b5b-114">LockClrVersion 函式</span><span class="sxs-lookup"><span data-stu-id="24b5b-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="24b5b-115">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="24b5b-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
