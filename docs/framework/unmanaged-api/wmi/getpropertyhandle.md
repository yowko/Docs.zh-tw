---
title: "GetPropertyHandle 函式 （Unmanaged API 參考）"
description: "GetPropertyHandle 函式會傳回該 identies 屬性唯一的控制代碼。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyHandle
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyHandle
helpviewer_keywords: GetPropertyHandle function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ab3df6d2233059de76036da7ff27f5cc1808aaf
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="getpropertyhandle-function"></a><span data-ttu-id="35131-103">GetPropertyHandle 函式</span><span class="sxs-lookup"><span data-stu-id="35131-103">GetPropertyHandle function</span></span>
<span data-ttu-id="35131-104">傳回唯一的控制代碼識別屬性。</span><span class="sxs-lookup"><span data-stu-id="35131-104">Returns a unique handle that identifies a property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="35131-105">語法</span><span class="sxs-lookup"><span data-stu-id="35131-105">Syntax</span></span>  
  
```  
HRESULT GetPropertyHandle (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
); 
```  

## <a name="parameters"></a><span data-ttu-id="35131-106">參數</span><span class="sxs-lookup"><span data-stu-id="35131-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="35131-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="35131-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="35131-108">[in]指標[IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="35131-108">[in] A pointer to an [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) instance.</span></span>

`wszPropertyName`  
<span data-ttu-id="35131-109">[in]包含屬性名稱的 UTF16 編碼 characaters null 結尾字串。</span><span class="sxs-lookup"><span data-stu-id="35131-109">[in] A null-terminated string of UTF16-encoded characaters that contains the property name.</span></span>   

`pType`  
<span data-ttu-id="35131-110">[out]指標[ `CIMTYPE` ](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx)列舉的成員，表示屬性的 CIM 類型。</span><span class="sxs-lookup"><span data-stu-id="35131-110">[out] A pointer to a [`CIMTYPE`](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) enumeration member that represents the CIM type of the property.</span></span>

`pHandle`   
<span data-ttu-id="35131-111">[out]包含屬性控制代碼的整數指標。</span><span class="sxs-lookup"><span data-stu-id="35131-111">[out] A pointer to an integer that contains the property handle.</span></span>

## <a name="return-value"></a><span data-ttu-id="35131-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="35131-112">Return value</span></span>

<span data-ttu-id="35131-113">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="35131-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="35131-114">常數</span><span class="sxs-lookup"><span data-stu-id="35131-114">Constant</span></span>  |<span data-ttu-id="35131-115">值</span><span class="sxs-lookup"><span data-stu-id="35131-115">Value</span></span>  |<span data-ttu-id="35131-116">說明</span><span class="sxs-lookup"><span data-stu-id="35131-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="35131-117">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="35131-117">0x80041002</span></span> | <span data-ttu-id="35131-118">找不到指定的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="35131-118">The specified property name was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="35131-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="35131-119">0x80041008</span></span> | <span data-ttu-id="35131-120">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="35131-120">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_SUPPORTED` | <span data-ttu-id="35131-121">0x8004100c</span><span class="sxs-lookup"><span data-stu-id="35131-121">0x8004100c</span></span> | <span data-ttu-id="35131-122">要求的屬性屬於型別是`CIM_OBJECT`或`CIM_ARRAY`。</span><span class="sxs-lookup"><span data-stu-id="35131-122">The requested property is of type are `CIM_OBJECT` or `CIM_ARRAY`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="35131-123">0</span><span class="sxs-lookup"><span data-stu-id="35131-123">0</span></span> | <span data-ttu-id="35131-124">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="35131-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="35131-125">備註</span><span class="sxs-lookup"><span data-stu-id="35131-125">Remarks</span></span>

<span data-ttu-id="35131-126">此函式會包裝呼叫[IWbemClassObject::GetPropertyHandle](https://msdn.microsoft.com/library/aa391771(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="35131-126">This function wraps a call to the [IWbemClassObject::GetPropertyHandle](https://msdn.microsoft.com/library/aa391771(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="35131-127">您可以使用此控制代碼來使用時，識別屬性[IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx)方法來讀取或寫入屬性值。</span><span class="sxs-lookup"><span data-stu-id="35131-127">You can use this handle to identify properties when using  [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) methods to read or write property values.</span></span>

<span data-ttu-id="35131-128">控制代碼可以擷取屬性的所有資料類型以外`CIM_OBJECT`和`CIM_ARRAY`。</span><span class="sxs-lookup"><span data-stu-id="35131-128">Handles can be retrieved for properties of all data types other than `CIM_OBJECT` and `CIM_ARRAY`.</span></span> <span data-ttu-id="35131-129">傳回類別的所有執行個體的控制代碼的工作。</span><span class="sxs-lookup"><span data-stu-id="35131-129">Returned handles work across all instances of a class.</span></span>

## <a name="requirements"></a><span data-ttu-id="35131-130">需求</span><span class="sxs-lookup"><span data-stu-id="35131-130">Requirements</span></span>  
<span data-ttu-id="35131-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="35131-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35131-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="35131-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="35131-133">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="35131-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35131-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="35131-134">See also</span></span>  
[<span data-ttu-id="35131-135">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="35131-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
