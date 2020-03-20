---
title: QualifierSet_Get函數（非託管 API 引用）
description: QualifierSet_Get函數獲取命名的限定詞。
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 2f4e2d4518e01f3415b8f17ce5778dd98b2a45c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174884"
---
# <a name="qualifierset_get-function"></a><span data-ttu-id="b3794-103">QualifierSet_Get 函式</span><span class="sxs-lookup"><span data-stu-id="b3794-103">QualifierSet_Get function</span></span>
<span data-ttu-id="b3794-104">取得指定的具名限定詞。</span><span class="sxs-lookup"><span data-stu-id="b3794-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b3794-105">語法</span><span class="sxs-lookup"><span data-stu-id="b3794-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a><span data-ttu-id="b3794-106">參數</span><span class="sxs-lookup"><span data-stu-id="b3794-106">Parameters</span></span>

<span data-ttu-id="b3794-107">`vFunc`[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="b3794-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="b3794-108">`ptr`[在]指向[IWbem 限定詞集實例的](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)指標。</span><span class="sxs-lookup"><span data-stu-id="b3794-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="b3794-109">`wszName`[在]請求其值的限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="b3794-109">`wszName` [in] The name of the qualifier whose value is requested.</span></span>

<span data-ttu-id="b3794-110">`lFlags`[在]保留。</span><span class="sxs-lookup"><span data-stu-id="b3794-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="b3794-111">此參數必須為 0。</span><span class="sxs-lookup"><span data-stu-id="b3794-111">This parameter must be 0.</span></span>

<span data-ttu-id="b3794-112">`pVal`[出]成功後，限定詞的正確類型和值。</span><span class="sxs-lookup"><span data-stu-id="b3794-112">`pVal` [out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="b3794-113">如果函數失敗，`VARIANT`則 不修改`pVal`指向 的 。</span><span class="sxs-lookup"><span data-stu-id="b3794-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="b3794-114">如果此參數為`null`，則忽略該參數。</span><span class="sxs-lookup"><span data-stu-id="b3794-114">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="b3794-115">`plFlavor`[出]指向 LONG 的指標，該指標接收請求的限定詞的限定詞的限定詞風味位。</span><span class="sxs-lookup"><span data-stu-id="b3794-115">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="b3794-116">如果不需要風味資訊，則此參數可以是`null`。</span><span class="sxs-lookup"><span data-stu-id="b3794-116">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="b3794-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="b3794-117">Return value</span></span>

<span data-ttu-id="b3794-118">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="b3794-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b3794-119">持續性</span><span class="sxs-lookup"><span data-stu-id="b3794-119">Constant</span></span>  |<span data-ttu-id="b3794-120">值</span><span class="sxs-lookup"><span data-stu-id="b3794-120">Value</span></span>  |<span data-ttu-id="b3794-121">描述</span><span class="sxs-lookup"><span data-stu-id="b3794-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b3794-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b3794-122">0x80041008</span></span> | <span data-ttu-id="b3794-123">參數無效。</span><span class="sxs-lookup"><span data-stu-id="b3794-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="b3794-124">0 x80041002</span><span class="sxs-lookup"><span data-stu-id="b3794-124">0x80041002</span></span> | <span data-ttu-id="b3794-125">指定的限定詞不存在。</span><span class="sxs-lookup"><span data-stu-id="b3794-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="b3794-126">0</span><span class="sxs-lookup"><span data-stu-id="b3794-126">0</span></span> | <span data-ttu-id="b3794-127">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="b3794-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b3794-128">備註</span><span class="sxs-lookup"><span data-stu-id="b3794-128">Remarks</span></span>

<span data-ttu-id="b3794-129">此函數包裝對[IWbem 限定詞集的調用：：get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get)方法。</span><span class="sxs-lookup"><span data-stu-id="b3794-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b3794-130">需求</span><span class="sxs-lookup"><span data-stu-id="b3794-130">Requirements</span></span>  
 <span data-ttu-id="b3794-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3794-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3794-132">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b3794-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b3794-133">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b3794-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3794-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3794-134">See also</span></span>

- [<span data-ttu-id="b3794-135">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="b3794-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
