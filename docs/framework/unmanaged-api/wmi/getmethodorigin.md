---
title: GetMethodOrigin 函式 （Unmanaged API 參考）
description: GetMethodOrigin 函式判斷宣告方法的類別。
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35e56494d0082db970afce21da8e63a597f0a535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458145"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="4893b-103">GetMethodOrigin 函式</span><span class="sxs-lookup"><span data-stu-id="4893b-103">GetMethodOrigin function</span></span>
<span data-ttu-id="4893b-104">判斷在其中宣告方法的類別。</span><span class="sxs-lookup"><span data-stu-id="4893b-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="4893b-105">語法</span><span class="sxs-lookup"><span data-stu-id="4893b-105">Syntax</span></span>  
  
```  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="4893b-106">參數</span><span class="sxs-lookup"><span data-stu-id="4893b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4893b-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="4893b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="4893b-108">[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="4893b-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="4893b-109">[in]正在要求其主控類別之物件的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="4893b-109">[in] The name of the method for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="4893b-110">[out]接收擁有方法的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="4893b-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="4893b-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="4893b-111">Return value</span></span>

<span data-ttu-id="4893b-112">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="4893b-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4893b-113">常數</span><span class="sxs-lookup"><span data-stu-id="4893b-113">Constant</span></span>  |<span data-ttu-id="4893b-114">值</span><span class="sxs-lookup"><span data-stu-id="4893b-114">Value</span></span>  |<span data-ttu-id="4893b-115">描述</span><span class="sxs-lookup"><span data-stu-id="4893b-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="4893b-116">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="4893b-116">0x80041002</span></span> | <span data-ttu-id="4893b-117">找不到指定的方法。</span><span class="sxs-lookup"><span data-stu-id="4893b-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4893b-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4893b-118">0x80041008</span></span> | <span data-ttu-id="4893b-119">一或多個參數都不是有效的。</span><span class="sxs-lookup"><span data-stu-id="4893b-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="4893b-120">0</span><span class="sxs-lookup"><span data-stu-id="4893b-120">0</span></span> | <span data-ttu-id="4893b-121">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="4893b-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="4893b-122">備註</span><span class="sxs-lookup"><span data-stu-id="4893b-122">Remarks</span></span>

<span data-ttu-id="4893b-123">此函式會包裝呼叫[IWbemClassObject::GetMethodOrigin](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="4893b-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="4893b-124">類別可以繼承一或多個基底類別方法，因為開發人員通常會想要判斷指定的方法定義所在的類別。</span><span class="sxs-lookup"><span data-stu-id="4893b-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="4893b-125">`pstrClassName`參數必須是指向有效`BSTR`因為這是在呼叫函式前`out`參數; 此指標會取消配置函式傳回後。</span><span class="sxs-lookup"><span data-stu-id="4893b-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="4893b-126">需求</span><span class="sxs-lookup"><span data-stu-id="4893b-126">Requirements</span></span>  
<span data-ttu-id="4893b-127">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4893b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4893b-128">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4893b-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4893b-129">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4893b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4893b-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4893b-130">See also</span></span>  
[<span data-ttu-id="4893b-131">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="4893b-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
