---
title: GetErrorInfo 函式 （Unmanaged API 參考）
description: GetErrorInfo 函式會從先前的函式呼叫中擷取資訊時發生錯誤。
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2df4b87016394d1998ef90abe2e3eeb911886ef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217494"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="10567-103">GetErrorInfo 函式</span><span class="sxs-lookup"><span data-stu-id="10567-103">GetErrorInfo function</span></span>
<span data-ttu-id="10567-104">從上一個函式呼叫擷取錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="10567-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="10567-105">語法</span><span class="sxs-lookup"><span data-stu-id="10567-105">Syntax</span></span>  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="10567-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="10567-106">Return value</span></span>

<span data-ttu-id="10567-107">指標[IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)物件，如果函式呼叫成功，或`null`失敗。</span><span class="sxs-lookup"><span data-stu-id="10567-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="10567-108">備註</span><span class="sxs-lookup"><span data-stu-id="10567-108">Remarks</span></span>

<span data-ttu-id="10567-109">此函式會包裝在呼叫[IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)方法。</span><span class="sxs-lookup"><span data-stu-id="10567-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="10567-110">需求</span><span class="sxs-lookup"><span data-stu-id="10567-110">Requirements</span></span>  
 <span data-ttu-id="10567-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10567-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10567-112">**標頭：** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="10567-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="10567-113">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="10567-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10567-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10567-114">See also</span></span>

- [<span data-ttu-id="10567-115">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="10567-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
