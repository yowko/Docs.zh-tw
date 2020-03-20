---
title: 寫入屬性值函數（非託管 API 引用）
description: WritePropertyValue 函數將位元組寫入屬性。
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4a950beef2e9bf8c0230d6a38008d75f89373410
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174832"
---
# <a name="writepropertyvalue-function"></a><span data-ttu-id="87a1c-103">WritePropertyValue 函式</span><span class="sxs-lookup"><span data-stu-id="87a1c-103">WritePropertyValue function</span></span>
<span data-ttu-id="87a1c-104">將指定的位元組數目寫入到屬性控制代碼所指定的屬性中。</span><span class="sxs-lookup"><span data-stu-id="87a1c-104">Writes a specified number of bytes to a property identified by a property handle.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="87a1c-105">語法</span><span class="sxs-lookup"><span data-stu-id="87a1c-105">Syntax</span></span>  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a><span data-ttu-id="87a1c-106">參數</span><span class="sxs-lookup"><span data-stu-id="87a1c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="87a1c-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="87a1c-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="87a1c-108">[在]指向[IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="87a1c-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`lHandle`  
<span data-ttu-id="87a1c-109">[在]包含標識此屬性的控制碼的整數。</span><span class="sxs-lookup"><span data-stu-id="87a1c-109">[in] An integer that contains the handle that identifies this property.</span></span> <span data-ttu-id="87a1c-110">可以通過調用[GetPropertyHandle](getpropertyhandle.md)函數來檢索控制碼。</span><span class="sxs-lookup"><span data-stu-id="87a1c-110">The handle can be retrieved by calling the [GetPropertyHandle](getpropertyhandle.md) function.</span></span>

`lNumBytes`  
<span data-ttu-id="87a1c-111">[在]寫入屬性的位元組數。</span><span class="sxs-lookup"><span data-stu-id="87a1c-111">[in] The number of bytes being written to the property.</span></span> <span data-ttu-id="87a1c-112">有關詳細資訊，請參閱[備註](#remarks)部分。</span><span class="sxs-lookup"><span data-stu-id="87a1c-112">See the [Remarks](#remarks) section for more information.</span></span>

<span data-ttu-id="87a1c-113">`pHandle`[出]指向包含資料的位元組陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="87a1c-113">`pHandle` [out] A pointer to the byte array that contains the data.</span></span>

## <a name="return-value"></a><span data-ttu-id="87a1c-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="87a1c-114">Return value</span></span>

<span data-ttu-id="87a1c-115">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="87a1c-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="87a1c-116">持續性</span><span class="sxs-lookup"><span data-stu-id="87a1c-116">Constant</span></span>  |<span data-ttu-id="87a1c-117">值</span><span class="sxs-lookup"><span data-stu-id="87a1c-117">Value</span></span>  |<span data-ttu-id="87a1c-118">描述</span><span class="sxs-lookup"><span data-stu-id="87a1c-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="87a1c-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="87a1c-119">0x80041008</span></span> | <span data-ttu-id="87a1c-120">參數無效。</span><span class="sxs-lookup"><span data-stu-id="87a1c-120">A parameter is not valid.</span></span> |
|`WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="87a1c-121">0x80041005</span><span class="sxs-lookup"><span data-stu-id="87a1c-121">0x80041005</span></span> | <span data-ttu-id="87a1c-122">發生型別不符。</span><span class="sxs-lookup"><span data-stu-id="87a1c-122">A type mismatch occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="87a1c-123">0</span><span class="sxs-lookup"><span data-stu-id="87a1c-123">0</span></span> | <span data-ttu-id="87a1c-124">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="87a1c-124">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="87a1c-125">備註</span><span class="sxs-lookup"><span data-stu-id="87a1c-125">Remarks</span></span>

<span data-ttu-id="87a1c-126">此函數將調用包起來到[IWbemClassObject：：WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue)方法。</span><span class="sxs-lookup"><span data-stu-id="87a1c-126">This function wraps a call to the [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) method.</span></span>

<span data-ttu-id="87a1c-127">使用此函數可以設置字串和所有其他非`DWORD`或非`QWORD`資料。</span><span class="sxs-lookup"><span data-stu-id="87a1c-127">Use this function to set string and all other non-`DWORD` or non-`QWORD` data.</span></span>

<span data-ttu-id="87a1c-128">對於非字串屬性值，`lNumBytes`必須為指定的屬性類型的正確資料大小。</span><span class="sxs-lookup"><span data-stu-id="87a1c-128">For nonstring property values, `lNumBytes` must be the correct data size of the property type specified.</span></span> <span data-ttu-id="87a1c-129">對於字串屬性值，`lNumBytes`必須為指定字串的長度（以位元組為單位），並且字串本身的長度（以位元組為單位）並且後面必須使用 null 終止字元。</span><span class="sxs-lookup"><span data-stu-id="87a1c-129">For string property values, `lNumBytes` must be the length of the specified string in bytes, and the string itself must be of an even length in bytes and be followed with a null-termination character.</span></span>

## <a name="requirements"></a><span data-ttu-id="87a1c-130">需求</span><span class="sxs-lookup"><span data-stu-id="87a1c-130">Requirements</span></span>  
<span data-ttu-id="87a1c-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87a1c-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87a1c-132">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="87a1c-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="87a1c-133">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="87a1c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87a1c-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87a1c-134">See also</span></span>

- [<span data-ttu-id="87a1c-135">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="87a1c-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
