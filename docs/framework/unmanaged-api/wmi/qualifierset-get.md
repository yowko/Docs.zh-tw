---
title: 'QualifierSet_Get 函式 (非受控 API 參考) '
description: QualifierSet_Get 函式會取得命名限定詞。
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
ms.openlocfilehash: fd096287b85b4a51a8cae85dddcca95cc1a8dbae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721136"
---
# <a name="qualifierset_get-function"></a><span data-ttu-id="2f821-103">QualifierSet_Get 函式</span><span class="sxs-lookup"><span data-stu-id="2f821-103">QualifierSet_Get function</span></span>

<span data-ttu-id="2f821-104">取得指定的具名限定詞。</span><span class="sxs-lookup"><span data-stu-id="2f821-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2f821-105">語法</span><span class="sxs-lookup"><span data-stu-id="2f821-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="2f821-106">參數</span><span class="sxs-lookup"><span data-stu-id="2f821-106">Parameters</span></span>

<span data-ttu-id="2f821-107">`vFunc` 在此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="2f821-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="2f821-108">`ptr` 在 [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="2f821-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="2f821-109">`wszName` 在要求其值的辨識符號名稱。</span><span class="sxs-lookup"><span data-stu-id="2f821-109">`wszName` [in] The name of the qualifier whose value is requested.</span></span>

<span data-ttu-id="2f821-110">`lFlags` 在保留。</span><span class="sxs-lookup"><span data-stu-id="2f821-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="2f821-111">此參數必須為0。</span><span class="sxs-lookup"><span data-stu-id="2f821-111">This parameter must be 0.</span></span>

<span data-ttu-id="2f821-112">`pVal` 擴展如果成功，則為辨識符號的正確類型和值。</span><span class="sxs-lookup"><span data-stu-id="2f821-112">`pVal` [out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="2f821-113">如果函式失敗，則 `VARIANT` `pVal` 不會修改指向的。</span><span class="sxs-lookup"><span data-stu-id="2f821-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="2f821-114">如果此參數為 `null` ，則會忽略參數。</span><span class="sxs-lookup"><span data-stu-id="2f821-114">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="2f821-115">`plFlavor` 擴展LONG 的指標，可接收所要求限定詞的限定詞類別位。</span><span class="sxs-lookup"><span data-stu-id="2f821-115">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="2f821-116">如果不需要類別資訊，這個參數可以是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="2f821-116">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="2f821-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="2f821-117">Return value</span></span>

<span data-ttu-id="2f821-118">這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="2f821-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2f821-119">常數</span><span class="sxs-lookup"><span data-stu-id="2f821-119">Constant</span></span>  |<span data-ttu-id="2f821-120">值</span><span class="sxs-lookup"><span data-stu-id="2f821-120">Value</span></span>  |<span data-ttu-id="2f821-121">描述</span><span class="sxs-lookup"><span data-stu-id="2f821-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2f821-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2f821-122">0x80041008</span></span> | <span data-ttu-id="2f821-123">參數無效。</span><span class="sxs-lookup"><span data-stu-id="2f821-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="2f821-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="2f821-124">0x80041002</span></span> | <span data-ttu-id="2f821-125">指定的限定詞不存在。</span><span class="sxs-lookup"><span data-stu-id="2f821-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="2f821-126">0</span><span class="sxs-lookup"><span data-stu-id="2f821-126">0</span></span> | <span data-ttu-id="2f821-127">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="2f821-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2f821-128">備註</span><span class="sxs-lookup"><span data-stu-id="2f821-128">Remarks</span></span>

<span data-ttu-id="2f821-129">此函數會包裝對 [IWbemQualifierSet：： Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="2f821-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2f821-130">需求</span><span class="sxs-lookup"><span data-stu-id="2f821-130">Requirements</span></span>  

 <span data-ttu-id="2f821-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2f821-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f821-132">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="2f821-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2f821-133">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2f821-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f821-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f821-134">See also</span></span>

- [<span data-ttu-id="2f821-135">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="2f821-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
