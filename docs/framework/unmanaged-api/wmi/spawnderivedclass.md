---
title: 生成派生類函數（非託管 API 引用）
description: Spawn 派生類函數創建一個從物件派生的新物件。
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
ms.openlocfilehash: e9784f8a024c788823dc702794b2b86eea1827bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174845"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="78850-103">SpawnDerivedClass 函式</span><span class="sxs-lookup"><span data-stu-id="78850-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="78850-104">從指定的物件建立新的衍生類別物件。</span><span class="sxs-lookup"><span data-stu-id="78850-104">Creates a newly derived class object from a specified object.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="78850-105">語法</span><span class="sxs-lookup"><span data-stu-id="78850-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass);
```  

## <a name="parameters"></a><span data-ttu-id="78850-106">參數</span><span class="sxs-lookup"><span data-stu-id="78850-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="78850-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="78850-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="78850-108">[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="78850-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="78850-109">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="78850-109">[in] Reserved.</span></span> <span data-ttu-id="78850-110">此參數必須為 0。</span><span class="sxs-lookup"><span data-stu-id="78850-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="78850-111">[出]接收指向新類定義物件的指標。</span><span class="sxs-lookup"><span data-stu-id="78850-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="78850-112">如果發生錯誤，則不會返回新物件，並且`ppNewClass`未修改。</span><span class="sxs-lookup"><span data-stu-id="78850-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="78850-113">其值不能為`null`。</span><span class="sxs-lookup"><span data-stu-id="78850-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="78850-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="78850-114">Return value</span></span>

<span data-ttu-id="78850-115">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="78850-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="78850-116">持續性</span><span class="sxs-lookup"><span data-stu-id="78850-116">Constant</span></span>  |<span data-ttu-id="78850-117">值</span><span class="sxs-lookup"><span data-stu-id="78850-117">Value</span></span>  |<span data-ttu-id="78850-118">描述</span><span class="sxs-lookup"><span data-stu-id="78850-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="78850-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="78850-119">0x80041001</span></span> | <span data-ttu-id="78850-120">出現了一個普遍的失敗。</span><span class="sxs-lookup"><span data-stu-id="78850-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="78850-121">0 x80041016</span><span class="sxs-lookup"><span data-stu-id="78850-121">0x80041016</span></span> | <span data-ttu-id="78850-122">請求無效操作，例如從實例生成類。</span><span class="sxs-lookup"><span data-stu-id="78850-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="78850-123">源類未完全定義或註冊到 Windows 管理，因此不允許使用新的派生類。</span><span class="sxs-lookup"><span data-stu-id="78850-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="78850-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="78850-124">0x80041006</span></span> | <span data-ttu-id="78850-125">可用的記憶體不足，無法完成作業。</span><span class="sxs-lookup"><span data-stu-id="78850-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="78850-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="78850-126">0x80041008</span></span> | <span data-ttu-id="78850-127">`ppNewClass` 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="78850-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="78850-128">0</span><span class="sxs-lookup"><span data-stu-id="78850-128">0</span></span> | <span data-ttu-id="78850-129">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="78850-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="78850-130">備註</span><span class="sxs-lookup"><span data-stu-id="78850-130">Remarks</span></span>

<span data-ttu-id="78850-131">此函數將調用包起來到[IWbem ClassObject：：spawn派生類](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)方法。</span><span class="sxs-lookup"><span data-stu-id="78850-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="78850-132">`ptr`必須是成為生成物件的父類的類定義。</span><span class="sxs-lookup"><span data-stu-id="78850-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="78850-133">返回的物件將成為當前物件的子類。</span><span class="sxs-lookup"><span data-stu-id="78850-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="78850-134">返回`ppNewClass`的新物件將自動成為當前物件的子類。</span><span class="sxs-lookup"><span data-stu-id="78850-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="78850-135">無法重寫此行為。</span><span class="sxs-lookup"><span data-stu-id="78850-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="78850-136">沒有其他方法可以創建子類（派生類）。</span><span class="sxs-lookup"><span data-stu-id="78850-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="78850-137">需求</span><span class="sxs-lookup"><span data-stu-id="78850-137">Requirements</span></span>  
 <span data-ttu-id="78850-138">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="78850-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78850-139">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="78850-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="78850-140">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="78850-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78850-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78850-141">See also</span></span>

- [<span data-ttu-id="78850-142">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="78850-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
