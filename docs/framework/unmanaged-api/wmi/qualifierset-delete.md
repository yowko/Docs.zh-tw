---
title: QualifierSet_Delete 函式（非受控 API 參考）
description: QualifierSet_Delete 函數會依名稱刪除限定詞。
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bc26a16650a5beecc17898e0421e79536713deb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798332"
---
# <a name="qualifierset_delete-function"></a><span data-ttu-id="da6ca-103">QualifierSet_Delete 函式</span><span class="sxs-lookup"><span data-stu-id="da6ca-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="da6ca-104">依名稱刪除指定的限定詞。</span><span class="sxs-lookup"><span data-stu-id="da6ca-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="da6ca-105">語法</span><span class="sxs-lookup"><span data-stu-id="da6ca-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="da6ca-106">參數</span><span class="sxs-lookup"><span data-stu-id="da6ca-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="da6ca-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="da6ca-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="da6ca-108">在[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="da6ca-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="da6ca-109">在要刪除的限定詞名稱。</span><span class="sxs-lookup"><span data-stu-id="da6ca-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="da6ca-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="da6ca-110">Return value</span></span>

<span data-ttu-id="da6ca-111">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="da6ca-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="da6ca-112">常數</span><span class="sxs-lookup"><span data-stu-id="da6ca-112">Constant</span></span>  |<span data-ttu-id="da6ca-113">值</span><span class="sxs-lookup"><span data-stu-id="da6ca-113">Value</span></span>  |<span data-ttu-id="da6ca-114">描述</span><span class="sxs-lookup"><span data-stu-id="da6ca-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="da6ca-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="da6ca-115">0x80041008</span></span> | <span data-ttu-id="da6ca-116">`wszName` 參數無效。</span><span class="sxs-lookup"><span data-stu-id="da6ca-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="da6ca-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="da6ca-117">0x80041016</span></span> | <span data-ttu-id="da6ca-118">刪除這個限定詞是不合法的。</span><span class="sxs-lookup"><span data-stu-id="da6ca-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="da6ca-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="da6ca-119">0x80041002</span></span> | <span data-ttu-id="da6ca-120">找不到指定的限定詞。</span><span class="sxs-lookup"><span data-stu-id="da6ca-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="da6ca-121">0</span><span class="sxs-lookup"><span data-stu-id="da6ca-121">0</span></span> | <span data-ttu-id="da6ca-122">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="da6ca-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="da6ca-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="da6ca-123">0x40002</span></span> | <span data-ttu-id="da6ca-124">已刪除本機覆寫，且父物件的原始辨識符號已恢復範圍。</span><span class="sxs-lookup"><span data-stu-id="da6ca-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="da6ca-125">備註</span><span class="sxs-lookup"><span data-stu-id="da6ca-125">Remarks</span></span>

<span data-ttu-id="da6ca-126">此函式會包裝對[IWbemQualifierSet：:D 刪除](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="da6ca-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="da6ca-127">由於限定詞傳播規則的緣故，特定的辨識符號可能已經繼承自另一個物件，而且只會在目前的類別或實例中覆寫。</span><span class="sxs-lookup"><span data-stu-id="da6ca-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="da6ca-128">在此情況下， `QualifierSet_Delete`方法會將限定詞重設為其原始的繼承值。</span><span class="sxs-lookup"><span data-stu-id="da6ca-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="da6ca-129">在此情況下，函式會傳回`WBEM_S_RESET_TO_DEFAULT`狀態碼。</span><span class="sxs-lookup"><span data-stu-id="da6ca-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="da6ca-130">需求</span><span class="sxs-lookup"><span data-stu-id="da6ca-130">Requirements</span></span>  
 <span data-ttu-id="da6ca-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da6ca-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da6ca-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="da6ca-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="da6ca-133">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="da6ca-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da6ca-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da6ca-134">See also</span></span>

- [<span data-ttu-id="da6ca-135">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="da6ca-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
