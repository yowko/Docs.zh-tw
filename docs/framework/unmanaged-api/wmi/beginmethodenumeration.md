---
title: BeginMethodEnumeration 函式 （Unmanaged API 參考）
description: BeginMethodEnumeration 函式開頭物件的方法的列舉
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d6de2a5ff4d2743c7aca2e46b3af848138c15fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158778"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="79ce8-103">BeginEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="79ce8-103">BeginEnumeration function</span></span>
<span data-ttu-id="79ce8-104">開始列舉型別物件的可用方法。</span><span class="sxs-lookup"><span data-stu-id="79ce8-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="79ce8-105">語法</span><span class="sxs-lookup"><span data-stu-id="79ce8-105">Syntax</span></span>  
  
``` 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="79ce8-106">參數</span><span class="sxs-lookup"><span data-stu-id="79ce8-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="79ce8-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="79ce8-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="79ce8-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="79ce8-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="79ce8-109">[in]所有的方法，或指定的列舉型別範圍的旗標，為零 (0)。</span><span class="sxs-lookup"><span data-stu-id="79ce8-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="79ce8-110">中所定義的下列旗標*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="79ce8-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="79ce8-111">常數</span><span class="sxs-lookup"><span data-stu-id="79ce8-111">Constant</span></span>  |<span data-ttu-id="79ce8-112">值</span><span class="sxs-lookup"><span data-stu-id="79ce8-112">Value</span></span>  |<span data-ttu-id="79ce8-113">描述</span><span class="sxs-lookup"><span data-stu-id="79ce8-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="79ce8-114">0x10</span><span class="sxs-lookup"><span data-stu-id="79ce8-114">0x10</span></span> | <span data-ttu-id="79ce8-115">限制類別本身中定義的方法來列舉型別。</span><span class="sxs-lookup"><span data-stu-id="79ce8-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="79ce8-116">0x20</span><span class="sxs-lookup"><span data-stu-id="79ce8-116">0x20</span></span> | <span data-ttu-id="79ce8-117">限制列舉型別繼承自基底類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="79ce8-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="79ce8-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="79ce8-118">Return value</span></span>

<span data-ttu-id="79ce8-119">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="79ce8-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="79ce8-120">常數</span><span class="sxs-lookup"><span data-stu-id="79ce8-120">Constant</span></span>  |<span data-ttu-id="79ce8-121">值</span><span class="sxs-lookup"><span data-stu-id="79ce8-121">Value</span></span>  |<span data-ttu-id="79ce8-122">描述</span><span class="sxs-lookup"><span data-stu-id="79ce8-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="79ce8-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="79ce8-123">0x80041008</span></span> | <span data-ttu-id="79ce8-124">`lEnnumFlags` 為非零，並不是其中一個指定的旗標。</span><span class="sxs-lookup"><span data-stu-id="79ce8-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="79ce8-125">0</span><span class="sxs-lookup"><span data-stu-id="79ce8-125">0</span></span> | <span data-ttu-id="79ce8-126">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="79ce8-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="79ce8-127">備註</span><span class="sxs-lookup"><span data-stu-id="79ce8-127">Remarks</span></span>

<span data-ttu-id="79ce8-128">此函式會包裝在呼叫[IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration)方法。</span><span class="sxs-lookup"><span data-stu-id="79ce8-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="79ce8-129">如果目前的物件類別定義才支援這個方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="79ce8-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="79ce8-130">方法操作不是可從[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指標，指向 執行個體。</span><span class="sxs-lookup"><span data-stu-id="79ce8-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="79ce8-131">方法會列舉在其中的順序保證為指定的執行個體而異[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)。</span><span class="sxs-lookup"><span data-stu-id="79ce8-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="79ce8-132">需求</span><span class="sxs-lookup"><span data-stu-id="79ce8-132">Requirements</span></span>  
 <span data-ttu-id="79ce8-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="79ce8-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79ce8-134">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="79ce8-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="79ce8-135">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="79ce8-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79ce8-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79ce8-136">See also</span></span>

- [<span data-ttu-id="79ce8-137">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="79ce8-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
