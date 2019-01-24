---
title: SpawnDerivedClass 函式 （Unmanaged API 參考）
description: SpawnDerivedClass 函式會建立新的物件衍生自物件。
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99b996cf848de968d71cc1d325d3bbda7bd5386f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715548"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="5c655-103">SpawnDerivedClass 函式</span><span class="sxs-lookup"><span data-stu-id="5c655-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="5c655-104">從指定的物件建立新的衍生類別物件。</span><span class="sxs-lookup"><span data-stu-id="5c655-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5c655-105">語法</span><span class="sxs-lookup"><span data-stu-id="5c655-105">Syntax</span></span>  
  
```  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="5c655-106">參數</span><span class="sxs-lookup"><span data-stu-id="5c655-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5c655-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="5c655-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="5c655-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="5c655-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="5c655-109">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="5c655-109">[in] Reserved.</span></span> <span data-ttu-id="5c655-110">這個參數必須是 0。</span><span class="sxs-lookup"><span data-stu-id="5c655-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="5c655-111">[out]接收新的類別定義物件的指標。</span><span class="sxs-lookup"><span data-stu-id="5c655-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="5c655-112">發生錯誤時，新的物件不是傳回，和`ppNewClass`左未經修改。</span><span class="sxs-lookup"><span data-stu-id="5c655-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="5c655-113">其值不能是`null`。</span><span class="sxs-lookup"><span data-stu-id="5c655-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="5c655-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="5c655-114">Return value</span></span>

<span data-ttu-id="5c655-115">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="5c655-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5c655-116">常數</span><span class="sxs-lookup"><span data-stu-id="5c655-116">Constant</span></span>  |<span data-ttu-id="5c655-117">值</span><span class="sxs-lookup"><span data-stu-id="5c655-117">Value</span></span>  |<span data-ttu-id="5c655-118">描述</span><span class="sxs-lookup"><span data-stu-id="5c655-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="5c655-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5c655-119">0x80041001</span></span> | <span data-ttu-id="5c655-120">已有一般失敗。</span><span class="sxs-lookup"><span data-stu-id="5c655-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="5c655-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="5c655-121">0x80041016</span></span> | <span data-ttu-id="5c655-122">無效的作業，例如產生類別的執行個體中，已要求。</span><span class="sxs-lookup"><span data-stu-id="5c655-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="5c655-123">不完全的來源類別已定義，或向 Windows 管理，因此不允許新的衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="5c655-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5c655-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5c655-124">0x80041006</span></span> | <span data-ttu-id="5c655-125">沒有足夠的記憶體可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="5c655-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5c655-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5c655-126">0x80041008</span></span> | <span data-ttu-id="5c655-127">`ppNewClass` 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="5c655-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="5c655-128">0</span><span class="sxs-lookup"><span data-stu-id="5c655-128">0</span></span> | <span data-ttu-id="5c655-129">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="5c655-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5c655-130">備註</span><span class="sxs-lookup"><span data-stu-id="5c655-130">Remarks</span></span>

<span data-ttu-id="5c655-131">此函式會包裝在呼叫[IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)方法。</span><span class="sxs-lookup"><span data-stu-id="5c655-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="5c655-132">`ptr` 必須是變成繁衍 （spawn） 物件的父類別的類別定義。</span><span class="sxs-lookup"><span data-stu-id="5c655-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="5c655-133">傳回的物件會變成目前物件的子類別。</span><span class="sxs-lookup"><span data-stu-id="5c655-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="5c655-134">新的物件中傳回`ppNewClass`會自動變成目前物件的子類別。</span><span class="sxs-lookup"><span data-stu-id="5c655-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="5c655-135">無法覆寫這個行為。</span><span class="sxs-lookup"><span data-stu-id="5c655-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="5c655-136">沒有任何其他子類別 （衍生類別） 可以建立的方法。</span><span class="sxs-lookup"><span data-stu-id="5c655-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="5c655-137">需求</span><span class="sxs-lookup"><span data-stu-id="5c655-137">Requirements</span></span>  
 <span data-ttu-id="5c655-138">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c655-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c655-139">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5c655-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5c655-140">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5c655-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c655-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c655-141">See also</span></span>
- [<span data-ttu-id="5c655-142">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="5c655-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
