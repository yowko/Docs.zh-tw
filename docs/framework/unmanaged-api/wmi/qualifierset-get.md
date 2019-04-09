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
ms.openlocfilehash: b0dc76a2732bf9c1e4f3a26fa2d045bfbcd837ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181086"
---
# <a name="qualifiersetget-function"></a><span data-ttu-id="32c9d-103">QualifierSet_Get 函式</span><span class="sxs-lookup"><span data-stu-id="32c9d-103">QualifierSet_Get function</span></span>
<span data-ttu-id="32c9d-104">取得指定的具名限定詞。</span><span class="sxs-lookup"><span data-stu-id="32c9d-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="32c9d-105">語法</span><span class="sxs-lookup"><span data-stu-id="32c9d-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="32c9d-106">參數</span><span class="sxs-lookup"><span data-stu-id="32c9d-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="32c9d-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="32c9d-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="32c9d-108">[in]指標[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)執行個體。</span><span class="sxs-lookup"><span data-stu-id="32c9d-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="32c9d-109">[in]其值所要求的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="32c9d-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="32c9d-110">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="32c9d-110">[in] Reserved.</span></span> <span data-ttu-id="32c9d-111">這個參數必須是 0。</span><span class="sxs-lookup"><span data-stu-id="32c9d-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="32c9d-112">[out]成功時，正確的型別和辨識符號值。</span><span class="sxs-lookup"><span data-stu-id="32c9d-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="32c9d-113">如果函式失敗，`VARIANT`所指向`pVal`則不會修改。</span><span class="sxs-lookup"><span data-stu-id="32c9d-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="32c9d-114">如果這個參數是`null`，則會忽略參數。</span><span class="sxs-lookup"><span data-stu-id="32c9d-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="32c9d-115">[out]接收要求的辨識符號的限定詞 flavor 個位元長整數指標。</span><span class="sxs-lookup"><span data-stu-id="32c9d-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="32c9d-116">如果不想要的類別資訊，此參數可以是`null`。</span><span class="sxs-lookup"><span data-stu-id="32c9d-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="32c9d-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="32c9d-117">Return value</span></span>

<span data-ttu-id="32c9d-118">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="32c9d-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="32c9d-119">常數</span><span class="sxs-lookup"><span data-stu-id="32c9d-119">Constant</span></span>  |<span data-ttu-id="32c9d-120">值</span><span class="sxs-lookup"><span data-stu-id="32c9d-120">Value</span></span>  |<span data-ttu-id="32c9d-121">描述</span><span class="sxs-lookup"><span data-stu-id="32c9d-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="32c9d-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="32c9d-122">0x80041008</span></span> | <span data-ttu-id="32c9d-123">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="32c9d-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="32c9d-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="32c9d-124">0x80041002</span></span> | <span data-ttu-id="32c9d-125">指定的辨識符號不存在。</span><span class="sxs-lookup"><span data-stu-id="32c9d-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="32c9d-126">0</span><span class="sxs-lookup"><span data-stu-id="32c9d-126">0</span></span> | <span data-ttu-id="32c9d-127">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="32c9d-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="32c9d-128">備註</span><span class="sxs-lookup"><span data-stu-id="32c9d-128">Remarks</span></span>

<span data-ttu-id="32c9d-129">此函式會包裝在呼叫[IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get)方法。</span><span class="sxs-lookup"><span data-stu-id="32c9d-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="32c9d-130">需求</span><span class="sxs-lookup"><span data-stu-id="32c9d-130">Requirements</span></span>  
 <span data-ttu-id="32c9d-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32c9d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32c9d-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="32c9d-132">**Header:** WMINet_Utils.idl</span></span>  
  
 **<span data-ttu-id="32c9d-133">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="32c9d-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="32c9d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32c9d-134">See also</span></span>

- [<span data-ttu-id="32c9d-135">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="32c9d-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
