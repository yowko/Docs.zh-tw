---
title: 獲取方法源函數（非託管 API 引用）
description: GetMethodOrigin 函數確定聲明方法的類。
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
ms.openlocfilehash: 5b4609b6649be875aea7dfcf52ba36b1e98ab7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176795"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="829ef-103">GetMethodOrigin 函式</span><span class="sxs-lookup"><span data-stu-id="829ef-103">GetMethodOrigin function</span></span>
<span data-ttu-id="829ef-104">判斷方法在其中宣告的類別。</span><span class="sxs-lookup"><span data-stu-id="829ef-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="829ef-105">語法</span><span class="sxs-lookup"><span data-stu-id="829ef-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```  

## <a name="parameters"></a><span data-ttu-id="829ef-106">參數</span><span class="sxs-lookup"><span data-stu-id="829ef-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="829ef-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="829ef-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="829ef-108">[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="829ef-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="829ef-109">[在]正在請求其擁有類的物件的方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="829ef-109">[in] The name of the method for the object whose owning class is being requested.</span></span>

`pstrClassName`  
<span data-ttu-id="829ef-110">[出]接收擁有 方法的類的名稱。</span><span class="sxs-lookup"><span data-stu-id="829ef-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="829ef-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="829ef-111">Return value</span></span>

<span data-ttu-id="829ef-112">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="829ef-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="829ef-113">持續性</span><span class="sxs-lookup"><span data-stu-id="829ef-113">Constant</span></span>  |<span data-ttu-id="829ef-114">值</span><span class="sxs-lookup"><span data-stu-id="829ef-114">Value</span></span>  |<span data-ttu-id="829ef-115">描述</span><span class="sxs-lookup"><span data-stu-id="829ef-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="829ef-116">0 x80041002</span><span class="sxs-lookup"><span data-stu-id="829ef-116">0x80041002</span></span> | <span data-ttu-id="829ef-117">找不到指定的方法。</span><span class="sxs-lookup"><span data-stu-id="829ef-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="829ef-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="829ef-118">0x80041008</span></span> | <span data-ttu-id="829ef-119">一個或多個參數無效。</span><span class="sxs-lookup"><span data-stu-id="829ef-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="829ef-120">0</span><span class="sxs-lookup"><span data-stu-id="829ef-120">0</span></span> | <span data-ttu-id="829ef-121">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="829ef-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="829ef-122">備註</span><span class="sxs-lookup"><span data-stu-id="829ef-122">Remarks</span></span>

<span data-ttu-id="829ef-123">此函數包裝對[IWbem ClassObject 的調用：：獲取方法原點](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)方法。</span><span class="sxs-lookup"><span data-stu-id="829ef-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="829ef-124">由於類可以從一個或多個基類繼承方法，因此開發人員通常希望確定在其中定義給定方法的類。</span><span class="sxs-lookup"><span data-stu-id="829ef-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="829ef-125">在`pstrClassName`調用函數之前，參數不能指向`BSTR`有效，因為這是一個`out`參數;因此，參數在調用函數之前，不能指向該參數。函數返回後，此指標不會處理。</span><span class="sxs-lookup"><span data-stu-id="829ef-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="829ef-126">需求</span><span class="sxs-lookup"><span data-stu-id="829ef-126">Requirements</span></span>  
<span data-ttu-id="829ef-127">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="829ef-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="829ef-128">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="829ef-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="829ef-129">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="829ef-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="829ef-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="829ef-130">See also</span></span>

- [<span data-ttu-id="829ef-131">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="829ef-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
