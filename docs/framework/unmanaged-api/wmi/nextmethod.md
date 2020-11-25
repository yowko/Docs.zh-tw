---
title: 'NextMethod 函式 (非受控 API 參考) '
description: NextMethod 函式會捕獲列舉中的下一個方法。
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
ms.openlocfilehash: a0466aee47b0a6142870640c78b43f49e221ac2b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726765"
---
# <a name="nextmethod-function"></a><span data-ttu-id="2d5f9-103">NextMethod 函式</span><span class="sxs-lookup"><span data-stu-id="2d5f9-103">NextMethod function</span></span>

<span data-ttu-id="2d5f9-104">以呼叫 [BeginMethodEnumeration](beginmethodenumeration.md)的開頭，抓取列舉中的下一個方法。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2d5f9-105">語法</span><span class="sxs-lookup"><span data-stu-id="2d5f9-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="2d5f9-106">參數</span><span class="sxs-lookup"><span data-stu-id="2d5f9-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="2d5f9-107">在此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="2d5f9-108">在 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="2d5f9-109">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-109">[in] Reserved.</span></span> <span data-ttu-id="2d5f9-110">此參數必須為0。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="2d5f9-111">擴展指向呼叫之前的指標 `null` 。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="2d5f9-112">當函式傳回時，為包含方法名稱之新的位址 `BSTR` 。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span>

`ppSignatureIn`  
<span data-ttu-id="2d5f9-113">擴展指標，接收包含方法參數之 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 的指標 `in` 。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-113">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `in` parameters for the method.</span></span>

`ppSignatureOut`  
<span data-ttu-id="2d5f9-114">擴展指標，接收包含方法參數之 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 的指標 `out` 。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-114">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `out` parameters for the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="2d5f9-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="2d5f9-115">Return value</span></span>

<span data-ttu-id="2d5f9-116">這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="2d5f9-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2d5f9-117">常數</span><span class="sxs-lookup"><span data-stu-id="2d5f9-117">Constant</span></span>  |<span data-ttu-id="2d5f9-118">值</span><span class="sxs-lookup"><span data-stu-id="2d5f9-118">Value</span></span>  |<span data-ttu-id="2d5f9-119">描述</span><span class="sxs-lookup"><span data-stu-id="2d5f9-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="2d5f9-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="2d5f9-120">0x8004101d</span></span> | <span data-ttu-id="2d5f9-121">沒有函數的呼叫 [`BeginEnumeration`](beginenumeration.md) 。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="2d5f9-122">0</span><span class="sxs-lookup"><span data-stu-id="2d5f9-122">0</span></span> | <span data-ttu-id="2d5f9-123">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="2d5f9-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="2d5f9-124">0x40005</span></span> | <span data-ttu-id="2d5f9-125">列舉中沒有其他屬性。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="2d5f9-126">備註</span><span class="sxs-lookup"><span data-stu-id="2d5f9-126">Remarks</span></span>

<span data-ttu-id="2d5f9-127">此函數會包裝對 [IWbemClassObject：： NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-127">This function wraps a call to the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

<span data-ttu-id="2d5f9-128">呼叫端會藉由呼叫 [BeginMethodEnumeration](beginmethodenumeration.md) 函式來開始列舉序列，然後呼叫 [NextMethod] 函式，直到函式傳回為止 `WBEM_S_NO_MORE_DATA` 。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="2d5f9-129">（選擇性）呼叫端會藉由呼叫 [EndMethodEnumeration](endmethodenumeration.md)來完成序列。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="2d5f9-130">呼叫端可以在任何時間呼叫 [EndMethodEnumeration](endmethodenumeration.md) ，提早終止列舉。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="2d5f9-131">範例</span><span class="sxs-lookup"><span data-stu-id="2d5f9-131">Example</span></span>

<span data-ttu-id="2d5f9-132">如需 c + + 範例，請參閱 [IWbemClassObject：： NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) 方法。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-132">For a C++ example, see the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2d5f9-133">需求</span><span class="sxs-lookup"><span data-stu-id="2d5f9-133">Requirements</span></span>  

 <span data-ttu-id="2d5f9-134">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d5f9-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d5f9-135">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="2d5f9-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2d5f9-136">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2d5f9-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d5f9-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d5f9-137">See also</span></span>

- [<span data-ttu-id="2d5f9-138">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="2d5f9-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
