---
title: "EndEnumeration 函式 （Unmanaged API 參考）"
description: "EndEnumeration 函式會終止列舉型別。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: EndEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: EndEnumeration
helpviewer_keywords: EndEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 043fce26870e5af2850b9f2e91e7e97c7bee6c90
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="endenumeration-function"></a><span data-ttu-id="1b829-103">EndEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="1b829-103">EndEnumeration function</span></span>
<span data-ttu-id="1b829-104">結束呼叫啟動列舉順序[BeginEnumeration 函式](beginenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="1b829-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="1b829-105">語法</span><span class="sxs-lookup"><span data-stu-id="1b829-105">Syntax</span></span>  
  
```  
HRESULT EndEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="1b829-106">參數</span><span class="sxs-lookup"><span data-stu-id="1b829-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="1b829-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="1b829-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="1b829-108">[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="1b829-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>


## <a name="return-value"></a><span data-ttu-id="1b829-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="1b829-109">Return value</span></span>

<span data-ttu-id="1b829-110">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="1b829-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1b829-111">常數</span><span class="sxs-lookup"><span data-stu-id="1b829-111">Constant</span></span>  |<span data-ttu-id="1b829-112">值</span><span class="sxs-lookup"><span data-stu-id="1b829-112">Value</span></span>  |<span data-ttu-id="1b829-113">說明</span><span class="sxs-lookup"><span data-stu-id="1b829-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="1b829-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="1b829-114">0x80041001</span></span> | <span data-ttu-id="1b829-115">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="1b829-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1b829-116">0</span><span class="sxs-lookup"><span data-stu-id="1b829-116">0</span></span> | <span data-ttu-id="1b829-117">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="1b829-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="1b829-118">備註</span><span class="sxs-lookup"><span data-stu-id="1b829-118">Remarks</span></span>

<span data-ttu-id="1b829-119">此函式會包裝呼叫[IWbemClassObject::EndEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="1b829-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) method.</span></span>

<span data-ttu-id="1b829-120">呼叫`EndEnumeration`函式不是必要項目，但建議因為列舉型別相關聯的資源釋出。</span><span class="sxs-lookup"><span data-stu-id="1b829-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="1b829-121">不過，resoruces 會自動解除配置時啟動下一次列舉或釋放物件。</span><span class="sxs-lookup"><span data-stu-id="1b829-121">However, the resoruces are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="1b829-122">需求</span><span class="sxs-lookup"><span data-stu-id="1b829-122">Requirements</span></span>  
 <span data-ttu-id="1b829-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b829-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b829-124">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1b829-124">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1b829-125">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1b829-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b829-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="1b829-126">See also</span></span>  
[<span data-ttu-id="1b829-127">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="1b829-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
