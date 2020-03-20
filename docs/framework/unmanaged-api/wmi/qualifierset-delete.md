---
title: QualifierSet_Delete功能（非託管 API 引用）
description: QualifierSet_Delete函數按名稱刪除限定詞。
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
ms.openlocfilehash: 0d2a02ba9d89ba16e776bb73563eaebf8a92f1fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174897"
---
# <a name="qualifierset_delete-function"></a><span data-ttu-id="276e0-103">QualifierSet_Delete 函式</span><span class="sxs-lookup"><span data-stu-id="276e0-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="276e0-104">依名稱刪除指定的限定詞。</span><span class="sxs-lookup"><span data-stu-id="276e0-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="276e0-105">語法</span><span class="sxs-lookup"><span data-stu-id="276e0-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="276e0-106">參數</span><span class="sxs-lookup"><span data-stu-id="276e0-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="276e0-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="276e0-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="276e0-108">`ptr`[在]指向[IWbem 限定詞集實例的](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)指標。</span><span class="sxs-lookup"><span data-stu-id="276e0-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="276e0-109">`wszName`[在]要刪除的限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="276e0-109">`wszName` [in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="276e0-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="276e0-110">Return value</span></span>

<span data-ttu-id="276e0-111">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="276e0-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="276e0-112">持續性</span><span class="sxs-lookup"><span data-stu-id="276e0-112">Constant</span></span>  |<span data-ttu-id="276e0-113">值</span><span class="sxs-lookup"><span data-stu-id="276e0-113">Value</span></span>  |<span data-ttu-id="276e0-114">描述</span><span class="sxs-lookup"><span data-stu-id="276e0-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="276e0-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="276e0-115">0x80041008</span></span> | <span data-ttu-id="276e0-116">`wszName` 參數無效。</span><span class="sxs-lookup"><span data-stu-id="276e0-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="276e0-117">0 x80041016</span><span class="sxs-lookup"><span data-stu-id="276e0-117">0x80041016</span></span> | <span data-ttu-id="276e0-118">刪除此限定詞是非法的。</span><span class="sxs-lookup"><span data-stu-id="276e0-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="276e0-119">0 x80041002</span><span class="sxs-lookup"><span data-stu-id="276e0-119">0x80041002</span></span> | <span data-ttu-id="276e0-120">未找到指定的限定詞。</span><span class="sxs-lookup"><span data-stu-id="276e0-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="276e0-121">0</span><span class="sxs-lookup"><span data-stu-id="276e0-121">0</span></span> | <span data-ttu-id="276e0-122">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="276e0-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="276e0-123">0 x40002</span><span class="sxs-lookup"><span data-stu-id="276e0-123">0x40002</span></span> | <span data-ttu-id="276e0-124">本地重寫已被刪除，父物件的原始限定詞已恢復作用域。</span><span class="sxs-lookup"><span data-stu-id="276e0-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="276e0-125">備註</span><span class="sxs-lookup"><span data-stu-id="276e0-125">Remarks</span></span>

<span data-ttu-id="276e0-126">此函數包裝對[IWbem 限定詞集：:Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete)方法的調用。</span><span class="sxs-lookup"><span data-stu-id="276e0-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="276e0-127">由於限定詞傳播規則，特定限定詞可能從另一個物件繼承，並且只是在當前類或實例中重寫。</span><span class="sxs-lookup"><span data-stu-id="276e0-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="276e0-128">在這種情況下，`QualifierSet_Delete`該方法將限定詞重置為其原始繼承的值。</span><span class="sxs-lookup"><span data-stu-id="276e0-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="276e0-129">在這種情況下，函數返回狀態碼`WBEM_S_RESET_TO_DEFAULT`。</span><span class="sxs-lookup"><span data-stu-id="276e0-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="276e0-130">需求</span><span class="sxs-lookup"><span data-stu-id="276e0-130">Requirements</span></span>  
 <span data-ttu-id="276e0-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="276e0-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="276e0-132">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="276e0-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="276e0-133">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="276e0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="276e0-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="276e0-134">See also</span></span>

- [<span data-ttu-id="276e0-135">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="276e0-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
