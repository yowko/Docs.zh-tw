---
title: 'GetErrorInfo 函式 (非受控 API 參考) '
description: GetErrorInfo 函式會從先前的函式呼叫中抓取錯誤資訊。
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
ms.openlocfilehash: 9a80c0b5522113e704336cda29362a0406077931
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553671"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="0e71c-103">GetErrorInfo 函式</span><span class="sxs-lookup"><span data-stu-id="0e71c-103">GetErrorInfo function</span></span>
<span data-ttu-id="0e71c-104">從上一個函式呼叫擷取錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="0e71c-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="0e71c-105">語法</span><span class="sxs-lookup"><span data-stu-id="0e71c-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a><span data-ttu-id="0e71c-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="0e71c-106">Return value</span></span>

<span data-ttu-id="0e71c-107">如果函式呼叫成功，則為 [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) 物件的指標，如果失敗，則為 `null` 。</span><span class="sxs-lookup"><span data-stu-id="0e71c-107">An pointer to an [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="0e71c-108">備註</span><span class="sxs-lookup"><span data-stu-id="0e71c-108">Remarks</span></span>

<span data-ttu-id="0e71c-109">此函數會包裝對 [IComThreadingInfo：： GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="0e71c-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="0e71c-110">需求</span><span class="sxs-lookup"><span data-stu-id="0e71c-110">Requirements</span></span>  
 <span data-ttu-id="0e71c-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0e71c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e71c-112">**標頭：** WMINet_Utils .def</span><span class="sxs-lookup"><span data-stu-id="0e71c-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="0e71c-113">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0e71c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e71c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e71c-114">See also</span></span>

- [<span data-ttu-id="0e71c-115">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="0e71c-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
