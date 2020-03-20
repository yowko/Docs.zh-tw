---
title: GetErrorInfo 函數（非託管 API 引用）
description: GetErrorInfo 函數從上一個函式呼叫中檢索錯誤資訊。
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
ms.openlocfilehash: 802ee66a5be213ac7a599b193ec6de589773ea17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176808"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="9461b-103">GetErrorInfo 函式</span><span class="sxs-lookup"><span data-stu-id="9461b-103">GetErrorInfo function</span></span>
<span data-ttu-id="9461b-104">從上一個函式呼叫擷取錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="9461b-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9461b-105">語法</span><span class="sxs-lookup"><span data-stu-id="9461b-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a><span data-ttu-id="9461b-106">傳回值</span><span class="sxs-lookup"><span data-stu-id="9461b-106">Return value</span></span>

<span data-ttu-id="9461b-107">如果函式呼叫成功或`null`失敗，則指向[IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)物件的指標。</span><span class="sxs-lookup"><span data-stu-id="9461b-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="9461b-108">備註</span><span class="sxs-lookup"><span data-stu-id="9461b-108">Remarks</span></span>

<span data-ttu-id="9461b-109">此函數包裝對[IComThreadingInfo 的調用：：GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)方法。</span><span class="sxs-lookup"><span data-stu-id="9461b-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9461b-110">需求</span><span class="sxs-lookup"><span data-stu-id="9461b-110">Requirements</span></span>  
 <span data-ttu-id="9461b-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9461b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9461b-112">**標題：** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="9461b-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="9461b-113">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9461b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9461b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9461b-114">See also</span></span>

- [<span data-ttu-id="9461b-115">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="9461b-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
