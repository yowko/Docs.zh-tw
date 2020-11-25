---
title: 'QualifierSet_Delete 函式 (非受控 API 參考) '
description: QualifierSet_Delete 函數會依名稱刪除辨識符號。
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 2000de77903c3dabb43116fa1700b4ed393aeb5a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721149"
---
# <a name="qualifierset_delete-function"></a><span data-ttu-id="d956d-103">QualifierSet_Delete 函式</span><span class="sxs-lookup"><span data-stu-id="d956d-103">QualifierSet_Delete function</span></span>

<span data-ttu-id="d956d-104">依名稱刪除指定的限定詞。</span><span class="sxs-lookup"><span data-stu-id="d956d-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d956d-105">語法</span><span class="sxs-lookup"><span data-stu-id="d956d-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="d956d-106">參數</span><span class="sxs-lookup"><span data-stu-id="d956d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d956d-107">在此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="d956d-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="d956d-108">`ptr` 在 [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="d956d-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="d956d-109">`wszName` 在要刪除的辨識符號名稱。</span><span class="sxs-lookup"><span data-stu-id="d956d-109">`wszName` [in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="d956d-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="d956d-110">Return value</span></span>

<span data-ttu-id="d956d-111">這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="d956d-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d956d-112">常數</span><span class="sxs-lookup"><span data-stu-id="d956d-112">Constant</span></span>  |<span data-ttu-id="d956d-113">值</span><span class="sxs-lookup"><span data-stu-id="d956d-113">Value</span></span>  |<span data-ttu-id="d956d-114">描述</span><span class="sxs-lookup"><span data-stu-id="d956d-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d956d-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d956d-115">0x80041008</span></span> | <span data-ttu-id="d956d-116">`wszName` 參數無效。</span><span class="sxs-lookup"><span data-stu-id="d956d-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="d956d-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="d956d-117">0x80041016</span></span> | <span data-ttu-id="d956d-118">刪除此限定詞不合法。</span><span class="sxs-lookup"><span data-stu-id="d956d-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="d956d-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="d956d-119">0x80041002</span></span> | <span data-ttu-id="d956d-120">找不到指定的限定詞。</span><span class="sxs-lookup"><span data-stu-id="d956d-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d956d-121">0</span><span class="sxs-lookup"><span data-stu-id="d956d-121">0</span></span> | <span data-ttu-id="d956d-122">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="d956d-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="d956d-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="d956d-123">0x40002</span></span> | <span data-ttu-id="d956d-124">已刪除本機覆寫，且父物件的原始辨識符號已恢復範圍。</span><span class="sxs-lookup"><span data-stu-id="d956d-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="d956d-125">備註</span><span class="sxs-lookup"><span data-stu-id="d956d-125">Remarks</span></span>

<span data-ttu-id="d956d-126">此函數會包裝對 [IWbemQualifierSet：:D elete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="d956d-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="d956d-127">由於限定詞傳播規則，特定限定詞可能已繼承自另一個物件，而只會在目前的類別或實例中覆寫。</span><span class="sxs-lookup"><span data-stu-id="d956d-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="d956d-128">在此情況下， `QualifierSet_Delete` 方法會將限定詞重設為其原始的繼承值。</span><span class="sxs-lookup"><span data-stu-id="d956d-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="d956d-129">在此情況下，函式會傳回狀態碼 `WBEM_S_RESET_TO_DEFAULT` 。</span><span class="sxs-lookup"><span data-stu-id="d956d-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="d956d-130">需求</span><span class="sxs-lookup"><span data-stu-id="d956d-130">Requirements</span></span>  

 <span data-ttu-id="d956d-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d956d-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d956d-132">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="d956d-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d956d-133">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d956d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d956d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d956d-134">See also</span></span>

- [<span data-ttu-id="d956d-135">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="d956d-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
