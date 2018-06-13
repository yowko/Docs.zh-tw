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
ms.openlocfilehash: ea8a74633d3e950f6cf7ba87c00a9efa45206545
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459560"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="bb6b7-103">VerifyClientKey 函式</span><span class="sxs-lookup"><span data-stu-id="bb6b7-103">VerifyClientKey function</span></span>
<span data-ttu-id="bb6b7-104">可確保用戶端金鑰具有正確的安全性。</span><span class="sxs-lookup"><span data-stu-id="bb6b7-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="bb6b7-105">語法</span><span class="sxs-lookup"><span data-stu-id="bb6b7-105">Syntax</span></span>  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="bb6b7-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="bb6b7-106">Return value</span></span>

<span data-ttu-id="bb6b7-107">如果函式成功，傳回值是`ERROR_SUCCESS`(0)。</span><span class="sxs-lookup"><span data-stu-id="bb6b7-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="bb6b7-108">如果函式失敗，傳回值是中定義的非零的錯誤代碼*WinError.h*。</span><span class="sxs-lookup"><span data-stu-id="bb6b7-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="bb6b7-109">需求</span><span class="sxs-lookup"><span data-stu-id="bb6b7-109">Requirements</span></span>  
 <span data-ttu-id="bb6b7-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb6b7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb6b7-111">**標頭：** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="bb6b7-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="bb6b7-112">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bb6b7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb6b7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb6b7-113">See also</span></span>  
[<span data-ttu-id="bb6b7-114">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="bb6b7-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
