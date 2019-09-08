---
title: VerifyClientKey 函式（非受控 API 參考）
description: VerifyClientKey 函數可確保用戶端金鑰具有正確的安全性。
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
ms.openlocfilehash: b674e959ab93cf76b84e2af41e875a50b7d115f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798185"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="e0f74-103">VerifyClientKey 函式</span><span class="sxs-lookup"><span data-stu-id="e0f74-103">VerifyClientKey function</span></span>
<span data-ttu-id="e0f74-104">確定用戶端金鑰有正確的安全性。</span><span class="sxs-lookup"><span data-stu-id="e0f74-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e0f74-105">語法</span><span class="sxs-lookup"><span data-stu-id="e0f74-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="e0f74-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="e0f74-106">Return value</span></span>

<span data-ttu-id="e0f74-107">如果函式成功，則傳回值為`ERROR_SUCCESS` （0）。</span><span class="sxs-lookup"><span data-stu-id="e0f74-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="e0f74-108">如果函式失敗，則傳回值為*winerror.h*中定義的非零錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e0f74-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="e0f74-109">需求</span><span class="sxs-lookup"><span data-stu-id="e0f74-109">Requirements</span></span>  
 <span data-ttu-id="e0f74-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0f74-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0f74-111">**標頭：** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="e0f74-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="e0f74-112">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e0f74-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f74-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0f74-113">See also</span></span>

- [<span data-ttu-id="e0f74-114">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="e0f74-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
