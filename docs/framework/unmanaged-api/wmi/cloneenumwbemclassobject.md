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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1605314f94fd82d2a2cd7be105dde9e273f607bc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798692"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="b73c7-103">CloneEnumWbemClassObject 函式</span><span class="sxs-lookup"><span data-stu-id="b73c7-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="b73c7-104">建立列舉程式的邏輯複本，並保留其在列舉中的目前位置。</span><span class="sxs-lookup"><span data-stu-id="b73c7-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="b73c7-105">語法</span><span class="sxs-lookup"><span data-stu-id="b73c7-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="b73c7-106">參數</span><span class="sxs-lookup"><span data-stu-id="b73c7-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="b73c7-107">脫銷接收新[IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="b73c7-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="b73c7-108">在授權層級。</span><span class="sxs-lookup"><span data-stu-id="b73c7-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="b73c7-109">在模擬層級。</span><span class="sxs-lookup"><span data-stu-id="b73c7-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="b73c7-110">脫銷要複製之[IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="b73c7-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="b73c7-111">在使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="b73c7-111">[in] The user name.</span></span> <span data-ttu-id="b73c7-112">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="b73c7-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="b73c7-113">在密碼。</span><span class="sxs-lookup"><span data-stu-id="b73c7-113">[in] The password.</span></span> <span data-ttu-id="b73c7-114">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="b73c7-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="b73c7-115">`strAuthority`\ [in] 使用者的功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="b73c7-115">`strAuthority`\ [in] The domain name of the user.</span></span> <span data-ttu-id="b73c7-116">如需詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="b73c7-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="b73c7-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="b73c7-117">Return value</span></span>

<span data-ttu-id="b73c7-118">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="b73c7-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b73c7-119">常數</span><span class="sxs-lookup"><span data-stu-id="b73c7-119">Constant</span></span>  |<span data-ttu-id="b73c7-120">值</span><span class="sxs-lookup"><span data-stu-id="b73c7-120">Value</span></span>  |<span data-ttu-id="b73c7-121">描述</span><span class="sxs-lookup"><span data-stu-id="b73c7-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="b73c7-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="b73c7-122">0x80041001</span></span> | <span data-ttu-id="b73c7-123">發生一般失敗。</span><span class="sxs-lookup"><span data-stu-id="b73c7-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b73c7-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b73c7-124">0x80041008</span></span> | <span data-ttu-id="b73c7-125">參數無效。</span><span class="sxs-lookup"><span data-stu-id="b73c7-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b73c7-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b73c7-126">0x80041006</span></span> | <span data-ttu-id="b73c7-127">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="b73c7-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="b73c7-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="b73c7-128">0x80041015</span></span> | <span data-ttu-id="b73c7-129">目前進程和 WMI 之間的遠端程序呼叫（RPC）連結失敗。</span><span class="sxs-lookup"><span data-stu-id="b73c7-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="b73c7-130">0</span><span class="sxs-lookup"><span data-stu-id="b73c7-130">0</span></span> | <span data-ttu-id="b73c7-131">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="b73c7-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="b73c7-132">備註</span><span class="sxs-lookup"><span data-stu-id="b73c7-132">Remarks</span></span>

<span data-ttu-id="b73c7-133">此函式會包裝對[IEnumWbemClassObject：： Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="b73c7-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="b73c7-134">這個方法只會進行「最大的工作」複製。</span><span class="sxs-lookup"><span data-stu-id="b73c7-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="b73c7-135">由於許多 CIM 物件的動態本質，新的列舉值可能不會列舉與來源列舉值相同的物件集合。</span><span class="sxs-lookup"><span data-stu-id="b73c7-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="b73c7-136">如果函式呼叫失敗，您可以藉由呼叫[GetErrorInfo](geterrorinfo.md)函數來取得其他錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="b73c7-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="b73c7-137">範例</span><span class="sxs-lookup"><span data-stu-id="b73c7-137">Example</span></span>

<span data-ttu-id="b73c7-138">如需範例，請參閱[IEnumWbemClassObject：： Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)方法。</span><span class="sxs-lookup"><span data-stu-id="b73c7-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b73c7-139">需求</span><span class="sxs-lookup"><span data-stu-id="b73c7-139">Requirements</span></span>
 <span data-ttu-id="b73c7-140">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b73c7-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="b73c7-141">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b73c7-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="b73c7-142">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b73c7-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b73c7-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b73c7-143">See also</span></span>

- [<span data-ttu-id="b73c7-144">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="b73c7-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
