---
title: Initialize 函式 （Unmanaged API 參考）
description: Initialize 函式會執行 WMI 初始化。
ms.date: 11/06/2017
api_name:
- Initialize
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Initialize
helpviewer_keywords:
- Initialize function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca8e87157a7adf45f35608aeba1067f2d66c8972
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081602"
---
# <a name="initialize-function"></a><span data-ttu-id="533ae-103">Initialize 函式</span><span class="sxs-lookup"><span data-stu-id="533ae-103">Initialize function</span></span>
<span data-ttu-id="533ae-104">執行 WMI 初始化。</span><span class="sxs-lookup"><span data-stu-id="533ae-104">Performs WMI initialization.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="533ae-105">語法</span><span class="sxs-lookup"><span data-stu-id="533ae-105">Syntax</span></span> 
```  
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
); 
```  
## <a name="parameters"></a><span data-ttu-id="533ae-106">參數</span><span class="sxs-lookup"><span data-stu-id="533ae-106">Parameters</span></span>

`bAllowIManagementObjectQI`   
<span data-ttu-id="533ae-107">[in]`true`來表示允許 WMI 物件上的呼叫 QueryInterface;`false`否則。</span><span class="sxs-lookup"><span data-stu-id="533ae-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="533ae-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="533ae-108">Return value</span></span>

<span data-ttu-id="533ae-109">此函數永遠會傳回`S_OK`(0)。</span><span class="sxs-lookup"><span data-stu-id="533ae-109">The function always returns `S_OK` (0).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="533ae-110">需求</span><span class="sxs-lookup"><span data-stu-id="533ae-110">Requirements</span></span>  
 <span data-ttu-id="533ae-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="533ae-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="533ae-112">**標頭：** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="533ae-112">**Header:** WMINet_Utils.def</span></span>  
  
 **<span data-ttu-id="533ae-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="533ae-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="533ae-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="533ae-114">See also</span></span>

- [<span data-ttu-id="533ae-115">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="533ae-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
