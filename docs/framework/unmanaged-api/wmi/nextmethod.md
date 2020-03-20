---
title: NextMethod 函數（非託管 API 引用）
description: NextMethod 函數檢索枚舉中的下一個方法。
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 36acd6135110a8865bd8efdda628c352c01b4f26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174923"
---
# <a name="nextmethod-function"></a><span data-ttu-id="cd319-103">NextMethod 函式</span><span class="sxs-lookup"><span data-stu-id="cd319-103">NextMethod function</span></span>
<span data-ttu-id="cd319-104">檢索枚舉中的下一個方法，該方法以調用[BeginMethodEa）](beginmethodenumeration.md)開頭。</span><span class="sxs-lookup"><span data-stu-id="cd319-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="cd319-105">語法</span><span class="sxs-lookup"><span data-stu-id="cd319-105">Syntax</span></span>  
  
```cpp  
HRESULT NextMethod (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```  

## <a name="parameters"></a><span data-ttu-id="cd319-106">參數</span><span class="sxs-lookup"><span data-stu-id="cd319-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="cd319-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="cd319-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="cd319-108">[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="cd319-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="cd319-109">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="cd319-109">[in] Reserved.</span></span> <span data-ttu-id="cd319-110">此參數必須為 0。</span><span class="sxs-lookup"><span data-stu-id="cd319-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="cd319-111">[出]指向調用`null`之前的指標。</span><span class="sxs-lookup"><span data-stu-id="cd319-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="cd319-112">當函數返回時，包含方法名稱的新位址`BSTR`。</span><span class="sxs-lookup"><span data-stu-id="cd319-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span>

`ppSignatureIn`  
<span data-ttu-id="cd319-113">[出]接收指向[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標的指標，其中包含方法的`in`參數。</span><span class="sxs-lookup"><span data-stu-id="cd319-113">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `in` parameters for the method.</span></span>

`ppSignatureOut`  
<span data-ttu-id="cd319-114">[出]接收指向[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標的指標，其中包含方法的`out`參數。</span><span class="sxs-lookup"><span data-stu-id="cd319-114">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `out` parameters for the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="cd319-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="cd319-115">Return value</span></span>

<span data-ttu-id="cd319-116">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="cd319-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="cd319-117">持續性</span><span class="sxs-lookup"><span data-stu-id="cd319-117">Constant</span></span>  |<span data-ttu-id="cd319-118">值</span><span class="sxs-lookup"><span data-stu-id="cd319-118">Value</span></span>  |<span data-ttu-id="cd319-119">描述</span><span class="sxs-lookup"><span data-stu-id="cd319-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="cd319-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="cd319-120">0x8004101d</span></span> | <span data-ttu-id="cd319-121">沒有調用該[`BeginEnumeration`](beginenumeration.md)函數。</span><span class="sxs-lookup"><span data-stu-id="cd319-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="cd319-122">0</span><span class="sxs-lookup"><span data-stu-id="cd319-122">0</span></span> | <span data-ttu-id="cd319-123">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="cd319-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="cd319-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="cd319-124">0x40005</span></span> | <span data-ttu-id="cd319-125">枚舉中沒有更多的屬性。</span><span class="sxs-lookup"><span data-stu-id="cd319-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="cd319-126">備註</span><span class="sxs-lookup"><span data-stu-id="cd319-126">Remarks</span></span>

<span data-ttu-id="cd319-127">此函數包裝對[IWbemClassObject：：NextMethod 方法](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod)的調用。</span><span class="sxs-lookup"><span data-stu-id="cd319-127">This function wraps a call to the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

<span data-ttu-id="cd319-128">調用方通過調用[BeginMethod 枚舉](beginmethodenumeration.md)函數來開始枚舉序列，然後調用 [NextMethod] 函數，直到函數返回`WBEM_S_NO_MORE_DATA`。</span><span class="sxs-lookup"><span data-stu-id="cd319-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="cd319-129">或者，調用方通過調用[EndMethod 枚舉](endmethodenumeration.md)來完成序列。</span><span class="sxs-lookup"><span data-stu-id="cd319-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="cd319-130">調用方可以隨時調用[EndMethodEa 枚舉](endmethodenumeration.md)，從而提前終止枚舉。</span><span class="sxs-lookup"><span data-stu-id="cd319-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="cd319-131">範例</span><span class="sxs-lookup"><span data-stu-id="cd319-131">Example</span></span>

<span data-ttu-id="cd319-132">有關C++示例，請參閱[IWbemClassObject：：NextMethod 方法](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod)。</span><span class="sxs-lookup"><span data-stu-id="cd319-132">For a C++ example, see the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cd319-133">需求</span><span class="sxs-lookup"><span data-stu-id="cd319-133">Requirements</span></span>  
 <span data-ttu-id="cd319-134">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd319-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd319-135">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="cd319-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="cd319-136">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cd319-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd319-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd319-137">See also</span></span>

- [<span data-ttu-id="cd319-138">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="cd319-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
