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
ms.openlocfilehash: 46e3356df6578f2adf2ceee00b1363b65fd014ea
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760236"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="6c617-102">FLockClrVersionCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="6c617-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="6c617-103">函式的一般語言執行平台 (CLR) 呼叫，表示初始設定啟動或完成的點。</span><span class="sxs-lookup"><span data-stu-id="6c617-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="6c617-104">在.NET Framework 4 中，已被取代此函式指標。</span><span class="sxs-lookup"><span data-stu-id="6c617-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c617-105">語法</span><span class="sxs-lookup"><span data-stu-id="6c617-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="6c617-106">備註</span><span class="sxs-lookup"><span data-stu-id="6c617-106">Remarks</span></span>  
 <span data-ttu-id="6c617-107">此函式是由主應用程式實作。</span><span class="sxs-lookup"><span data-stu-id="6c617-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c617-108">需求</span><span class="sxs-lookup"><span data-stu-id="6c617-108">Requirements</span></span>  
 <span data-ttu-id="6c617-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c617-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c617-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6c617-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c617-111">**LIBRARY:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="6c617-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="6c617-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c617-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c617-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c617-113">See also</span></span>

- [<span data-ttu-id="6c617-114">LockClrVersion 函式</span><span class="sxs-lookup"><span data-stu-id="6c617-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="6c617-115">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="6c617-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
