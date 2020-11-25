---
title: 'EndMethodEnumeration 函式 (非受控 API 參考) '
description: EndMethodEnumeration 函式會終止方法列舉序列。
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
ms.openlocfilehash: 82f50530967699427d8a00b1c9f518b639273626
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708058"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="a80a5-103">EndMethodEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="a80a5-103">EndMethodEnumeration function</span></span>

<span data-ttu-id="a80a5-104">終止透過呼叫 [BeginMethodEnumeration](beginmethodenumeration.md)函式開始的列舉序列。</span><span class="sxs-lookup"><span data-stu-id="a80a5-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="a80a5-105">語法</span><span class="sxs-lookup"><span data-stu-id="a80a5-105">Syntax</span></span>  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```  

## <a name="parameters"></a><span data-ttu-id="a80a5-106">參數</span><span class="sxs-lookup"><span data-stu-id="a80a5-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a80a5-107">在此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="a80a5-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a80a5-108">在 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="a80a5-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="a80a5-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="a80a5-109">Return value</span></span>

<span data-ttu-id="a80a5-110">這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="a80a5-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a80a5-111">常數</span><span class="sxs-lookup"><span data-stu-id="a80a5-111">Constant</span></span>  |<span data-ttu-id="a80a5-112">值</span><span class="sxs-lookup"><span data-stu-id="a80a5-112">Value</span></span>  |<span data-ttu-id="a80a5-113">描述</span><span class="sxs-lookup"><span data-stu-id="a80a5-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="a80a5-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="a80a5-114">0x8004101d</span></span> | <span data-ttu-id="a80a5-115">發生內部錯誤。</span><span class="sxs-lookup"><span data-stu-id="a80a5-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a80a5-116">0</span><span class="sxs-lookup"><span data-stu-id="a80a5-116">0</span></span> | <span data-ttu-id="a80a5-117">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="a80a5-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a80a5-118">備註</span><span class="sxs-lookup"><span data-stu-id="a80a5-118">Remarks</span></span>

<span data-ttu-id="a80a5-119">此函數會包裝對 [IWbemClassObject：： EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a80a5-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="a80a5-120">呼叫端會使用 [BeginMethodEnumeration](beginmethodenumeration.md)函式來開始列舉順序，然後在方法傳回之前呼叫 [NextMethod 函數](nextmethod.md ) `WBEM_S_NO_MORE_DATA` 。</span><span class="sxs-lookup"><span data-stu-id="a80a5-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="a80a5-121">呼叫端會選擇性地完成序列 `EndMethodEnumeration` 。</span><span class="sxs-lookup"><span data-stu-id="a80a5-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="a80a5-122">呼叫端可以在任何時間呼叫，提早終止列舉 `EndMethodEnumeration` 。</span><span class="sxs-lookup"><span data-stu-id="a80a5-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="a80a5-123">需求</span><span class="sxs-lookup"><span data-stu-id="a80a5-123">Requirements</span></span>  

 <span data-ttu-id="a80a5-124">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a80a5-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a80a5-125">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="a80a5-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a80a5-126">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a80a5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a80a5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a80a5-127">See also</span></span>

- [<span data-ttu-id="a80a5-128">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="a80a5-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
