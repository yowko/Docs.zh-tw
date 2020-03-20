---
title: 設置安全功能（非託管 API 引用）
description: SetSecurity 函數檢索當前執行緒的類比權杖。
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
ms.openlocfilehash: 809f6a95fdd6854b3a591b496877838c48d52199
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176730"
---
# <a name="setsecurity-function"></a><span data-ttu-id="396bb-103">SetSecurity 函式</span><span class="sxs-lookup"><span data-stu-id="396bb-103">SetSecurity function</span></span>

<span data-ttu-id="396bb-104">擷取與目前執行緒關聯的模擬權杖。</span><span class="sxs-lookup"><span data-stu-id="396bb-104">Retrieves the impersonation token associated with the current thread.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="396bb-105">語法</span><span class="sxs-lookup"><span data-stu-id="396bb-105">Syntax</span></span>

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset,
   [out] HANDLE* pCurrentThreadToken
);
```

## <a name="parameters"></a><span data-ttu-id="396bb-106">參數</span><span class="sxs-lookup"><span data-stu-id="396bb-106">Parameters</span></span>

`pNeedToReset`\
<span data-ttu-id="396bb-107">[出]當函數返回時，包含指向 的`boolean`指標，指示是否應通過調用[ResetSecurity](resetsecurity.md)函數重置權杖。</span><span class="sxs-lookup"><span data-stu-id="396bb-107">[out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>

`token`\
<span data-ttu-id="396bb-108">[出]當函數返回時，包含指向與當前執行緒關聯的類比權杖控制碼的指標。</span><span class="sxs-lookup"><span data-stu-id="396bb-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="396bb-109">如果沒有與當前執行緒`null`關聯的權杖，則其值可以是。</span><span class="sxs-lookup"><span data-stu-id="396bb-109">Its value can be `null` if there is no token associated with the current thread.</span></span>

## <a name="return-value"></a><span data-ttu-id="396bb-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="396bb-110">Return value</span></span>

<span data-ttu-id="396bb-111">如果函數成功，則傳回值為`S_OK`（0）。</span><span class="sxs-lookup"><span data-stu-id="396bb-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="396bb-112">如果函數失敗，傳回值是非零錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="396bb-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="396bb-113">要獲取擴展的錯誤資訊，請致電[GetErrorInfo](geterrorinfo.md)函數。</span><span class="sxs-lookup"><span data-stu-id="396bb-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="396bb-114">需求</span><span class="sxs-lookup"><span data-stu-id="396bb-114">Requirements</span></span>

 <span data-ttu-id="396bb-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="396bb-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="396bb-116">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="396bb-116">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="396bb-117">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="396bb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="396bb-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="396bb-118">See also</span></span>

- [<span data-ttu-id="396bb-119">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="396bb-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
