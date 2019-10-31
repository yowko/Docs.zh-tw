---
title: GetMethod 函式（非受控 API 參考）
description: GetMethod 函數會抓取方法的相關資訊。
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
ms.openlocfilehash: 48986f5ff1cbbb45840ec1a059aa86711848d717
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102582"
---
# <a name="getmethod-function"></a><span data-ttu-id="23c4a-103">GetMethod 函式</span><span class="sxs-lookup"><span data-stu-id="23c4a-103">GetMethod function</span></span>

<span data-ttu-id="23c4a-104">擷取指定之方法的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="23c4a-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="23c4a-105">語法</span><span class="sxs-lookup"><span data-stu-id="23c4a-105">Syntax</span></span>

```cpp
HRESULT GetMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```

## <a name="parameters"></a><span data-ttu-id="23c4a-106">參數</span><span class="sxs-lookup"><span data-stu-id="23c4a-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="23c4a-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="23c4a-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="23c4a-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="23c4a-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="23c4a-109">在方法名稱。</span><span class="sxs-lookup"><span data-stu-id="23c4a-109">[in] The method name.</span></span> <span data-ttu-id="23c4a-110">這個參數不能 `null`，而且必須指向有效的 `LPCWSTR`。</span><span class="sxs-lookup"><span data-stu-id="23c4a-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`\
<span data-ttu-id="23c4a-111">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="23c4a-111">[in] Reserved.</span></span> <span data-ttu-id="23c4a-112">這個參數必須是0。</span><span class="sxs-lookup"><span data-stu-id="23c4a-112">This parameter must be 0.</span></span>

`ppInSignature`\
<span data-ttu-id="23c4a-113">脫銷[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例位址的指標，描述方法的 in 參數。</span><span class="sxs-lookup"><span data-stu-id="23c4a-113">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the in parameters to the method.</span></span> <span data-ttu-id="23c4a-114">如果此參數設定為 `null`，則會予以忽略。</span><span class="sxs-lookup"><span data-stu-id="23c4a-114">This parameter is ignored if it is set to `null`.</span></span>

`ppOutSignature`\
<span data-ttu-id="23c4a-115">脫銷[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例之位址的指標，描述方法的 out 參數。</span><span class="sxs-lookup"><span data-stu-id="23c4a-115">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="23c4a-116">如果此參數設定為 `null`，則會予以忽略。</span><span class="sxs-lookup"><span data-stu-id="23c4a-116">This parameter is ignored if it is set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="23c4a-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="23c4a-117">Return value</span></span>

<span data-ttu-id="23c4a-118">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="23c4a-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="23c4a-119">常數</span><span class="sxs-lookup"><span data-stu-id="23c4a-119">Constant</span></span>  |<span data-ttu-id="23c4a-120">值</span><span class="sxs-lookup"><span data-stu-id="23c4a-120">Value</span></span>  |<span data-ttu-id="23c4a-121">描述</span><span class="sxs-lookup"><span data-stu-id="23c4a-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="23c4a-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="23c4a-122">0x80041002</span></span> | <span data-ttu-id="23c4a-123">找不到指定的屬性。</span><span class="sxs-lookup"><span data-stu-id="23c4a-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="23c4a-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="23c4a-124">0x80041006</span></span> | <span data-ttu-id="23c4a-125">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="23c4a-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="23c4a-126">0</span><span class="sxs-lookup"><span data-stu-id="23c4a-126">0</span></span> | <span data-ttu-id="23c4a-127">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="23c4a-127">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="23c4a-128">備註</span><span class="sxs-lookup"><span data-stu-id="23c4a-128">Remarks</span></span>

<span data-ttu-id="23c4a-129">此函式會包裝對[IWbemClassObject：： GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="23c4a-129">This function wraps a call to the [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="23c4a-130">如果方法中沒有 in 參數，Windows 管理可以將[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指標設定為 `null`。</span><span class="sxs-lookup"><span data-stu-id="23c4a-130">Windows Management can set the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="23c4a-131">在 `ppInSignature` 和 `ppOutSignature` 分別描述 in 和 out 參數，當做 system 類別[_Parameters](/windows/desktop/WmiSdk/--parameters)之 `IWbemClassObject` 實例中的屬性。</span><span class="sxs-lookup"><span data-stu-id="23c4a-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](/windows/desktop/WmiSdk/--parameters).</span></span> <span data-ttu-id="23c4a-132">`ppInSignature` 中的屬性會命名為 `Param`*n*，其中*n*是方法簽章中參數的位置（例如 `Param1`、`Param2`等）。</span><span class="sxs-lookup"><span data-stu-id="23c4a-132">The properties in `ppInSignature` are named `Param`*n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="23c4a-133">`ppOutSignature` 中的屬性也會命名為 `Param`*n*，而傳回值會命名為 `ReturnValue`。</span><span class="sxs-lookup"><span data-stu-id="23c4a-133">The properties in `ppOutSignature` are also named `Param`*n*, and the return value is named `ReturnValue`.</span></span> <span data-ttu-id="23c4a-134">如需詳細資訊和範例，請參閱[IWbemClassObject：： GetMethod 方法](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod)。</span><span class="sxs-lookup"><span data-stu-id="23c4a-134">For more information and an example, see [IWbemClassObject::GetMethod method](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span></span>

## <a name="requirements"></a><span data-ttu-id="23c4a-135">需求</span><span class="sxs-lookup"><span data-stu-id="23c4a-135">Requirements</span></span>

<span data-ttu-id="23c4a-136">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23c4a-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="23c4a-137">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="23c4a-137">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="23c4a-138">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="23c4a-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="23c4a-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="23c4a-139">See also</span></span>

- [<span data-ttu-id="23c4a-140">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="23c4a-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
