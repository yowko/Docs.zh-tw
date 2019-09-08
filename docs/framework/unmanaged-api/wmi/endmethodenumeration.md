---
title: EndMethodEnumeration 函式（非受控 API 參考）
description: EndMethodEnumeration 函數會終止方法列舉序列。
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cdcf49bd748a423b1cebfba88644aa961f1c7b65
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799351"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="17d9b-103">EndMethodEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="17d9b-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="17d9b-104">結束通話[BeginMethodEnumeration 函數](beginmethodenumeration.md)所啟動的列舉序列。</span><span class="sxs-lookup"><span data-stu-id="17d9b-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="17d9b-105">語法</span><span class="sxs-lookup"><span data-stu-id="17d9b-105">Syntax</span></span>  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="17d9b-106">參數</span><span class="sxs-lookup"><span data-stu-id="17d9b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="17d9b-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="17d9b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="17d9b-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="17d9b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="17d9b-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="17d9b-109">Return value</span></span>

<span data-ttu-id="17d9b-110">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="17d9b-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="17d9b-111">常數</span><span class="sxs-lookup"><span data-stu-id="17d9b-111">Constant</span></span>  |<span data-ttu-id="17d9b-112">值</span><span class="sxs-lookup"><span data-stu-id="17d9b-112">Value</span></span>  |<span data-ttu-id="17d9b-113">說明</span><span class="sxs-lookup"><span data-stu-id="17d9b-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="17d9b-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="17d9b-114">0x8004101d</span></span> | <span data-ttu-id="17d9b-115">發生內部錯誤。</span><span class="sxs-lookup"><span data-stu-id="17d9b-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="17d9b-116">0</span><span class="sxs-lookup"><span data-stu-id="17d9b-116">0</span></span> | <span data-ttu-id="17d9b-117">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="17d9b-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="17d9b-118">備註</span><span class="sxs-lookup"><span data-stu-id="17d9b-118">Remarks</span></span>

<span data-ttu-id="17d9b-119">此函式會包裝對[IWbemClassObject：： EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="17d9b-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="17d9b-120">呼叫端會使用[BeginMethodEnumeration 函數](beginmethodenumeration.md)開始列舉序列，然後呼叫[NextMethod](nextmethod.md )函式，直到方法`WBEM_S_NO_MORE_DATA`傳回為止。</span><span class="sxs-lookup"><span data-stu-id="17d9b-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="17d9b-121">呼叫端選擇性地透過呼叫`EndMethodEnumeration`來完成序列。</span><span class="sxs-lookup"><span data-stu-id="17d9b-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="17d9b-122">呼叫端可能會在任何時間呼叫`EndMethodEnumeration` ，提早終止列舉。</span><span class="sxs-lookup"><span data-stu-id="17d9b-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="17d9b-123">需求</span><span class="sxs-lookup"><span data-stu-id="17d9b-123">Requirements</span></span>  
 <span data-ttu-id="17d9b-124">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17d9b-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17d9b-125">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="17d9b-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="17d9b-126">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="17d9b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d9b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17d9b-127">See also</span></span>

- [<span data-ttu-id="17d9b-128">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="17d9b-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
