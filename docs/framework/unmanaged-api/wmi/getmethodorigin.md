---
title: 'GetMethodOrigin 函式 (非受控 API 參考) '
description: GetMethodOrigin 函式會判斷宣告方法的類別。
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
ms.openlocfilehash: 434392ffb4d9124e319bcd9c42fdd340d3fec5b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722774"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="0200a-103">GetMethodOrigin 函式</span><span class="sxs-lookup"><span data-stu-id="0200a-103">GetMethodOrigin function</span></span>

<span data-ttu-id="0200a-104">判斷方法在其中宣告的類別。</span><span class="sxs-lookup"><span data-stu-id="0200a-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0200a-105">語法</span><span class="sxs-lookup"><span data-stu-id="0200a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```  

## <a name="parameters"></a><span data-ttu-id="0200a-106">參數</span><span class="sxs-lookup"><span data-stu-id="0200a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="0200a-107">在此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="0200a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="0200a-108">在 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="0200a-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="0200a-109">在要求其擁有類別之物件的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="0200a-109">[in] The name of the method for the object whose owning class is being requested.</span></span>

`pstrClassName`  
<span data-ttu-id="0200a-110">擴展接收擁有方法之類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="0200a-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="0200a-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="0200a-111">Return value</span></span>

<span data-ttu-id="0200a-112">這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="0200a-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0200a-113">常數</span><span class="sxs-lookup"><span data-stu-id="0200a-113">Constant</span></span>  |<span data-ttu-id="0200a-114">值</span><span class="sxs-lookup"><span data-stu-id="0200a-114">Value</span></span>  |<span data-ttu-id="0200a-115">描述</span><span class="sxs-lookup"><span data-stu-id="0200a-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="0200a-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="0200a-116">0x80041002</span></span> | <span data-ttu-id="0200a-117">找不到指定的方法。</span><span class="sxs-lookup"><span data-stu-id="0200a-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0200a-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0200a-118">0x80041008</span></span> | <span data-ttu-id="0200a-119">一或多個參數無效。</span><span class="sxs-lookup"><span data-stu-id="0200a-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="0200a-120">0</span><span class="sxs-lookup"><span data-stu-id="0200a-120">0</span></span> | <span data-ttu-id="0200a-121">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="0200a-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="0200a-122">備註</span><span class="sxs-lookup"><span data-stu-id="0200a-122">Remarks</span></span>

<span data-ttu-id="0200a-123">此函數會包裝對 [IWbemClassObject：： GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="0200a-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="0200a-124">因為類別可以繼承一或多個基類的方法，所以開發人員通常會想要判斷指定方法定義所在的類別。</span><span class="sxs-lookup"><span data-stu-id="0200a-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="0200a-125">`pstrClassName`參數必須在呼叫函式之前，不能指向有效的， `BSTR` 因為這是參數，在函式傳回 `out` 之後，這個指標不會解除配置。</span><span class="sxs-lookup"><span data-stu-id="0200a-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="0200a-126">需求</span><span class="sxs-lookup"><span data-stu-id="0200a-126">Requirements</span></span>  

<span data-ttu-id="0200a-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0200a-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0200a-128">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="0200a-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0200a-129">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0200a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0200a-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0200a-130">See also</span></span>

- [<span data-ttu-id="0200a-131">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="0200a-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
