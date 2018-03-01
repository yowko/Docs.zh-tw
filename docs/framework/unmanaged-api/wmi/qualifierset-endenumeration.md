---
title: "QualifierSet_EndEnumeration 函式 （Unmanaged API 參考）"
description: "QualifierSet_EndEnumeration 函式會終止列舉型別。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7d8e6bb24eb471d807af2493f82b6be4f644124f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetendenumeration-function"></a><span data-ttu-id="77e91-103">QualifierSet_EndEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="77e91-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="77e91-104">結束呼叫開始列舉[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)函式。</span><span class="sxs-lookup"><span data-stu-id="77e91-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="77e91-105">語法</span><span class="sxs-lookup"><span data-stu-id="77e91-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="77e91-106">參數</span><span class="sxs-lookup"><span data-stu-id="77e91-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="77e91-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="77e91-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="77e91-108">[in]指標[IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="77e91-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="77e91-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="77e91-109">Return value</span></span>

<span data-ttu-id="77e91-110">這個函式傳回下列值以定義*WbemCli.h*標頭檔，或者您可以定義它做為常數在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="77e91-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="77e91-111">常數</span><span class="sxs-lookup"><span data-stu-id="77e91-111">Constant</span></span>  |<span data-ttu-id="77e91-112">值</span><span class="sxs-lookup"><span data-stu-id="77e91-112">Value</span></span>  |<span data-ttu-id="77e91-113">描述</span><span class="sxs-lookup"><span data-stu-id="77e91-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="77e91-114">0</span><span class="sxs-lookup"><span data-stu-id="77e91-114">0</span></span> | <span data-ttu-id="77e91-115">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="77e91-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="77e91-116">備註</span><span class="sxs-lookup"><span data-stu-id="77e91-116">Remarks</span></span>

<span data-ttu-id="77e91-117">此函式會包裝呼叫[IWbemQualifierSet::EndEnumeration](https://msdn.microsoft.com/library/aa391865(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="77e91-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](https://msdn.microsoft.com/library/aa391865(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="77e91-118">此呼叫，建議使用，但非必要。</span><span class="sxs-lookup"><span data-stu-id="77e91-118">This call is recommended, but not required.</span></span> <span data-ttu-id="77e91-119">它會立即釋出與列舉型別相關聯的資源。</span><span class="sxs-lookup"><span data-stu-id="77e91-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="77e91-120">需求</span><span class="sxs-lookup"><span data-stu-id="77e91-120">Requirements</span></span>  

<span data-ttu-id="77e91-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77e91-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="77e91-122">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="77e91-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="77e91-123">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="77e91-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e91-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77e91-124">See also</span></span>  
[<span data-ttu-id="77e91-125">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="77e91-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
