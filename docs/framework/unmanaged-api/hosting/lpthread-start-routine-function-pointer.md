---
title: "LPTHREAD_START_ROUTINE 函式指標"
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
- LPTHREAD_START_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPTHREAD_START_ROUTINE
helpviewer_keywords:
- LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d28cdbfa2cb6c2c1f6b730e34b623a621119bc3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="lpthreadstartroutine-function-pointer"></a><span data-ttu-id="ab9e5-102">LPTHREAD_START_ROUTINE 函式指標</span><span class="sxs-lookup"><span data-stu-id="ab9e5-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="ab9e5-103">指向以通知主機在執行緒已開始執行的函式。</span><span class="sxs-lookup"><span data-stu-id="ab9e5-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="ab9e5-104">此函式指標中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ab9e5-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab9e5-105">語法</span><span class="sxs-lookup"><span data-stu-id="ab9e5-105">Syntax</span></span>  
  
```  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab9e5-106">參數</span><span class="sxs-lookup"><span data-stu-id="ab9e5-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="ab9e5-107">[in]已開始執行的程式碼之指標。</span><span class="sxs-lookup"><span data-stu-id="ab9e5-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab9e5-108">備註</span><span class="sxs-lookup"><span data-stu-id="ab9e5-108">Remarks</span></span>  
 <span data-ttu-id="ab9e5-109">函式`LPTHREAD_START_ROUTINE`點是回呼函式，而且必須在裝載應用程式寫入器實作。</span><span class="sxs-lookup"><span data-stu-id="ab9e5-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab9e5-110">需求</span><span class="sxs-lookup"><span data-stu-id="ab9e5-110">Requirements</span></span>  
 <span data-ttu-id="ab9e5-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab9e5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab9e5-112">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ab9e5-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ab9e5-113">**程式庫：** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="ab9e5-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="ab9e5-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab9e5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab9e5-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="ab9e5-115">See Also</span></span>  
 [<span data-ttu-id="ab9e5-116">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="ab9e5-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
