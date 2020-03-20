---
title: QualifierSet_EndEnumeration函數（非託管 API 引用）
description: QualifierSet_EndEnumeration函數終止枚舉。
ms.date: 11/06/2017
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
ms.openlocfilehash: c606580ff2e02c5659c14b134b1a17a65651952b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176743"
---
# <a name="qualifierset_endenumeration-function"></a><span data-ttu-id="5490b-103">QualifierSet_EndEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="5490b-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="5490b-104">終止從調用[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md)函數開始的枚舉。</span><span class="sxs-lookup"><span data-stu-id="5490b-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5490b-105">語法</span><span class="sxs-lookup"><span data-stu-id="5490b-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr
);
```  

## <a name="parameters"></a><span data-ttu-id="5490b-106">參數</span><span class="sxs-lookup"><span data-stu-id="5490b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="5490b-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="5490b-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="5490b-108">`ptr`[在]指向[IWbem 限定詞集實例的](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)指標。</span><span class="sxs-lookup"><span data-stu-id="5490b-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="5490b-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="5490b-109">Return value</span></span>

<span data-ttu-id="5490b-110">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，也可以將其定義為代碼中的常量：</span><span class="sxs-lookup"><span data-stu-id="5490b-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="5490b-111">持續性</span><span class="sxs-lookup"><span data-stu-id="5490b-111">Constant</span></span>  |<span data-ttu-id="5490b-112">值</span><span class="sxs-lookup"><span data-stu-id="5490b-112">Value</span></span>  |<span data-ttu-id="5490b-113">描述</span><span class="sxs-lookup"><span data-stu-id="5490b-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5490b-114">0</span><span class="sxs-lookup"><span data-stu-id="5490b-114">0</span></span> | <span data-ttu-id="5490b-115">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="5490b-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5490b-116">備註</span><span class="sxs-lookup"><span data-stu-id="5490b-116">Remarks</span></span>

<span data-ttu-id="5490b-117">此函數包裝對[IWbem 限定詞集：：結束枚舉方法的](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration)調用。</span><span class="sxs-lookup"><span data-stu-id="5490b-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="5490b-118">建議使用此調用，但不是必需的。</span><span class="sxs-lookup"><span data-stu-id="5490b-118">This call is recommended, but not required.</span></span> <span data-ttu-id="5490b-119">它立即釋放與枚舉關聯的資源。</span><span class="sxs-lookup"><span data-stu-id="5490b-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="5490b-120">需求</span><span class="sxs-lookup"><span data-stu-id="5490b-120">Requirements</span></span>  

<span data-ttu-id="5490b-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5490b-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="5490b-122">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5490b-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="5490b-123">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5490b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5490b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5490b-124">See also</span></span>

- [<span data-ttu-id="5490b-125">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="5490b-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
