---
title: VerifyClientKey 函式 （Unmanaged API 參考）
description: VerifyClientKey 函式可確保用戶端金鑰具有正確的安全性。
ms.date: 11/06/2017
api_name:
- VerifyClientKey
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- VerifyClientKey
helpviewer_keywords:
- VerifyClientKey function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4b51fe4510f4172227d9afd049eb6815790a165
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783093"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="28972-103">VerifyClientKey 函式</span><span class="sxs-lookup"><span data-stu-id="28972-103">VerifyClientKey function</span></span>
<span data-ttu-id="28972-104">確定用戶端金鑰有正確的安全性。</span><span class="sxs-lookup"><span data-stu-id="28972-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="28972-105">語法</span><span class="sxs-lookup"><span data-stu-id="28972-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="28972-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="28972-106">Return value</span></span>

<span data-ttu-id="28972-107">如果此函數成功，傳回的值是`ERROR_SUCCESS`(0)。</span><span class="sxs-lookup"><span data-stu-id="28972-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="28972-108">如果函式失敗，傳回值是中定義的非零的錯誤代碼*WinError.h*。</span><span class="sxs-lookup"><span data-stu-id="28972-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="28972-109">需求</span><span class="sxs-lookup"><span data-stu-id="28972-109">Requirements</span></span>  
 <span data-ttu-id="28972-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="28972-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28972-111">**標頭：** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="28972-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="28972-112">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="28972-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28972-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28972-113">See also</span></span>

- [<span data-ttu-id="28972-114">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="28972-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
