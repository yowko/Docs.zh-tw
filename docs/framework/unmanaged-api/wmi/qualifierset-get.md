---
title: QualifierSet_Get 函式 （Unmanaged API 參考）
description: QualifierSet_Get 函式會取得一個具名的辨識符號。
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8c10a680f1caffd583097b16c046729fe10b140
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43804236"
---
# <a name="qualifiersetget-function"></a><span data-ttu-id="258e8-103">QualifierSet_Get 函式</span><span class="sxs-lookup"><span data-stu-id="258e8-103">QualifierSet_Get function</span></span>
<span data-ttu-id="258e8-104">取得指定的具名限定詞。</span><span class="sxs-lookup"><span data-stu-id="258e8-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="258e8-105">語法</span><span class="sxs-lookup"><span data-stu-id="258e8-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Get (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="258e8-106">參數</span><span class="sxs-lookup"><span data-stu-id="258e8-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="258e8-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="258e8-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="258e8-108">[in]指標[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)執行個體。</span><span class="sxs-lookup"><span data-stu-id="258e8-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="258e8-109">[in]其值所要求的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="258e8-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="258e8-110">[in]保留。</span><span class="sxs-lookup"><span data-stu-id="258e8-110">[in] Reserved.</span></span> <span data-ttu-id="258e8-111">這個參數必須是 0。</span><span class="sxs-lookup"><span data-stu-id="258e8-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="258e8-112">[out]成功時，正確的型別和辨識符號值。</span><span class="sxs-lookup"><span data-stu-id="258e8-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="258e8-113">如果函式失敗，`VARIANT`所指向`pVal`則不會修改。</span><span class="sxs-lookup"><span data-stu-id="258e8-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="258e8-114">如果這個參數是`null`，則會忽略參數。</span><span class="sxs-lookup"><span data-stu-id="258e8-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="258e8-115">[out]接收要求的辨識符號的限定詞 flavor 個位元長整數指標。</span><span class="sxs-lookup"><span data-stu-id="258e8-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="258e8-116">如果不想要的類別資訊，此參數可以是`null`。</span><span class="sxs-lookup"><span data-stu-id="258e8-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="258e8-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="258e8-117">Return value</span></span>

<span data-ttu-id="258e8-118">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="258e8-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="258e8-119">常數</span><span class="sxs-lookup"><span data-stu-id="258e8-119">Constant</span></span>  |<span data-ttu-id="258e8-120">值</span><span class="sxs-lookup"><span data-stu-id="258e8-120">Value</span></span>  |<span data-ttu-id="258e8-121">描述</span><span class="sxs-lookup"><span data-stu-id="258e8-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="258e8-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="258e8-122">0x80041008</span></span> | <span data-ttu-id="258e8-123">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="258e8-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="258e8-124">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="258e8-124">0x80041002</span></span> | <span data-ttu-id="258e8-125">指定的辨識符號不存在。</span><span class="sxs-lookup"><span data-stu-id="258e8-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="258e8-126">0</span><span class="sxs-lookup"><span data-stu-id="258e8-126">0</span></span> | <span data-ttu-id="258e8-127">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="258e8-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="258e8-128">備註</span><span class="sxs-lookup"><span data-stu-id="258e8-128">Remarks</span></span>

<span data-ttu-id="258e8-129">此函式會包裝在呼叫[IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get)方法。</span><span class="sxs-lookup"><span data-stu-id="258e8-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="258e8-130">需求</span><span class="sxs-lookup"><span data-stu-id="258e8-130">Requirements</span></span>  
 <span data-ttu-id="258e8-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="258e8-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="258e8-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="258e8-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="258e8-133">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="258e8-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="258e8-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="258e8-134">See also</span></span>  
[<span data-ttu-id="258e8-135">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="258e8-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
