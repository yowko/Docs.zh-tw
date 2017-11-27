---
title: "刪除函式 （Unmanaged API 參考）"
description: "Delete 函式會刪除指定的屬性和所有其限定詞的 CIM 類別定義中。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Delete
helpviewer_keywords: Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f32487d2bd59bd76acdc32218c6bb0842de20e87
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="delete-function"></a><span data-ttu-id="b165e-103">刪除函式</span><span class="sxs-lookup"><span data-stu-id="b165e-103">Delete function</span></span>
<span data-ttu-id="b165e-104">刪除指定的屬性和所有其限定詞的 CIM 類別定義中。</span><span class="sxs-lookup"><span data-stu-id="b165e-104">Deletes the specified property and all of its qualifiers from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="b165e-105">語法</span><span class="sxs-lookup"><span data-stu-id="b165e-105">Syntax</span></span>  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="b165e-106">參數</span><span class="sxs-lookup"><span data-stu-id="b165e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b165e-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="b165e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b165e-108">[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="b165e-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="b165e-109">[in]要刪除之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="b165e-109">[in] The name of the property to delete.</span></span> <span data-ttu-id="b165e-110">`wszName`必須是有效的指標`LPCWSTR`。</span><span class="sxs-lookup"><span data-stu-id="b165e-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="b165e-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="b165e-111">Return value</span></span>

<span data-ttu-id="b165e-112">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="b165e-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b165e-113">常數</span><span class="sxs-lookup"><span data-stu-id="b165e-113">Constant</span></span>  |<span data-ttu-id="b165e-114">值</span><span class="sxs-lookup"><span data-stu-id="b165e-114">Value</span></span>  |<span data-ttu-id="b165e-115">說明</span><span class="sxs-lookup"><span data-stu-id="b165e-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="b165e-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="b165e-116">0x80041001</span></span> | <span data-ttu-id="b165e-117">發生意外的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b165e-117">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="b165e-118">0x80041016</span><span class="sxs-lookup"><span data-stu-id="b165e-118">0x80041016</span></span> | <span data-ttu-id="b165e-119">無法刪除屬性。</span><span class="sxs-lookup"><span data-stu-id="b165e-119">The property cannot be deleted.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b165e-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b165e-120">0x80041008</span></span> | <span data-ttu-id="b165e-121">`wszzName` 無效。</span><span class="sxs-lookup"><span data-stu-id="b165e-121">`wszzName` is invalid.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="b165e-122">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="b165e-122">0x80041002</span></span> | <span data-ttu-id="b165e-123">指定的屬性不存在。</span><span class="sxs-lookup"><span data-stu-id="b165e-123">The specified property does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b165e-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b165e-124">0x80041006</span></span> | <span data-ttu-id="b165e-125">不是記憶體不足，無法完成作業。</span><span class="sxs-lookup"><span data-stu-id="b165e-125">There is not enough memory to complete the operation.</span></span> |
| `WBEM_E_PROPAGATED_PROPERTY` | <span data-ttu-id="b165e-126">0x8004101c</span><span class="sxs-lookup"><span data-stu-id="b165e-126">0x8004101c</span></span> | <span data-ttu-id="b165e-127">屬性被繼承自基底類別。</span><span class="sxs-lookup"><span data-stu-id="b165e-127">The property is inherited from a base class.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | | <span data-ttu-id="b165e-128">屬性是系統屬性。</span><span class="sxs-lookup"><span data-stu-id="b165e-128">The property is a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b165e-129">0</span><span class="sxs-lookup"><span data-stu-id="b165e-129">0</span></span> | <span data-ttu-id="b165e-130">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="b165e-130">The function call was successful.</span></span>  |
| `WBEM_E_RESET_TO_DEFAULT` | <span data-ttu-id="b165e-131">0x80041030</span><span class="sxs-lookup"><span data-stu-id="b165e-131">0x80041030</span></span> | <span data-ttu-id="b165e-132">函式會刪除目前類別的覆寫預設值。</span><span class="sxs-lookup"><span data-stu-id="b165e-132">The function deleted an override default value for the current class.</span></span> <span data-ttu-id="b165e-133">這個屬性的父類別中的預設值已經 reactiviated。</span><span class="sxs-lookup"><span data-stu-id="b165e-133">The default value for this property in the parent class has been reactiviated.</span></span> | 

## <a name="remarks"></a><span data-ttu-id="b165e-134">備註</span><span class="sxs-lookup"><span data-stu-id="b165e-134">Remarks</span></span>

<span data-ttu-id="b165e-135">此函式會包裝呼叫[IWbemClassObject::Delete](https://msdn.microsoft.com/library/aa391438(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="b165e-135">This function wraps a call to the [IWbemClassObject::Delete](https://msdn.microsoft.com/library/aa391438(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b165e-136">需求</span><span class="sxs-lookup"><span data-stu-id="b165e-136">Requirements</span></span>  
 <span data-ttu-id="b165e-137">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b165e-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b165e-138">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b165e-138">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b165e-139">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b165e-139">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b165e-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="b165e-140">See also</span></span>  
[<span data-ttu-id="b165e-141">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="b165e-141">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
