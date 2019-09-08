---
title: ResetSecurity 函式（非受控 API 參考）
description: ResetSecurity 函數會將模擬 token 指派給目前的執行緒。
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1636d7de8273389e785131dbc1145affd5d3b45f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798250"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="c9a54-103">ResetSecurity 函式</span><span class="sxs-lookup"><span data-stu-id="c9a54-103">ResetSecurity function</span></span>
<span data-ttu-id="c9a54-104">將提供的模擬權杖指派給目前的執行緒。</span><span class="sxs-lookup"><span data-stu-id="c9a54-104">Assigns the supplied impersonation token to the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="c9a54-105">語法</span><span class="sxs-lookup"><span data-stu-id="c9a54-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a><span data-ttu-id="c9a54-106">參數</span><span class="sxs-lookup"><span data-stu-id="c9a54-106">Parameters</span></span>

`token`  
<span data-ttu-id="c9a54-107">在要與目前線程產生關聯的模擬權杖。</span><span class="sxs-lookup"><span data-stu-id="c9a54-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="c9a54-108">其值可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="c9a54-108">Its value can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="c9a54-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="c9a54-109">Return value</span></span>

<span data-ttu-id="c9a54-110">如果函式成功，則傳回值為`S_OK` （0）。</span><span class="sxs-lookup"><span data-stu-id="c9a54-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="c9a54-111">如果函式失敗，則傳回值為非零的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c9a54-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="c9a54-112">若要取得擴充的錯誤資訊，請呼叫[GetErrorInfo](geterrorinfo.md)函式。</span><span class="sxs-lookup"><span data-stu-id="c9a54-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="c9a54-113">需求</span><span class="sxs-lookup"><span data-stu-id="c9a54-113">Requirements</span></span>  
 <span data-ttu-id="c9a54-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c9a54-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9a54-115">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c9a54-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c9a54-116">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c9a54-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9a54-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9a54-117">See also</span></span>

- [<span data-ttu-id="c9a54-118">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="c9a54-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
