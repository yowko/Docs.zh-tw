---
title: Clone 函式（非受控 API 參考）
description: 複製函式會傳回新的物件，它是目前的完整複本。
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
ms.openlocfilehash: 5957f591dca7df30178660eb3fb074567c285715
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798717"
---
# <a name="clone-function"></a><span data-ttu-id="67202-103">Clone 函式</span><span class="sxs-lookup"><span data-stu-id="67202-103">Clone function</span></span>
<span data-ttu-id="67202-104">傳回屬於目前物件之完整複製品的新物件。</span><span class="sxs-lookup"><span data-stu-id="67202-104">Returns a new object that is a complete clone of the current object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="67202-105">語法</span><span class="sxs-lookup"><span data-stu-id="67202-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a><span data-ttu-id="67202-106">參數</span><span class="sxs-lookup"><span data-stu-id="67202-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="67202-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="67202-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="67202-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="67202-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppCopy`  
<span data-ttu-id="67202-109">脫銷新的物件，它是的完整獨立`ptr`。</span><span class="sxs-lookup"><span data-stu-id="67202-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="67202-110">如果這個引數`null`收到目前物件的複本，就不能是。</span><span class="sxs-lookup"><span data-stu-id="67202-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="67202-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="67202-111">Return value</span></span>

<span data-ttu-id="67202-112">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="67202-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="67202-113">常數</span><span class="sxs-lookup"><span data-stu-id="67202-113">Constant</span></span>  |<span data-ttu-id="67202-114">值</span><span class="sxs-lookup"><span data-stu-id="67202-114">Value</span></span>  |<span data-ttu-id="67202-115">描述</span><span class="sxs-lookup"><span data-stu-id="67202-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="67202-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="67202-116">0x80041001</span></span> | <span data-ttu-id="67202-117">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="67202-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="67202-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="67202-118">0x80041008</span></span> | <span data-ttu-id="67202-119">`null`已指定為參數，而且在此用法中不合法。</span><span class="sxs-lookup"><span data-stu-id="67202-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="67202-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="67202-120">0x80041006</span></span> | <span data-ttu-id="67202-121">沒有足夠的記憶體可複製物件。</span><span class="sxs-lookup"><span data-stu-id="67202-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="67202-122">0</span><span class="sxs-lookup"><span data-stu-id="67202-122">0</span></span> | <span data-ttu-id="67202-123">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="67202-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="67202-124">備註</span><span class="sxs-lookup"><span data-stu-id="67202-124">Remarks</span></span>

<span data-ttu-id="67202-125">此函式會包裝對[IWbemClassObject：： Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="67202-125">This function wraps a call to the [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="67202-126">複製的物件是參考計數為1的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="67202-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="67202-127">需求</span><span class="sxs-lookup"><span data-stu-id="67202-127">Requirements</span></span>  
 <span data-ttu-id="67202-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67202-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67202-129">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="67202-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="67202-130">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="67202-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67202-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67202-131">See also</span></span>

- [<span data-ttu-id="67202-132">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="67202-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
