---
title: "SetSecurity 函式 （Unmanaged API 參考）"
description: "SetSecurity 函式會擷取目前的執行緒模擬語彙基元。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- SetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SetSecurity
helpviewer_keywords:
- SetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: abb716d64bde9b298203e54d862ff4f1b2bcd170
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="setsecurity-function"></a><span data-ttu-id="ab241-103">SetSecurity 函式</span><span class="sxs-lookup"><span data-stu-id="ab241-103">SetSecurity function</span></span>
<span data-ttu-id="ab241-104">擷取與目前執行緒相關聯的模擬權杖。</span><span class="sxs-lookup"><span data-stu-id="ab241-104">Retrieves the impersonation token associated with the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ab241-105">語法</span><span class="sxs-lookup"><span data-stu-id="ab241-105">Syntax</span></span>  
  
```  
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```  

## <a name="parameters"></a><span data-ttu-id="ab241-106">參數</span><span class="sxs-lookup"><span data-stu-id="ab241-106">Parameters</span></span>

<span data-ttu-id="ab241-107">`pNeedToReset`[out]此函式傳回時，包含指標`boolean`，指出呼叫是否應重設語彙基元[ResetSecurity](resetsecurity.md)函式。</span><span class="sxs-lookup"><span data-stu-id="ab241-107">`pNeedToReset` [out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>  

`token`  
<span data-ttu-id="ab241-108">[out]此函式傳回時，包含與目前執行緒相關聯的模擬語彙基元的控制代碼的指標。</span><span class="sxs-lookup"><span data-stu-id="ab241-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="ab241-109">其值可以是`null`是否有任何與目前執行緒相關聯的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="ab241-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="ab241-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="ab241-110">Return value</span></span>

<span data-ttu-id="ab241-111">如果函式成功，傳回值是`S_OK`(0)。</span><span class="sxs-lookup"><span data-stu-id="ab241-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="ab241-112">如果函式失敗，傳回的值就會為非零的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ab241-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="ab241-113">若要取得延伸錯誤資訊，請呼叫[GetErrorInfo](geterrorinfo.md)函式。</span><span class="sxs-lookup"><span data-stu-id="ab241-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="ab241-114">需求</span><span class="sxs-lookup"><span data-stu-id="ab241-114">Requirements</span></span>  
 <span data-ttu-id="ab241-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab241-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab241-116">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ab241-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ab241-117">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ab241-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab241-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab241-118">See also</span></span>  
[<span data-ttu-id="ab241-119">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="ab241-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
