---
title: QualifierSet_Get 函式 （Unmanaged API 參考）
description: QualifierSet_Get 函式取得具名的限定詞。
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
ms.openlocfilehash: f1bc57ab45a0452d9e3a50f0ab2de786ad73204a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458643"
---
# <a name="qualifiersetget-function"></a><span data-ttu-id="79887-103">QualifierSet_Get 函式</span><span class="sxs-lookup"><span data-stu-id="79887-103">QualifierSet_Get function</span></span>
<span data-ttu-id="79887-104">取得指定的具名的限定詞。</span><span class="sxs-lookup"><span data-stu-id="79887-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="79887-105">語法</span><span class="sxs-lookup"><span data-stu-id="79887-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="79887-106">參數</span><span class="sxs-lookup"><span data-stu-id="79887-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="79887-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="79887-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="79887-108">[in]指標[IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="79887-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="79887-109">[in]要求其值限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="79887-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="79887-110">[in]保留。</span><span class="sxs-lookup"><span data-stu-id="79887-110">[in] Reserved.</span></span> <span data-ttu-id="79887-111">這個參數必須是 0。</span><span class="sxs-lookup"><span data-stu-id="79887-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="79887-112">[out]成功時，正確的型別和辨識符號值。</span><span class="sxs-lookup"><span data-stu-id="79887-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="79887-113">如果函式失敗，`VARIANT`指向`pVal`則不會修改。</span><span class="sxs-lookup"><span data-stu-id="79887-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="79887-114">如果這個參數是`null`，會忽略此參數。</span><span class="sxs-lookup"><span data-stu-id="79887-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="79887-115">[out]接收要求的識別碼辨識符號的限定詞 flavor 位元長整數指標。</span><span class="sxs-lookup"><span data-stu-id="79887-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="79887-116">如果不想要的類別資訊，這個參數可以是`null`。</span><span class="sxs-lookup"><span data-stu-id="79887-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="79887-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="79887-117">Return value</span></span>

<span data-ttu-id="79887-118">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="79887-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="79887-119">常數</span><span class="sxs-lookup"><span data-stu-id="79887-119">Constant</span></span>  |<span data-ttu-id="79887-120">值</span><span class="sxs-lookup"><span data-stu-id="79887-120">Value</span></span>  |<span data-ttu-id="79887-121">描述</span><span class="sxs-lookup"><span data-stu-id="79887-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="79887-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="79887-122">0x80041008</span></span> | <span data-ttu-id="79887-123">參數不是有效的。</span><span class="sxs-lookup"><span data-stu-id="79887-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="79887-124">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="79887-124">0x80041002</span></span> | <span data-ttu-id="79887-125">指定的限定詞不存在。</span><span class="sxs-lookup"><span data-stu-id="79887-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="79887-126">0</span><span class="sxs-lookup"><span data-stu-id="79887-126">0</span></span> | <span data-ttu-id="79887-127">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="79887-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="79887-128">備註</span><span class="sxs-lookup"><span data-stu-id="79887-128">Remarks</span></span>

<span data-ttu-id="79887-129">此函式會包裝呼叫[IWbemQualifierSet::Get](https://msdn.microsoft.com/library/aa391867(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="79887-129">This function wraps a call to the [IWbemQualifierSet::Get](https://msdn.microsoft.com/library/aa391867(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="79887-130">需求</span><span class="sxs-lookup"><span data-stu-id="79887-130">Requirements</span></span>  
 <span data-ttu-id="79887-131">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="79887-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79887-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="79887-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="79887-133">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="79887-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79887-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79887-134">See also</span></span>  
[<span data-ttu-id="79887-135">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="79887-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
