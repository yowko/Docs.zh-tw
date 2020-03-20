---
title: 重置安全功能（非託管 API 引用）
description: 重置安全功能將類比權杖分配給當前執行緒。
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
ms.openlocfilehash: ce74494455c6cc7fe382a4ea4ef2ff0c4e98c61b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174858"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="638e1-103">ResetSecurity 函式</span><span class="sxs-lookup"><span data-stu-id="638e1-103">ResetSecurity function</span></span>
<span data-ttu-id="638e1-104">將提供的模擬權杖指派給目前的執行緒。</span><span class="sxs-lookup"><span data-stu-id="638e1-104">Assigns the supplied impersonation token to the current thread.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="638e1-105">語法</span><span class="sxs-lookup"><span data-stu-id="638e1-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
);
```  

## <a name="parameters"></a><span data-ttu-id="638e1-106">參數</span><span class="sxs-lookup"><span data-stu-id="638e1-106">Parameters</span></span>

`token`  
<span data-ttu-id="638e1-107">[在]要與當前執行緒關聯的類比權杖。</span><span class="sxs-lookup"><span data-stu-id="638e1-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="638e1-108">其值可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="638e1-108">Its value can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="638e1-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="638e1-109">Return value</span></span>

<span data-ttu-id="638e1-110">如果函數成功，則傳回值為`S_OK`（0）。</span><span class="sxs-lookup"><span data-stu-id="638e1-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="638e1-111">如果函數失敗，傳回值是非零錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="638e1-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="638e1-112">要獲取擴展的錯誤資訊，請致電[GetErrorInfo](geterrorinfo.md)函數。</span><span class="sxs-lookup"><span data-stu-id="638e1-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="638e1-113">需求</span><span class="sxs-lookup"><span data-stu-id="638e1-113">Requirements</span></span>  
 <span data-ttu-id="638e1-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="638e1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="638e1-115">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="638e1-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="638e1-116">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="638e1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="638e1-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="638e1-117">See also</span></span>

- [<span data-ttu-id="638e1-118">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="638e1-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
