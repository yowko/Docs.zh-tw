---
title: 克隆EnumWbem類物件函數（非託管 API 引用）
description: CloneEnumWbemClassObject 函數創建枚舉器的邏輯副本。
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f2a3a7e848108e50c04f0ec70cf42586755a0a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175014"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="1d3eb-103">CloneEnumWbemClassObject 函式</span><span class="sxs-lookup"><span data-stu-id="1d3eb-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="1d3eb-104">建立列舉程式的邏輯複本，並保留其在列舉中的目前位置。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="1d3eb-105">語法</span><span class="sxs-lookup"><span data-stu-id="1d3eb-105">Syntax</span></span>

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum,
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject,
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority
);
```

## <a name="parameters"></a><span data-ttu-id="1d3eb-106">參數</span><span class="sxs-lookup"><span data-stu-id="1d3eb-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="1d3eb-107">[出]接收指向新[IEnumWbem ClassObject 的指標](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="1d3eb-108">[在]授權級別。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="1d3eb-109">[在]類比級別。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="1d3eb-110">[出]指向要克隆的[IEnumWbemClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="1d3eb-111">[在]使用者名。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-111">[in] The user name.</span></span> <span data-ttu-id="1d3eb-112">有關詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="1d3eb-113">[在]密碼。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-113">[in] The password.</span></span> <span data-ttu-id="1d3eb-114">有關詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="1d3eb-115">[在]使用者的功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-115">[in] The domain name of the user.</span></span> <span data-ttu-id="1d3eb-116">有關詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="1d3eb-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="1d3eb-117">Return value</span></span>

<span data-ttu-id="1d3eb-118">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="1d3eb-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1d3eb-119">持續性</span><span class="sxs-lookup"><span data-stu-id="1d3eb-119">Constant</span></span>  |<span data-ttu-id="1d3eb-120">值</span><span class="sxs-lookup"><span data-stu-id="1d3eb-120">Value</span></span>  |<span data-ttu-id="1d3eb-121">描述</span><span class="sxs-lookup"><span data-stu-id="1d3eb-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="1d3eb-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="1d3eb-122">0x80041001</span></span> | <span data-ttu-id="1d3eb-123">出現了一個普遍的失敗。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1d3eb-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1d3eb-124">0x80041008</span></span> | <span data-ttu-id="1d3eb-125">參數無效。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="1d3eb-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="1d3eb-126">0x80041006</span></span> | <span data-ttu-id="1d3eb-127">沒有足夠的記憶體可用於完成操作。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="1d3eb-128">0 x80041015</span><span class="sxs-lookup"><span data-stu-id="1d3eb-128">0x80041015</span></span> | <span data-ttu-id="1d3eb-129">當前進程和 WMI 之間的遠端程序呼叫 （RPC） 鏈路已失敗。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="1d3eb-130">0</span><span class="sxs-lookup"><span data-stu-id="1d3eb-130">0</span></span> | <span data-ttu-id="1d3eb-131">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="1d3eb-132">備註</span><span class="sxs-lookup"><span data-stu-id="1d3eb-132">Remarks</span></span>

<span data-ttu-id="1d3eb-133">此函數包裝對[IEnumWbem ClassObject：：clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)方法的調用。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="1d3eb-134">此方法僅進行"盡力"複製。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="1d3eb-135">由於許多 CIM 物件的動態性質，新的枚舉器可能不會枚舉與源枚舉器相同的物件集。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="1d3eb-136">如果函式呼叫失敗，您可以通過調用[GetErrorInfo](geterrorinfo.md)函數獲取其他錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="1d3eb-137">範例</span><span class="sxs-lookup"><span data-stu-id="1d3eb-137">Example</span></span>

<span data-ttu-id="1d3eb-138">例如，請參閱[IEnumWbem 類物件：：克隆](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)方法。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1d3eb-139">需求</span><span class="sxs-lookup"><span data-stu-id="1d3eb-139">Requirements</span></span>
 <span data-ttu-id="1d3eb-140">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d3eb-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="1d3eb-141">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1d3eb-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="1d3eb-142">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1d3eb-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1d3eb-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d3eb-143">See also</span></span>

- [<span data-ttu-id="1d3eb-144">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="1d3eb-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
