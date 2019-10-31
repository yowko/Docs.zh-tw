---
title: CloneEnumWbemClassObject 函式（非受控 API 參考）
description: CloneEnumWbemClassObject 函數會建立枚舉器的邏輯複本。
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
ms.openlocfilehash: 9d2442161aaa83693a33f9efc230c09b8c4426e2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128726"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="f4cf3-103">CloneEnumWbemClassObject 函式</span><span class="sxs-lookup"><span data-stu-id="f4cf3-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="f4cf3-104">建立列舉程式的邏輯複本，並保留其在列舉中的目前位置。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="f4cf3-105">語法</span><span class="sxs-lookup"><span data-stu-id="f4cf3-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="f4cf3-106">參數</span><span class="sxs-lookup"><span data-stu-id="f4cf3-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="f4cf3-107">脫銷接收新[IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="f4cf3-108">在授權層級。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="f4cf3-109">在模擬層級。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="f4cf3-110">脫銷要複製之[IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="f4cf3-111">在使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-111">[in] The user name.</span></span> <span data-ttu-id="f4cf3-112">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="f4cf3-113">在密碼。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-113">[in] The password.</span></span> <span data-ttu-id="f4cf3-114">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="f4cf3-115">`strAuthority`\ [in] 使用者的功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-115">`strAuthority`\ [in] The domain name of the user.</span></span> <span data-ttu-id="f4cf3-116">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="f4cf3-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="f4cf3-117">Return value</span></span>

<span data-ttu-id="f4cf3-118">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="f4cf3-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f4cf3-119">常數</span><span class="sxs-lookup"><span data-stu-id="f4cf3-119">Constant</span></span>  |<span data-ttu-id="f4cf3-120">值</span><span class="sxs-lookup"><span data-stu-id="f4cf3-120">Value</span></span>  |<span data-ttu-id="f4cf3-121">描述</span><span class="sxs-lookup"><span data-stu-id="f4cf3-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="f4cf3-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f4cf3-122">0x80041001</span></span> | <span data-ttu-id="f4cf3-123">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f4cf3-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f4cf3-124">0x80041008</span></span> | <span data-ttu-id="f4cf3-125">參數無效。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f4cf3-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f4cf3-126">0x80041006</span></span> | <span data-ttu-id="f4cf3-127">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="f4cf3-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="f4cf3-128">0x80041015</span></span> | <span data-ttu-id="f4cf3-129">目前進程和 WMI 之間的遠端程序呼叫（RPC）連結失敗。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="f4cf3-130">0</span><span class="sxs-lookup"><span data-stu-id="f4cf3-130">0</span></span> | <span data-ttu-id="f4cf3-131">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="f4cf3-132">備註</span><span class="sxs-lookup"><span data-stu-id="f4cf3-132">Remarks</span></span>

<span data-ttu-id="f4cf3-133">此函式會包裝對[IEnumWbemClassObject：： Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="f4cf3-134">這個方法只會進行「最大的工作」複製。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="f4cf3-135">由於許多 CIM 物件的動態本質，新的列舉值可能不會列舉與來源列舉值相同的物件集合。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="f4cf3-136">如果函式呼叫失敗，您可以藉由呼叫[GetErrorInfo](geterrorinfo.md)函數來取得其他錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="f4cf3-137">範例</span><span class="sxs-lookup"><span data-stu-id="f4cf3-137">Example</span></span>

<span data-ttu-id="f4cf3-138">如需範例，請參閱[IEnumWbemClassObject：： Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)方法。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f4cf3-139">需求</span><span class="sxs-lookup"><span data-stu-id="f4cf3-139">Requirements</span></span>
 <span data-ttu-id="f4cf3-140">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f4cf3-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="f4cf3-141">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="f4cf3-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="f4cf3-142">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f4cf3-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f4cf3-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="f4cf3-143">See also</span></span>

- [<span data-ttu-id="f4cf3-144">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="f4cf3-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
