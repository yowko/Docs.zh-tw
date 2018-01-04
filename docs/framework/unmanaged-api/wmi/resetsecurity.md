---
title: "ResetSecurity 函式 （Unmanaged API 參考）"
description: "ResetSecurity 函式會模擬語彙基元指派給目前的執行緒。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ResetSecurity
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ResetSecurity
helpviewer_keywords: ResetSecurity function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bacee65633d25e705d978d3902a6804516a88bf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="resetsecurity-function"></a><span data-ttu-id="6a06a-103">ResetSecurity 函式</span><span class="sxs-lookup"><span data-stu-id="6a06a-103">ResetSecurity function</span></span>
<span data-ttu-id="6a06a-104">將提供的模擬語彙基元指派給目前的執行緒。</span><span class="sxs-lookup"><span data-stu-id="6a06a-104">Assigns the supplied impersonation token to the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="6a06a-105">語法</span><span class="sxs-lookup"><span data-stu-id="6a06a-105">Syntax</span></span>  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a><span data-ttu-id="6a06a-106">參數</span><span class="sxs-lookup"><span data-stu-id="6a06a-106">Parameters</span></span>

`token`  
<span data-ttu-id="6a06a-107">[in]與目前執行緒相關聯的模擬權杖。</span><span class="sxs-lookup"><span data-stu-id="6a06a-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="6a06a-108">其值可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="6a06a-108">Its value can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="6a06a-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6a06a-109">Return value</span></span>

<span data-ttu-id="6a06a-110">如果函式成功，傳回值是`S_OK`(0)。</span><span class="sxs-lookup"><span data-stu-id="6a06a-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="6a06a-111">如果函式失敗，傳回的值就會為非零的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="6a06a-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="6a06a-112">若要取得延伸錯誤資訊，請呼叫[GetErrorInfo](geterrorinfo.md)函式。</span><span class="sxs-lookup"><span data-stu-id="6a06a-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="6a06a-113">需求</span><span class="sxs-lookup"><span data-stu-id="6a06a-113">Requirements</span></span>  
 <span data-ttu-id="6a06a-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a06a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a06a-115">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6a06a-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6a06a-116">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6a06a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a06a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a06a-117">See also</span></span>  
[<span data-ttu-id="6a06a-118">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="6a06a-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
