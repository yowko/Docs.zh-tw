---
title: 'BeginMethodEnumeration 函式 (非受控 API 參考) '
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
ms.openlocfilehash: a72d61a572a0582ed8c03e56a8a9933c5f2775f0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719758"
---
# <a name="beginmethodenumeration-function"></a><span data-ttu-id="91e62-103">BeginMethodEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="91e62-103">BeginMethodEnumeration function</span></span>

<span data-ttu-id="91e62-104">開始物件的可用方法列舉。</span><span class="sxs-lookup"><span data-stu-id="91e62-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="91e62-105">語法</span><span class="sxs-lookup"><span data-stu-id="91e62-105">Syntax</span></span>  
  
```cpp
HRESULT BeginMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a><span data-ttu-id="91e62-106">參數</span><span class="sxs-lookup"><span data-stu-id="91e62-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="91e62-107">在此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="91e62-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="91e62-108">在 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="91e62-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="91e62-109">在所有方法的零 (0) 或指定列舉範圍的旗標。</span><span class="sxs-lookup"><span data-stu-id="91e62-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="91e62-110">下列旗標定義于 *WbemCli .h* 標頭檔中，您也可以在程式碼中將其定義為常數：</span><span class="sxs-lookup"><span data-stu-id="91e62-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="91e62-111">常數</span><span class="sxs-lookup"><span data-stu-id="91e62-111">Constant</span></span>  |<span data-ttu-id="91e62-112">值</span><span class="sxs-lookup"><span data-stu-id="91e62-112">Value</span></span>  |<span data-ttu-id="91e62-113">描述</span><span class="sxs-lookup"><span data-stu-id="91e62-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="91e62-114">0x10</span><span class="sxs-lookup"><span data-stu-id="91e62-114">0x10</span></span> | <span data-ttu-id="91e62-115">將列舉限制為類別本身中定義的方法。</span><span class="sxs-lookup"><span data-stu-id="91e62-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="91e62-116">0x20</span><span class="sxs-lookup"><span data-stu-id="91e62-116">0x20</span></span> | <span data-ttu-id="91e62-117">將列舉限制為繼承自基類的屬性。</span><span class="sxs-lookup"><span data-stu-id="91e62-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="91e62-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="91e62-118">Return value</span></span>

<span data-ttu-id="91e62-119">這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="91e62-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="91e62-120">常數</span><span class="sxs-lookup"><span data-stu-id="91e62-120">Constant</span></span>  |<span data-ttu-id="91e62-121">值</span><span class="sxs-lookup"><span data-stu-id="91e62-121">Value</span></span>  |<span data-ttu-id="91e62-122">描述</span><span class="sxs-lookup"><span data-stu-id="91e62-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="91e62-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="91e62-123">0x80041008</span></span> | <span data-ttu-id="91e62-124">`lEnnumFlags` 不是零，而且不是其中一個指定的旗標。</span><span class="sxs-lookup"><span data-stu-id="91e62-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="91e62-125">0</span><span class="sxs-lookup"><span data-stu-id="91e62-125">0</span></span> | <span data-ttu-id="91e62-126">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="91e62-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="91e62-127">備註</span><span class="sxs-lookup"><span data-stu-id="91e62-127">Remarks</span></span>

<span data-ttu-id="91e62-128">此函數會包裝對 [IWbemClassObject：： BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="91e62-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="91e62-129">只有當目前的物件是類別定義時，才支援這個方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="91e62-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="91e62-130">方法操作無法從指向實例的 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 指標使用。</span><span class="sxs-lookup"><span data-stu-id="91e62-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="91e62-131">針對指定的 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例，保證方法的列舉順序是不變的。</span><span class="sxs-lookup"><span data-stu-id="91e62-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="91e62-132">需求</span><span class="sxs-lookup"><span data-stu-id="91e62-132">Requirements</span></span>  

 <span data-ttu-id="91e62-133">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91e62-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91e62-134">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="91e62-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="91e62-135">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="91e62-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91e62-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91e62-136">See also</span></span>

- [<span data-ttu-id="91e62-137">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="91e62-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
