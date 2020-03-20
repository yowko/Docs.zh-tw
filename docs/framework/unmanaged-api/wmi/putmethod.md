---
title: PutMethod 函數（非託管 API 引用）
description: PutMethod 函數創建一個方法。
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 93347b7290211b5d62829604678261fdf4da1ec3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174910"
---
# <a name="putmethod-function"></a><span data-ttu-id="654a9-103">PutMethod 函式</span><span class="sxs-lookup"><span data-stu-id="654a9-103">PutMethod function</span></span>
<span data-ttu-id="654a9-104">建立方法。</span><span class="sxs-lookup"><span data-stu-id="654a9-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="654a9-105">語法</span><span class="sxs-lookup"><span data-stu-id="654a9-105">Syntax</span></span>  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*  ptr,
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
);
```  

## <a name="parameters"></a><span data-ttu-id="654a9-106">參數</span><span class="sxs-lookup"><span data-stu-id="654a9-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="654a9-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="654a9-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="654a9-108">[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="654a9-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="654a9-109">[在]要創建的方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="654a9-109">[in] The name of the method to create.</span></span>

`lFlags`  
<span data-ttu-id="654a9-110">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="654a9-110">[in] Reserved.</span></span> <span data-ttu-id="654a9-111">此參數必須為 0。</span><span class="sxs-lookup"><span data-stu-id="654a9-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="654a9-112">[在]指向包含方法參數[的__Parameters系統類](/windows/desktop/WmiSdk/--parameters)`in`副本的指標。</span><span class="sxs-lookup"><span data-stu-id="654a9-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="654a9-113">如果設置為`null`，則忽略此參數。</span><span class="sxs-lookup"><span data-stu-id="654a9-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="654a9-114">[在] 指向包含方法參數[的__Parameters系統類](/windows/desktop/WmiSdk/--parameters)`out`副本的指標。</span><span class="sxs-lookup"><span data-stu-id="654a9-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="654a9-115">如果設置為`null`，則忽略此參數。</span><span class="sxs-lookup"><span data-stu-id="654a9-115">This parameter is ignored if set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="654a9-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="654a9-116">Return value</span></span>

<span data-ttu-id="654a9-117">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="654a9-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="654a9-118">持續性</span><span class="sxs-lookup"><span data-stu-id="654a9-118">Constant</span></span>  |<span data-ttu-id="654a9-119">值</span><span class="sxs-lookup"><span data-stu-id="654a9-119">Value</span></span>  |<span data-ttu-id="654a9-120">描述</span><span class="sxs-lookup"><span data-stu-id="654a9-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="654a9-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="654a9-121">0x80041008</span></span> | <span data-ttu-id="654a9-122">一個或多個參數無效。</span><span class="sxs-lookup"><span data-stu-id="654a9-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="654a9-123">0 x80041043</span><span class="sxs-lookup"><span data-stu-id="654a9-123">0x80041043</span></span> | <span data-ttu-id="654a9-124">在`[in, out]` *pInSignature*和*pOutSignature*物件中指定的方法參數具有不同的限定詞。</span><span class="sxs-lookup"><span data-stu-id="654a9-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="654a9-125">0 x80041036</span><span class="sxs-lookup"><span data-stu-id="654a9-125">0x80041036</span></span> | <span data-ttu-id="654a9-126">缺少**ID**限定詞的規範的方法參數。</span><span class="sxs-lookup"><span data-stu-id="654a9-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="654a9-127">0 x80041038</span><span class="sxs-lookup"><span data-stu-id="654a9-127">0x80041038</span></span> | <span data-ttu-id="654a9-128">分配給方法參數的 ID 系列不是連續的，也不是從 0 開始的。</span><span class="sxs-lookup"><span data-stu-id="654a9-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="654a9-129">0 x80041039</span><span class="sxs-lookup"><span data-stu-id="654a9-129">0x80041039</span></span> | <span data-ttu-id="654a9-130">方法的傳回值具有**ID**限定詞。</span><span class="sxs-lookup"><span data-stu-id="654a9-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="654a9-131">0 x80041034</span><span class="sxs-lookup"><span data-stu-id="654a9-131">0x80041034</span></span> | <span data-ttu-id="654a9-132">嘗試從父類重用現有方法名稱，並且簽名不匹配。</span><span class="sxs-lookup"><span data-stu-id="654a9-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="654a9-133">0</span><span class="sxs-lookup"><span data-stu-id="654a9-133">0</span></span> | <span data-ttu-id="654a9-134">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="654a9-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="654a9-135">備註</span><span class="sxs-lookup"><span data-stu-id="654a9-135">Remarks</span></span>

<span data-ttu-id="654a9-136">此函數包裝對[IWbemClassObject：:PutMethod 方法的](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)調用。</span><span class="sxs-lookup"><span data-stu-id="654a9-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="654a9-137">僅當是 CIM 類定義`ptr`時，才支援此方法調用。</span><span class="sxs-lookup"><span data-stu-id="654a9-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="654a9-138">方法操作從指向 CIM 實例的[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指標中不可用。</span><span class="sxs-lookup"><span data-stu-id="654a9-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="654a9-139">使用者無法創建名稱以底線開頭或結尾的方法。</span><span class="sxs-lookup"><span data-stu-id="654a9-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="654a9-140">這是為系統類和屬性保留的。</span><span class="sxs-lookup"><span data-stu-id="654a9-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="654a9-141">對於方法，`in`和`out`參數被描述為[IWbemClassObject 物件](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)中的屬性。</span><span class="sxs-lookup"><span data-stu-id="654a9-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="654a9-142">`[in/out]`可以通過將相同的屬性添加到 和`pInSignature``pOutSignature`參數指向的兩個物件來定義參數。</span><span class="sxs-lookup"><span data-stu-id="654a9-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="654a9-143">在這種情況下，屬性共用相同的**ID**限定詞值。</span><span class="sxs-lookup"><span data-stu-id="654a9-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="654a9-144">[__Parameters](/windows/desktop/WmiSdk/--parameters)類物件中的每個屬性除必須具有`ReturnValue`**ID**限定詞外，該限定詞是標識參數顯示順序的零基數值。</span><span class="sxs-lookup"><span data-stu-id="654a9-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="654a9-145">沒有兩個參數可以具有相同的**ID**值，並且不能跳過**ID**值。</span><span class="sxs-lookup"><span data-stu-id="654a9-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="654a9-146">如果發生任一條件，`PutMethod`則函數`WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`將返回 。</span><span class="sxs-lookup"><span data-stu-id="654a9-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="654a9-147">範例</span><span class="sxs-lookup"><span data-stu-id="654a9-147">Example</span></span>

<span data-ttu-id="654a9-148">例如，請參閱[IWbemClassObject：:PutMethod 方法](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)。</span><span class="sxs-lookup"><span data-stu-id="654a9-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="654a9-149">需求</span><span class="sxs-lookup"><span data-stu-id="654a9-149">Requirements</span></span>  
 <span data-ttu-id="654a9-150">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="654a9-150">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="654a9-151">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="654a9-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="654a9-152">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="654a9-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="654a9-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="654a9-153">See also</span></span>

- [<span data-ttu-id="654a9-154">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="654a9-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
