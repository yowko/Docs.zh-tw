---
title: "複製函式 （Unmanaged API 參考）"
description: "複製函數會傳回目前的完整複本的新物件。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Clone
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Clone
helpviewer_keywords: Clone function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df6a089f66ddd6f8f9a2d5677dd8dd6917fcb719
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="clone-function"></a><span data-ttu-id="4e706-103">複製函式</span><span class="sxs-lookup"><span data-stu-id="4e706-103">Clone function</span></span>
<span data-ttu-id="4e706-104">傳回目前物件的完整複本的新物件。</span><span class="sxs-lookup"><span data-stu-id="4e706-104">Returns a new object that is a complete clone of the current object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="4e706-105">語法</span><span class="sxs-lookup"><span data-stu-id="4e706-105">Syntax</span></span>  
  
```  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a><span data-ttu-id="4e706-106">參數</span><span class="sxs-lookup"><span data-stu-id="4e706-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4e706-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="4e706-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="4e706-108">[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="4e706-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`ppCopy`  
<span data-ttu-id="4e706-109">[out]新的物件已完成的單獨`ptr`。</span><span class="sxs-lookup"><span data-stu-id="4e706-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="4e706-110">這個引數不可為`null`如果它接收的目前物件的複本。</span><span class="sxs-lookup"><span data-stu-id="4e706-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="4e706-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="4e706-111">Return value</span></span>

<span data-ttu-id="4e706-112">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="4e706-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4e706-113">常數</span><span class="sxs-lookup"><span data-stu-id="4e706-113">Constant</span></span>  |<span data-ttu-id="4e706-114">值</span><span class="sxs-lookup"><span data-stu-id="4e706-114">Value</span></span>  |<span data-ttu-id="4e706-115">說明</span><span class="sxs-lookup"><span data-stu-id="4e706-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="4e706-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="4e706-116">0x80041001</span></span> | <span data-ttu-id="4e706-117">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="4e706-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4e706-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4e706-118">0x80041008</span></span> | <span data-ttu-id="4e706-119">`null`已指定為參數，而且不合法，在這種用法。</span><span class="sxs-lookup"><span data-stu-id="4e706-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="4e706-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="4e706-120">0x80041006</span></span> | <span data-ttu-id="4e706-121">沒有足夠的記憶體可供複製物件。</span><span class="sxs-lookup"><span data-stu-id="4e706-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="4e706-122">0</span><span class="sxs-lookup"><span data-stu-id="4e706-122">0</span></span> | <span data-ttu-id="4e706-123">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="4e706-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4e706-124">備註</span><span class="sxs-lookup"><span data-stu-id="4e706-124">Remarks</span></span>

<span data-ttu-id="4e706-125">此函式會包裝呼叫[IWbemClassObject::Clone](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="4e706-125">This function wraps a call to the [IWbemClassObject::Clone](https://msdn.microsoft.com/library/aa391436(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="4e706-126">複製的物件是 COM 物件的參考計數為 1。</span><span class="sxs-lookup"><span data-stu-id="4e706-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="4e706-127">需求</span><span class="sxs-lookup"><span data-stu-id="4e706-127">Requirements</span></span>  
 <span data-ttu-id="4e706-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e706-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e706-129">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4e706-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4e706-130">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4e706-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e706-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e706-131">See also</span></span>  
[<span data-ttu-id="4e706-132">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="4e706-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
