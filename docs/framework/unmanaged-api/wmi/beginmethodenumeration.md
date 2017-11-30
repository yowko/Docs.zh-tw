---
title: "BeginMethodEnumeration 函式 （Unmanaged API 參考）"
description: "BeginMethodEnumeration 函式開頭物件的方法的列舉"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BeginMethodEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BeginMethodEnumeration
helpviewer_keywords: BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e44c432f9503f96ad4dab9e25b78e6dd148f94c
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="beginenumeration-function"></a><span data-ttu-id="3f058-103">BeginEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="3f058-103">BeginEnumeration function</span></span>
<span data-ttu-id="3f058-104">開始列舉物件的可用方法的型別。</span><span class="sxs-lookup"><span data-stu-id="3f058-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="3f058-105">語法</span><span class="sxs-lookup"><span data-stu-id="3f058-105">Syntax</span></span>  
  
``` 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="3f058-106">參數</span><span class="sxs-lookup"><span data-stu-id="3f058-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="3f058-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="3f058-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="3f058-108">[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="3f058-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="3f058-109">[in]零 (0) 的所有方法中或指定之列舉型別範圍的旗標。</span><span class="sxs-lookup"><span data-stu-id="3f058-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="3f058-110">中所定義的下列旗標*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="3f058-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="3f058-111">常數</span><span class="sxs-lookup"><span data-stu-id="3f058-111">Constant</span></span>  |<span data-ttu-id="3f058-112">值</span><span class="sxs-lookup"><span data-stu-id="3f058-112">Value</span></span>  |<span data-ttu-id="3f058-113">說明</span><span class="sxs-lookup"><span data-stu-id="3f058-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="3f058-114">0x10</span><span class="sxs-lookup"><span data-stu-id="3f058-114">0x10</span></span> | <span data-ttu-id="3f058-115">限制此類別本身中定義之方法的列舉。</span><span class="sxs-lookup"><span data-stu-id="3f058-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="3f058-116">0x20</span><span class="sxs-lookup"><span data-stu-id="3f058-116">0x20</span></span> | <span data-ttu-id="3f058-117">限制的列舉型別都繼承自基底類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="3f058-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="3f058-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="3f058-118">Return value</span></span>

<span data-ttu-id="3f058-119">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="3f058-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3f058-120">常數</span><span class="sxs-lookup"><span data-stu-id="3f058-120">Constant</span></span>  |<span data-ttu-id="3f058-121">值</span><span class="sxs-lookup"><span data-stu-id="3f058-121">Value</span></span>  |<span data-ttu-id="3f058-122">說明</span><span class="sxs-lookup"><span data-stu-id="3f058-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3f058-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3f058-123">0x80041008</span></span> | <span data-ttu-id="3f058-124">`lEnnumFlags`為非零，並不是其中一個指定的旗標。</span><span class="sxs-lookup"><span data-stu-id="3f058-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3f058-125">0</span><span class="sxs-lookup"><span data-stu-id="3f058-125">0</span></span> | <span data-ttu-id="3f058-126">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="3f058-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="3f058-127">備註</span><span class="sxs-lookup"><span data-stu-id="3f058-127">Remarks</span></span>

<span data-ttu-id="3f058-128">此函式會包裝呼叫[IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="3f058-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="3f058-129">如果目前的物件類別定義，才支援這個方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="3f058-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="3f058-130">方法操作中未提供[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)指向執行個體的指標。</span><span class="sxs-lookup"><span data-stu-id="3f058-130">Method manipulation is not available from [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointers that point to instances.</span></span> <span data-ttu-id="3f058-131">方法會列舉中的順序保證能夠針對指定的執行個體而異[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)。</span><span class="sxs-lookup"><span data-stu-id="3f058-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx).</span></span>

## <a name="requirements"></a><span data-ttu-id="3f058-132">需求</span><span class="sxs-lookup"><span data-stu-id="3f058-132">Requirements</span></span>  
 <span data-ttu-id="3f058-133">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3f058-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f058-134">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3f058-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3f058-135">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3f058-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f058-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="3f058-136">See also</span></span>  
[<span data-ttu-id="3f058-137">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="3f058-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
