---
title: 'QualifierSet_EndEnumeration 函式 (非受控 API 參考) '
description: QualifierSet_EndEnumeration 函式會終止列舉。
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
ms.openlocfilehash: 2739003fc9c1f93d379e4a59338cbef7a1a0f135
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726739"
---
# <a name="qualifierset_endenumeration-function"></a><span data-ttu-id="9d0cd-103">QualifierSet_EndEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="9d0cd-103">QualifierSet_EndEnumeration function</span></span>

<span data-ttu-id="9d0cd-104">終止使用 [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) 函式的呼叫開始的列舉。</span><span class="sxs-lookup"><span data-stu-id="9d0cd-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9d0cd-105">語法</span><span class="sxs-lookup"><span data-stu-id="9d0cd-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr
);
```  

## <a name="parameters"></a><span data-ttu-id="9d0cd-106">參數</span><span class="sxs-lookup"><span data-stu-id="9d0cd-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="9d0cd-107">在此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="9d0cd-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="9d0cd-108">`ptr` 在 [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="9d0cd-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="9d0cd-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="9d0cd-109">Return value</span></span>

<span data-ttu-id="9d0cd-110">這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它定義為常數：</span><span class="sxs-lookup"><span data-stu-id="9d0cd-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="9d0cd-111">常數</span><span class="sxs-lookup"><span data-stu-id="9d0cd-111">Constant</span></span>  |<span data-ttu-id="9d0cd-112">值</span><span class="sxs-lookup"><span data-stu-id="9d0cd-112">Value</span></span>  |<span data-ttu-id="9d0cd-113">描述</span><span class="sxs-lookup"><span data-stu-id="9d0cd-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="9d0cd-114">0</span><span class="sxs-lookup"><span data-stu-id="9d0cd-114">0</span></span> | <span data-ttu-id="9d0cd-115">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="9d0cd-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="9d0cd-116">備註</span><span class="sxs-lookup"><span data-stu-id="9d0cd-116">Remarks</span></span>

<span data-ttu-id="9d0cd-117">此函數會包裝對 [IWbemQualifierSet：： EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="9d0cd-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="9d0cd-118">這是建議的呼叫，但不是必要的。</span><span class="sxs-lookup"><span data-stu-id="9d0cd-118">This call is recommended, but not required.</span></span> <span data-ttu-id="9d0cd-119">它會立即釋放與列舉相關聯的資源。</span><span class="sxs-lookup"><span data-stu-id="9d0cd-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="9d0cd-120">需求</span><span class="sxs-lookup"><span data-stu-id="9d0cd-120">Requirements</span></span>  

<span data-ttu-id="9d0cd-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9d0cd-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="9d0cd-122">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="9d0cd-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="9d0cd-123">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9d0cd-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d0cd-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d0cd-124">See also</span></span>

- [<span data-ttu-id="9d0cd-125">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="9d0cd-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
