---
title: "GetErrorInfo 函式 （Unmanaged API 參考）"
description: "GetErrorInfo 函式會從先前的函式呼叫擷取資訊時發生錯誤。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetErrorInfo
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetErrorInfo
helpviewer_keywords: GetErrorInfo function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1bdaa72723855c6688a7c8c7704b958f6196dfd
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="5eb2d-103">GetErrorInfo 函式</span><span class="sxs-lookup"><span data-stu-id="5eb2d-103">GetErrorInfo function</span></span>
<span data-ttu-id="5eb2d-104">從先前的函式呼叫中擷取資訊時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="5eb2d-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5eb2d-105">語法</span><span class="sxs-lookup"><span data-stu-id="5eb2d-105">Syntax</span></span>  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="5eb2d-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="5eb2d-106">Return value</span></span>

<span data-ttu-id="5eb2d-107">指標[IErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms221233(v=vs.85).aspx)物件，如果函式呼叫成功，或`null`失敗時。</span><span class="sxs-lookup"><span data-stu-id="5eb2d-107">An pointer to an [IErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms221233(v=vs.85).aspx) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="5eb2d-108">備註</span><span class="sxs-lookup"><span data-stu-id="5eb2d-108">Remarks</span></span>

<span data-ttu-id="5eb2d-109">此函式會包裝呼叫[IComThreadingInfo::GetErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="5eb2d-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5eb2d-110">需求</span><span class="sxs-lookup"><span data-stu-id="5eb2d-110">Requirements</span></span>  
 <span data-ttu-id="5eb2d-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5eb2d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5eb2d-112">**標頭：** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="5eb2d-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="5eb2d-113">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5eb2d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eb2d-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="5eb2d-114">See also</span></span>  
[<span data-ttu-id="5eb2d-115">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="5eb2d-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
