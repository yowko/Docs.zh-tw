---
title: 複製函式 （Unmanaged API 參考）
description: 複製函式會傳回目前的完整複製的新物件。
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80faf1a5a6297f5b105fdb609366f6774f8692b3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761644"
---
# <a name="clone-function"></a><span data-ttu-id="12eb7-103">Clone 函式</span><span class="sxs-lookup"><span data-stu-id="12eb7-103">Clone function</span></span>
<span data-ttu-id="12eb7-104">傳回屬於目前物件之完整複製品的新物件。</span><span class="sxs-lookup"><span data-stu-id="12eb7-104">Returns a new object that is a complete clone of the current object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="12eb7-105">語法</span><span class="sxs-lookup"><span data-stu-id="12eb7-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a><span data-ttu-id="12eb7-106">參數</span><span class="sxs-lookup"><span data-stu-id="12eb7-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="12eb7-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="12eb7-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="12eb7-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="12eb7-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppCopy`  
<span data-ttu-id="12eb7-109">[out]新的物件，是一份完整的獨立`ptr`。</span><span class="sxs-lookup"><span data-stu-id="12eb7-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="12eb7-110">此引數不可為`null`如果收到的目前物件的複本。</span><span class="sxs-lookup"><span data-stu-id="12eb7-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="12eb7-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="12eb7-111">Return value</span></span>

<span data-ttu-id="12eb7-112">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="12eb7-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="12eb7-113">常數</span><span class="sxs-lookup"><span data-stu-id="12eb7-113">Constant</span></span>  |<span data-ttu-id="12eb7-114">值</span><span class="sxs-lookup"><span data-stu-id="12eb7-114">Value</span></span>  |<span data-ttu-id="12eb7-115">描述</span><span class="sxs-lookup"><span data-stu-id="12eb7-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="12eb7-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="12eb7-116">0x80041001</span></span> | <span data-ttu-id="12eb7-117">已有一般失敗。</span><span class="sxs-lookup"><span data-stu-id="12eb7-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="12eb7-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="12eb7-118">0x80041008</span></span> | <span data-ttu-id="12eb7-119">`null` 已指定為參數，以及是不合法，在這種用法。</span><span class="sxs-lookup"><span data-stu-id="12eb7-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="12eb7-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="12eb7-120">0x80041006</span></span> | <span data-ttu-id="12eb7-121">沒有足夠的記憶體可供複製的物件。</span><span class="sxs-lookup"><span data-stu-id="12eb7-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="12eb7-122">0</span><span class="sxs-lookup"><span data-stu-id="12eb7-122">0</span></span> | <span data-ttu-id="12eb7-123">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="12eb7-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="12eb7-124">備註</span><span class="sxs-lookup"><span data-stu-id="12eb7-124">Remarks</span></span>

<span data-ttu-id="12eb7-125">此函式會包裝在呼叫[IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)方法。</span><span class="sxs-lookup"><span data-stu-id="12eb7-125">This function wraps a call to the [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="12eb7-126">複製的物件是 COM 物件的參考計數為 1。</span><span class="sxs-lookup"><span data-stu-id="12eb7-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="12eb7-127">需求</span><span class="sxs-lookup"><span data-stu-id="12eb7-127">Requirements</span></span>  
 <span data-ttu-id="12eb7-128">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="12eb7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12eb7-129">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="12eb7-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="12eb7-130">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="12eb7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12eb7-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12eb7-131">See also</span></span>

- [<span data-ttu-id="12eb7-132">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="12eb7-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
