---
title: 驗證用戶端金鑰功能（非託管 API 引用）
description: 驗證用戶端金鑰功能可確保用戶端金鑰具有正確的安全性。
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
ms.openlocfilehash: ebb794240494deb0c831b50e95461ec52017a215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176704"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="75641-103">驗證用戶端金鑰功能</span><span class="sxs-lookup"><span data-stu-id="75641-103">VerifyClientKey function</span></span>
<span data-ttu-id="75641-104">確定用戶端金鑰有正確的安全性。</span><span class="sxs-lookup"><span data-stu-id="75641-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="75641-105">語法</span><span class="sxs-lookup"><span data-stu-id="75641-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey();
```  

## <a name="return-value"></a><span data-ttu-id="75641-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="75641-106">Return value</span></span>

<span data-ttu-id="75641-107">如果函數成功，則傳回值為`ERROR_SUCCESS`（0）。</span><span class="sxs-lookup"><span data-stu-id="75641-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="75641-108">如果函數失敗，傳回值是在*WinError.h*中定義的非零錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="75641-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="75641-109">需求</span><span class="sxs-lookup"><span data-stu-id="75641-109">Requirements</span></span>  
 <span data-ttu-id="75641-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="75641-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75641-111">**標題：** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="75641-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="75641-112">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="75641-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75641-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75641-113">See also</span></span>

- [<span data-ttu-id="75641-114">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="75641-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
