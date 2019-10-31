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
ms.openlocfilehash: f1ad414c30788801e14a33e98a0893e2a0f58d0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136510"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="29d2a-102">FLockClrVersionCallback 函式指標</span><span class="sxs-lookup"><span data-stu-id="29d2a-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="29d2a-103">指向 common language runtime （CLR）呼叫的函式，表示初始化已啟動或已完成。</span><span class="sxs-lookup"><span data-stu-id="29d2a-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="29d2a-104">這個函式指標在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="29d2a-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29d2a-105">語法</span><span class="sxs-lookup"><span data-stu-id="29d2a-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="29d2a-106">備註</span><span class="sxs-lookup"><span data-stu-id="29d2a-106">Remarks</span></span>  
 <span data-ttu-id="29d2a-107">此函式是由主機所執行。</span><span class="sxs-lookup"><span data-stu-id="29d2a-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29d2a-108">需求</span><span class="sxs-lookup"><span data-stu-id="29d2a-108">Requirements</span></span>  
 <span data-ttu-id="29d2a-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29d2a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29d2a-110">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="29d2a-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29d2a-111">連結**庫：** Mscorwks.dll .dll</span><span class="sxs-lookup"><span data-stu-id="29d2a-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="29d2a-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29d2a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d2a-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="29d2a-113">See also</span></span>

- [<span data-ttu-id="29d2a-114">LockClrVersion 函式</span><span class="sxs-lookup"><span data-stu-id="29d2a-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="29d2a-115">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="29d2a-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
