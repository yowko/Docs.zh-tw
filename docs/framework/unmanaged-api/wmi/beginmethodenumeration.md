---
title: BeginMethodEnumeration 函式（非受控 API 參考）
description: BeginMethodEnumeration 函式會開始列舉物件的方法
ms.date: 11/06/2017
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: be1e86e0b760ab403cf42ac19da03f84769a85cf
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884419"
---
# <a name="beginmethodenumeration-function"></a><span data-ttu-id="f2a5e-103">BeginMethodEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="f2a5e-103">BeginMethodEnumeration function</span></span>
<span data-ttu-id="f2a5e-104">開始可供物件使用之方法的列舉。</span><span class="sxs-lookup"><span data-stu-id="f2a5e-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f2a5e-105">語法</span><span class="sxs-lookup"><span data-stu-id="f2a5e-105">Syntax</span></span>  
  
```cpp 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="f2a5e-106">參數</span><span class="sxs-lookup"><span data-stu-id="f2a5e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f2a5e-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="f2a5e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f2a5e-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="f2a5e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="f2a5e-109">在所有方法都是零（0），或指定列舉範圍的旗標。</span><span class="sxs-lookup"><span data-stu-id="f2a5e-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="f2a5e-110">下列旗標定義于*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="f2a5e-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="f2a5e-111">常數</span><span class="sxs-lookup"><span data-stu-id="f2a5e-111">Constant</span></span>  |<span data-ttu-id="f2a5e-112">{2&gt;值&lt;2}</span><span class="sxs-lookup"><span data-stu-id="f2a5e-112">Value</span></span>  |<span data-ttu-id="f2a5e-113">描述</span><span class="sxs-lookup"><span data-stu-id="f2a5e-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="f2a5e-114">0x10</span><span class="sxs-lookup"><span data-stu-id="f2a5e-114">0x10</span></span> | <span data-ttu-id="f2a5e-115">將列舉限制為類別本身中定義的方法。</span><span class="sxs-lookup"><span data-stu-id="f2a5e-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="f2a5e-116">0x20</span><span class="sxs-lookup"><span data-stu-id="f2a5e-116">0x20</span></span> | <span data-ttu-id="f2a5e-117">將列舉限制為繼承自基類的屬性。</span><span class="sxs-lookup"><span data-stu-id="f2a5e-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="f2a5e-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="f2a5e-118">Return value</span></span>

<span data-ttu-id="f2a5e-119">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="f2a5e-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f2a5e-120">常數</span><span class="sxs-lookup"><span data-stu-id="f2a5e-120">Constant</span></span>  |<span data-ttu-id="f2a5e-121">{2&gt;值&lt;2}</span><span class="sxs-lookup"><span data-stu-id="f2a5e-121">Value</span></span>  |<span data-ttu-id="f2a5e-122">描述</span><span class="sxs-lookup"><span data-stu-id="f2a5e-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f2a5e-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f2a5e-123">0x80041008</span></span> | <span data-ttu-id="f2a5e-124">`lEnnumFlags` 為非零，而且不是其中一個指定的旗標。</span><span class="sxs-lookup"><span data-stu-id="f2a5e-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f2a5e-125">0</span><span class="sxs-lookup"><span data-stu-id="f2a5e-125">0</span></span> | <span data-ttu-id="f2a5e-126">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="f2a5e-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f2a5e-127">備註</span><span class="sxs-lookup"><span data-stu-id="f2a5e-127">Remarks</span></span>

<span data-ttu-id="f2a5e-128">此函式會包裝對[IWbemClassObject：： BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f2a5e-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="f2a5e-129">只有當目前的物件是類別定義時，才支援這個方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="f2a5e-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="f2a5e-130">方法操作無法從指向實例的[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指標使用。</span><span class="sxs-lookup"><span data-stu-id="f2a5e-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="f2a5e-131">針對指定的[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例，保證方法列舉的順序是不變的。</span><span class="sxs-lookup"><span data-stu-id="f2a5e-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="f2a5e-132">需求</span><span class="sxs-lookup"><span data-stu-id="f2a5e-132">Requirements</span></span>  
 <span data-ttu-id="f2a5e-133">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2a5e-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2a5e-134">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="f2a5e-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f2a5e-135">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f2a5e-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a5e-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="f2a5e-136">See also</span></span>

- [<span data-ttu-id="f2a5e-137">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="f2a5e-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
