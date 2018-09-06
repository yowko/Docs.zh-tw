---
title: EndMethodEnumeration 函式 （Unmanaged API 參考）
description: EndMethodEnumeration 函式會終止方法列舉型別序列。
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 42ee188c2a622d0bed2985e56e49997d2934686f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873298"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="fb8f4-103">EndMethodEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="fb8f4-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="fb8f4-104">結束藉由呼叫啟動列舉順序[BeginMethodEnumeration 函式](beginmethodenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="fb8f4-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="fb8f4-105">語法</span><span class="sxs-lookup"><span data-stu-id="fb8f4-105">Syntax</span></span>  
  
```  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="fb8f4-106">參數</span><span class="sxs-lookup"><span data-stu-id="fb8f4-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="fb8f4-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="fb8f4-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="fb8f4-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="fb8f4-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="fb8f4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="fb8f4-109">Return value</span></span>

<span data-ttu-id="fb8f4-110">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="fb8f4-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="fb8f4-111">常數</span><span class="sxs-lookup"><span data-stu-id="fb8f4-111">Constant</span></span>  |<span data-ttu-id="fb8f4-112">值</span><span class="sxs-lookup"><span data-stu-id="fb8f4-112">Value</span></span>  |<span data-ttu-id="fb8f4-113">描述</span><span class="sxs-lookup"><span data-stu-id="fb8f4-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="fb8f4-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="fb8f4-114">0x8004101d</span></span> | <span data-ttu-id="fb8f4-115">發生內部錯誤。</span><span class="sxs-lookup"><span data-stu-id="fb8f4-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="fb8f4-116">0</span><span class="sxs-lookup"><span data-stu-id="fb8f4-116">0</span></span> | <span data-ttu-id="fb8f4-117">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="fb8f4-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="fb8f4-118">備註</span><span class="sxs-lookup"><span data-stu-id="fb8f4-118">Remarks</span></span>

<span data-ttu-id="fb8f4-119">此函式會包裝在呼叫[IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration)方法。</span><span class="sxs-lookup"><span data-stu-id="fb8f4-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="fb8f4-120">呼叫端會列舉序列使用開始[BeginMethodEnumeration 函式](beginmethodenumeration.md)，然後再呼叫[NextMethod 函式](nextmethod.md )直到該方法傳回`WBEM_S_NO_MORE_DATA`。</span><span class="sxs-lookup"><span data-stu-id="fb8f4-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="fb8f4-121">（選擇性） 藉由呼叫完成序列的呼叫端`EndMethodEnumeration`。</span><span class="sxs-lookup"><span data-stu-id="fb8f4-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="fb8f4-122">呼叫端可能會提早終止列舉型別，藉由呼叫`EndMethodEnumeration`在任何時間。</span><span class="sxs-lookup"><span data-stu-id="fb8f4-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="fb8f4-123">需求</span><span class="sxs-lookup"><span data-stu-id="fb8f4-123">Requirements</span></span>  
 <span data-ttu-id="fb8f4-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fb8f4-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb8f4-125">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="fb8f4-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="fb8f4-126">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fb8f4-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb8f4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb8f4-127">See also</span></span>  
[<span data-ttu-id="fb8f4-128">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="fb8f4-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
