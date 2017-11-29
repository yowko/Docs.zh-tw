---
title: "WAITORTIMERCALLBACK 函式指標"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: WAITORTIMERCALLBACK
api_location: mscoree.dll
api_type: COM
f1_keywords: WAITORTIMERCALLBACK
helpviewer_keywords: WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 873d2ff489085ec2a0c37be2feeb3e15f61c9227
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="84af5-102">WAITORTIMERCALLBACK 函式指標</span><span class="sxs-lookup"><span data-stu-id="84af5-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="84af5-103">指向 通知的主應用程式等候處理的函式 (<xref:System.Threading.WaitHandle>) 已收到信號或逾時。</span><span class="sxs-lookup"><span data-stu-id="84af5-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="84af5-104">此函式指標中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="84af5-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84af5-105">語法</span><span class="sxs-lookup"><span data-stu-id="84af5-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84af5-106">參數</span><span class="sxs-lookup"><span data-stu-id="84af5-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="84af5-107">[in]包含由主應用程式定義資訊的物件指標。</span><span class="sxs-lookup"><span data-stu-id="84af5-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="84af5-108">[in]`true`如果逾時等候控制代碼，或`false`如果接獲訊號。</span><span class="sxs-lookup"><span data-stu-id="84af5-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84af5-109">備註</span><span class="sxs-lookup"><span data-stu-id="84af5-109">Remarks</span></span>  
 <span data-ttu-id="84af5-110">函式`WAITORTIMERCALLBACK`點是回呼函式，而且必須在裝載應用程式寫入器實作。</span><span class="sxs-lookup"><span data-stu-id="84af5-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84af5-111">需求</span><span class="sxs-lookup"><span data-stu-id="84af5-111">Requirements</span></span>  
 <span data-ttu-id="84af5-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84af5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84af5-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="84af5-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84af5-114">**程式庫：** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="84af5-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="84af5-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84af5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84af5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84af5-116">See Also</span></span>  
 [<span data-ttu-id="84af5-117">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="84af5-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
