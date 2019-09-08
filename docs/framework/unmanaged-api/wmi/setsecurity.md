---
title: SetSecurity 函式（非受控 API 參考）
description: SetSecurity 函數會抓取目前線程的模擬 token。
ms.date: 11/06/2017
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
ms.openlocfilehash: 94c76213acb66116105d181e9961a33976047ee7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798245"
---
# <a name="setsecurity-function"></a><span data-ttu-id="0777a-103">SetSecurity 函式</span><span class="sxs-lookup"><span data-stu-id="0777a-103">SetSecurity function</span></span>

<span data-ttu-id="0777a-104">擷取與目前執行緒關聯的模擬權杖。</span><span class="sxs-lookup"><span data-stu-id="0777a-104">Retrieves the impersonation token associated with the current thread.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0777a-105">語法</span><span class="sxs-lookup"><span data-stu-id="0777a-105">Syntax</span></span>

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```

## <a name="parameters"></a><span data-ttu-id="0777a-106">參數</span><span class="sxs-lookup"><span data-stu-id="0777a-106">Parameters</span></span>

`pNeedToReset`\
<span data-ttu-id="0777a-107">脫銷當函式傳回時，會包含的指標`boolean` ，指出是否應該藉由呼叫[ResetSecurity](resetsecurity.md)函式來重設權杖。</span><span class="sxs-lookup"><span data-stu-id="0777a-107">[out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>

`token`\
<span data-ttu-id="0777a-108">脫銷當函式傳回時，會包含與目前線程相關聯之模擬標記的控制碼指標。</span><span class="sxs-lookup"><span data-stu-id="0777a-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="0777a-109">如果沒有與目前`null`執行緒相關聯的 token，其值可以是。</span><span class="sxs-lookup"><span data-stu-id="0777a-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="0777a-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="0777a-110">Return value</span></span>

<span data-ttu-id="0777a-111">如果函式成功，則傳回值為`S_OK` （0）。</span><span class="sxs-lookup"><span data-stu-id="0777a-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="0777a-112">如果函式失敗，則傳回值為非零的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="0777a-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="0777a-113">若要取得擴充的錯誤資訊，請呼叫[GetErrorInfo](geterrorinfo.md)函式。</span><span class="sxs-lookup"><span data-stu-id="0777a-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="0777a-114">需求</span><span class="sxs-lookup"><span data-stu-id="0777a-114">Requirements</span></span>

 <span data-ttu-id="0777a-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0777a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="0777a-116">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0777a-116">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="0777a-117">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0777a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0777a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0777a-118">See also</span></span>

- [<span data-ttu-id="0777a-119">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="0777a-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
