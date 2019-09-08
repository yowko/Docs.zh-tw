---
title: SpawnDerivedClass 函式（非受控 API 參考）
description: SpawnDerivedClass 函數會建立衍生自物件的新物件。
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c213f311f1af1e56d0ce24eba3b76f33be541323
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798224"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="07f0b-103">SpawnDerivedClass 函式</span><span class="sxs-lookup"><span data-stu-id="07f0b-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="07f0b-104">從指定的物件建立新的衍生類別物件。</span><span class="sxs-lookup"><span data-stu-id="07f0b-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="07f0b-105">語法</span><span class="sxs-lookup"><span data-stu-id="07f0b-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="07f0b-106">參數</span><span class="sxs-lookup"><span data-stu-id="07f0b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="07f0b-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="07f0b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="07f0b-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="07f0b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="07f0b-109">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="07f0b-109">[in] Reserved.</span></span> <span data-ttu-id="07f0b-110">這個參數必須是0。</span><span class="sxs-lookup"><span data-stu-id="07f0b-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="07f0b-111">脫銷接收新類別定義物件的指標。</span><span class="sxs-lookup"><span data-stu-id="07f0b-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="07f0b-112">如果發生錯誤，則不會傳回新的物件，且`ppNewClass`會將其保留為未修改。</span><span class="sxs-lookup"><span data-stu-id="07f0b-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="07f0b-113">其值不能`null`是。</span><span class="sxs-lookup"><span data-stu-id="07f0b-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="07f0b-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="07f0b-114">Return value</span></span>

<span data-ttu-id="07f0b-115">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="07f0b-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="07f0b-116">常數</span><span class="sxs-lookup"><span data-stu-id="07f0b-116">Constant</span></span>  |<span data-ttu-id="07f0b-117">值</span><span class="sxs-lookup"><span data-stu-id="07f0b-117">Value</span></span>  |<span data-ttu-id="07f0b-118">描述</span><span class="sxs-lookup"><span data-stu-id="07f0b-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="07f0b-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="07f0b-119">0x80041001</span></span> | <span data-ttu-id="07f0b-120">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="07f0b-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="07f0b-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="07f0b-121">0x80041016</span></span> | <span data-ttu-id="07f0b-122">要求的作業無效（例如從實例中產生類別）。</span><span class="sxs-lookup"><span data-stu-id="07f0b-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="07f0b-123">來源類別並未完整定義或在 Windows 管理中註冊，因此不允許新的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="07f0b-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="07f0b-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="07f0b-124">0x80041006</span></span> | <span data-ttu-id="07f0b-125">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="07f0b-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="07f0b-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="07f0b-126">0x80041008</span></span> | <span data-ttu-id="07f0b-127">`ppNewClass` 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="07f0b-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="07f0b-128">0</span><span class="sxs-lookup"><span data-stu-id="07f0b-128">0</span></span> | <span data-ttu-id="07f0b-129">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="07f0b-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="07f0b-130">備註</span><span class="sxs-lookup"><span data-stu-id="07f0b-130">Remarks</span></span>

<span data-ttu-id="07f0b-131">此函式會包裝對[IWbemClassObject：： SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="07f0b-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="07f0b-132">`ptr`必須是類別定義，才會成為產生之物件的父類別。</span><span class="sxs-lookup"><span data-stu-id="07f0b-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="07f0b-133">傳回的物件會變成目前物件的子類別。</span><span class="sxs-lookup"><span data-stu-id="07f0b-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="07f0b-134">在中`ppNewClass`傳回的新物件會自動成為目前物件的子類別。</span><span class="sxs-lookup"><span data-stu-id="07f0b-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="07f0b-135">無法覆寫此行為。</span><span class="sxs-lookup"><span data-stu-id="07f0b-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="07f0b-136">沒有其他方法可建立子類別（衍生類別）。</span><span class="sxs-lookup"><span data-stu-id="07f0b-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="07f0b-137">需求</span><span class="sxs-lookup"><span data-stu-id="07f0b-137">Requirements</span></span>  
 <span data-ttu-id="07f0b-138">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07f0b-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07f0b-139">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="07f0b-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="07f0b-140">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="07f0b-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07f0b-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07f0b-141">See also</span></span>

- [<span data-ttu-id="07f0b-142">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="07f0b-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
