---
title: WAITORTIMERCALLBACK 函式指標
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1455ce7c3b07809d1dead8e98019c991475eb02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442143"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="47cac-102">WAITORTIMERCALLBACK 函式指標</span><span class="sxs-lookup"><span data-stu-id="47cac-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="47cac-103">指向 通知的主應用程式等候處理的函式 (<xref:System.Threading.WaitHandle>) 已收到信號或逾時。</span><span class="sxs-lookup"><span data-stu-id="47cac-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="47cac-104">此函式指標中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="47cac-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47cac-105">語法</span><span class="sxs-lookup"><span data-stu-id="47cac-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47cac-106">參數</span><span class="sxs-lookup"><span data-stu-id="47cac-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="47cac-107">[in]包含由主應用程式定義資訊的物件指標。</span><span class="sxs-lookup"><span data-stu-id="47cac-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="47cac-108">[in]`true`如果逾時等候控制代碼，或`false`如果接獲訊號。</span><span class="sxs-lookup"><span data-stu-id="47cac-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47cac-109">備註</span><span class="sxs-lookup"><span data-stu-id="47cac-109">Remarks</span></span>  
 <span data-ttu-id="47cac-110">函式`WAITORTIMERCALLBACK`點是回呼函式，而且必須在裝載應用程式寫入器實作。</span><span class="sxs-lookup"><span data-stu-id="47cac-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47cac-111">需求</span><span class="sxs-lookup"><span data-stu-id="47cac-111">Requirements</span></span>  
 <span data-ttu-id="47cac-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="47cac-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47cac-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="47cac-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="47cac-114">**程式庫：** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="47cac-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="47cac-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47cac-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47cac-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47cac-116">See Also</span></span>  
 [<span data-ttu-id="47cac-117">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="47cac-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
