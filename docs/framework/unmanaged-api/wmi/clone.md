---
title: 克隆功能（非託管 API 引用）
description: Clone 函數返回一個新物件，該物件是當前物件的完整克隆。
ms.date: 11/06/2017
api_name:
- Clone
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Clone
helpviewer_keywords:
- Clone function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: cb4951a1f289417482bfa1287028cc66349a5938
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176847"
---
# <a name="clone-function"></a><span data-ttu-id="84459-103">Clone 函式</span><span class="sxs-lookup"><span data-stu-id="84459-103">Clone function</span></span>
<span data-ttu-id="84459-104">傳回屬於目前物件之完整複製品的新物件。</span><span class="sxs-lookup"><span data-stu-id="84459-104">Returns a new object that is a complete clone of the current object.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="84459-105">語法</span><span class="sxs-lookup"><span data-stu-id="84459-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [out] IWbemClassObject**  ppCopy
);
```  

## <a name="parameters"></a><span data-ttu-id="84459-106">參數</span><span class="sxs-lookup"><span data-stu-id="84459-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="84459-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="84459-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="84459-108">[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="84459-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppCopy`  
<span data-ttu-id="84459-109">[出]一個新物件，它是 完全孤獨的`ptr`。</span><span class="sxs-lookup"><span data-stu-id="84459-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="84459-110">`null`如果此參數收到當前物件的副本，則不能。</span><span class="sxs-lookup"><span data-stu-id="84459-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="84459-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="84459-111">Return value</span></span>

<span data-ttu-id="84459-112">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="84459-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="84459-113">持續性</span><span class="sxs-lookup"><span data-stu-id="84459-113">Constant</span></span>  |<span data-ttu-id="84459-114">值</span><span class="sxs-lookup"><span data-stu-id="84459-114">Value</span></span>  |<span data-ttu-id="84459-115">描述</span><span class="sxs-lookup"><span data-stu-id="84459-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="84459-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="84459-116">0x80041001</span></span> | <span data-ttu-id="84459-117">出現了一個普遍的失敗。</span><span class="sxs-lookup"><span data-stu-id="84459-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="84459-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="84459-118">0x80041008</span></span> | <span data-ttu-id="84459-119">`null`被指定為參數，在此用法中不合法。</span><span class="sxs-lookup"><span data-stu-id="84459-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="84459-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="84459-120">0x80041006</span></span> | <span data-ttu-id="84459-121">沒有足夠的記憶體可用於克隆物件。</span><span class="sxs-lookup"><span data-stu-id="84459-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="84459-122">0</span><span class="sxs-lookup"><span data-stu-id="84459-122">0</span></span> | <span data-ttu-id="84459-123">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="84459-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="84459-124">備註</span><span class="sxs-lookup"><span data-stu-id="84459-124">Remarks</span></span>

<span data-ttu-id="84459-125">此函數包裝對[IWbem ClassObject：：克隆](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)方法的調用。</span><span class="sxs-lookup"><span data-stu-id="84459-125">This function wraps a call to the [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="84459-126">克隆的物件是引用計數為 1 的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="84459-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="84459-127">需求</span><span class="sxs-lookup"><span data-stu-id="84459-127">Requirements</span></span>  
 <span data-ttu-id="84459-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84459-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84459-129">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="84459-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="84459-130">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="84459-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84459-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84459-131">See also</span></span>

- [<span data-ttu-id="84459-132">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="84459-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
