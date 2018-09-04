---
title: GetMethod 函式 （Unmanaged API 參考）
description: GetMethod 函式會擷取方法的相關資訊。
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a913de0ff20fba51295fd8282b58e3953be9bba2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554865"
---
# <a name="getmethod-function"></a><span data-ttu-id="093c5-103">GetMethod 函式</span><span class="sxs-lookup"><span data-stu-id="093c5-103">GetMethod function</span></span>
<span data-ttu-id="093c5-104">擷取指定之方法的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="093c5-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="093c5-105">語法</span><span class="sxs-lookup"><span data-stu-id="093c5-105">Syntax</span></span>  
  
```  
HRESULT GetMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
); 
```  

## <a name="parameters"></a><span data-ttu-id="093c5-106">參數</span><span class="sxs-lookup"><span data-stu-id="093c5-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="093c5-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="093c5-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="093c5-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="093c5-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="093c5-109">[in]方法名稱。</span><span class="sxs-lookup"><span data-stu-id="093c5-109">[in] The method name.</span></span> <span data-ttu-id="093c5-110">這個參數不能`null`而且必須指向有效`LPCWSTR`。</span><span class="sxs-lookup"><span data-stu-id="093c5-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`  
<span data-ttu-id="093c5-111">[in]保留。</span><span class="sxs-lookup"><span data-stu-id="093c5-111">[in] Reserved.</span></span> <span data-ttu-id="093c5-112">這個參數必須是 0。</span><span class="sxs-lookup"><span data-stu-id="093c5-112">This parameter must be 0.</span></span>

`ppInSignature`   
<span data-ttu-id="093c5-113">[out]位址指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)描述方法在 paramteers 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="093c5-113">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the in paramteers to the method.</span></span> <span data-ttu-id="093c5-114">如果設定為，則會忽略這個參數`null`。</span><span class="sxs-lookup"><span data-stu-id="093c5-114">This parameter is ignored if it is set to `null`.</span></span> 

`ppOutSignature`  
<span data-ttu-id="093c5-115">[out]位址指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)描述方法的 out 參數的執行個體。</span><span class="sxs-lookup"><span data-stu-id="093c5-115">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="093c5-116">如果設定為，則會忽略這個參數`null`。</span><span class="sxs-lookup"><span data-stu-id="093c5-116">This parameter is ignored if it is set to `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="093c5-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="093c5-117">Return value</span></span>

<span data-ttu-id="093c5-118">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="093c5-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="093c5-119">常數</span><span class="sxs-lookup"><span data-stu-id="093c5-119">Constant</span></span>  |<span data-ttu-id="093c5-120">值</span><span class="sxs-lookup"><span data-stu-id="093c5-120">Value</span></span>  |<span data-ttu-id="093c5-121">描述</span><span class="sxs-lookup"><span data-stu-id="093c5-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="093c5-122">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="093c5-122">0x80041002</span></span> | <span data-ttu-id="093c5-123">找不到指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="093c5-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="093c5-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="093c5-124">0x80041006</span></span> | <span data-ttu-id="093c5-125">沒有足夠的記憶體可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="093c5-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="093c5-126">0</span><span class="sxs-lookup"><span data-stu-id="093c5-126">0</span></span> | <span data-ttu-id="093c5-127">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="093c5-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="093c5-128">備註</span><span class="sxs-lookup"><span data-stu-id="093c5-128">Remarks</span></span>

<span data-ttu-id="093c5-129">此函式會包裝在呼叫[IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)方法。</span><span class="sxs-lookup"><span data-stu-id="093c5-129">This function wraps a call to the [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="093c5-130">Windows 管理可以設定[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指標`null`如果方法沒有任何 in 參數。</span><span class="sxs-lookup"><span data-stu-id="093c5-130">Windows Management can set the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="093c5-131">在 `ppInSignature`並`ppOutSignature`分別中的屬性描述輸入和輸出參數，`IWbemClassObject`系統類別的執行個體[_Parameters](/windows/desktop/WmiSdk/--parameters)。</span><span class="sxs-lookup"><span data-stu-id="093c5-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](/windows/desktop/WmiSdk/--parameters).</span></span> <span data-ttu-id="093c5-132">中的屬性`ppInsignature`名為 **Param * * * n*，其中*n*是方法簽章中參數的位置 (例如`Param1`， `Param2`，依此類推。)。</span><span class="sxs-lookup"><span data-stu-id="093c5-132">The properties in `ppInsignature` are named **Param***n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="093c5-133">中的屬性`ppOutSignature`也稱為 **Param * * * n*，和名為傳回值**ReturnValue**。</span><span class="sxs-lookup"><span data-stu-id="093c5-133">The properties in `ppOutSignature` are also named **Param***n*, and the return value is named **ReturnValue**.</span></span> <span data-ttu-id="093c5-134">如需詳細資訊和範例，請參閱 < [IWbemClassObject::GetMethod 方法](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)。</span><span class="sxs-lookup"><span data-stu-id="093c5-134">For more information and an example, see [IWbemClassObject::GetMethod method](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span></span>

## <a name="requirements"></a><span data-ttu-id="093c5-135">需求</span><span class="sxs-lookup"><span data-stu-id="093c5-135">Requirements</span></span>  
<span data-ttu-id="093c5-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="093c5-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="093c5-137">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="093c5-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="093c5-138">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="093c5-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="093c5-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="093c5-139">See also</span></span>  
[<span data-ttu-id="093c5-140">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="093c5-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
