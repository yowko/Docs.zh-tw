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
ms.openlocfilehash: 0a0680651eb192e2798ede00048599c5130e63f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107354"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="fe219-103">VerifyClientKey 函式</span><span class="sxs-lookup"><span data-stu-id="fe219-103">VerifyClientKey function</span></span>
<span data-ttu-id="fe219-104">確定用戶端金鑰有正確的安全性。</span><span class="sxs-lookup"><span data-stu-id="fe219-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="fe219-105">語法</span><span class="sxs-lookup"><span data-stu-id="fe219-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="fe219-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="fe219-106">Return value</span></span>

<span data-ttu-id="fe219-107">如果函式成功，則傳回值會是 `ERROR_SUCCESS` （0）。</span><span class="sxs-lookup"><span data-stu-id="fe219-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="fe219-108">如果函式失敗，則傳回值為*winerror.h*中定義的非零錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="fe219-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="fe219-109">需求</span><span class="sxs-lookup"><span data-stu-id="fe219-109">Requirements</span></span>  
 <span data-ttu-id="fe219-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fe219-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe219-111">**標頭：** WMINet_Utils .def</span><span class="sxs-lookup"><span data-stu-id="fe219-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="fe219-112">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fe219-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe219-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe219-113">See also</span></span>

- [<span data-ttu-id="fe219-114">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="fe219-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
