---
title: 結束方法枚舉函數（非託管 API 引用）
description: EndMethodEee）計數函數終止方法枚舉序列。
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 63667d0668f905ded2aedd961be0d1831faf838c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175001"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="decd1-103">EndMethodEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="decd1-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="decd1-104">終止以調用[BeginMethodEee 計算函數](beginmethodenumeration.md)開始的枚舉序列。</span><span class="sxs-lookup"><span data-stu-id="decd1-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="decd1-105">語法</span><span class="sxs-lookup"><span data-stu-id="decd1-105">Syntax</span></span>  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```  

## <a name="parameters"></a><span data-ttu-id="decd1-106">參數</span><span class="sxs-lookup"><span data-stu-id="decd1-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="decd1-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="decd1-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="decd1-108">[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="decd1-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="decd1-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="decd1-109">Return value</span></span>

<span data-ttu-id="decd1-110">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="decd1-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="decd1-111">持續性</span><span class="sxs-lookup"><span data-stu-id="decd1-111">Constant</span></span>  |<span data-ttu-id="decd1-112">值</span><span class="sxs-lookup"><span data-stu-id="decd1-112">Value</span></span>  |<span data-ttu-id="decd1-113">描述</span><span class="sxs-lookup"><span data-stu-id="decd1-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="decd1-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="decd1-114">0x8004101d</span></span> | <span data-ttu-id="decd1-115">發生內部錯誤。</span><span class="sxs-lookup"><span data-stu-id="decd1-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="decd1-116">0</span><span class="sxs-lookup"><span data-stu-id="decd1-116">0</span></span> | <span data-ttu-id="decd1-117">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="decd1-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="decd1-118">備註</span><span class="sxs-lookup"><span data-stu-id="decd1-118">Remarks</span></span>

<span data-ttu-id="decd1-119">此函數將調用包起來到[IWbemClassObject：：結束方法枚舉](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration)方法。</span><span class="sxs-lookup"><span data-stu-id="decd1-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="decd1-120">調用方使用[BeginMethodEee 枚舉函數](beginmethodenumeration.md)開始枚舉序列，然後調用[NextMethod 函數](nextmethod.md )，直到`WBEM_S_NO_MORE_DATA`方法返回 。</span><span class="sxs-lookup"><span data-stu-id="decd1-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="decd1-121">調用方通過調用`EndMethodEnumeration`完成序列。</span><span class="sxs-lookup"><span data-stu-id="decd1-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="decd1-122">調用方可能通過隨時調用`EndMethodEnumeration`來提前終止枚舉。</span><span class="sxs-lookup"><span data-stu-id="decd1-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="decd1-123">需求</span><span class="sxs-lookup"><span data-stu-id="decd1-123">Requirements</span></span>  
 <span data-ttu-id="decd1-124">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="decd1-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="decd1-125">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="decd1-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="decd1-126">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="decd1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="decd1-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="decd1-127">See also</span></span>

- [<span data-ttu-id="decd1-128">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="decd1-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
