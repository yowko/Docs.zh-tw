---
title: QualifierSet_Delete 函式 （Unmanaged API 參考）
description: QualifierSet_Delete 函式會刪除限定詞名稱。
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
ms.openlocfilehash: 7ca4cc9fb65d1a4bd8713f969bbda5551ce5a2e2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881794"
---
# <a name="qualifiersetdelete-function"></a><span data-ttu-id="3463d-103">QualifierSet_Delete 函式</span><span class="sxs-lookup"><span data-stu-id="3463d-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="3463d-104">依名稱刪除指定的限定詞。</span><span class="sxs-lookup"><span data-stu-id="3463d-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="3463d-105">語法</span><span class="sxs-lookup"><span data-stu-id="3463d-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="3463d-106">參數</span><span class="sxs-lookup"><span data-stu-id="3463d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="3463d-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="3463d-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="3463d-108">[in]指標[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)執行個體。</span><span class="sxs-lookup"><span data-stu-id="3463d-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="3463d-109">[in]若要刪除限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="3463d-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="3463d-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="3463d-110">Return value</span></span>

<span data-ttu-id="3463d-111">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="3463d-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3463d-112">常數</span><span class="sxs-lookup"><span data-stu-id="3463d-112">Constant</span></span>  |<span data-ttu-id="3463d-113">值</span><span class="sxs-lookup"><span data-stu-id="3463d-113">Value</span></span>  |<span data-ttu-id="3463d-114">描述</span><span class="sxs-lookup"><span data-stu-id="3463d-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3463d-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3463d-115">0x80041008</span></span> | <span data-ttu-id="3463d-116">`wszName`參數無效。</span><span class="sxs-lookup"><span data-stu-id="3463d-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="3463d-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="3463d-117">0x80041016</span></span> | <span data-ttu-id="3463d-118">刪除這個限定詞是不合法的。</span><span class="sxs-lookup"><span data-stu-id="3463d-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="3463d-119">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="3463d-119">0x80041002</span></span> | <span data-ttu-id="3463d-120">找不到指定的限定詞。</span><span class="sxs-lookup"><span data-stu-id="3463d-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3463d-121">0</span><span class="sxs-lookup"><span data-stu-id="3463d-121">0</span></span> | <span data-ttu-id="3463d-122">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="3463d-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="3463d-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="3463d-123">0x40002</span></span> | <span data-ttu-id="3463d-124">本機覆寫已經刪除，原始的辨識符號，從父物件已重新開始範圍。</span><span class="sxs-lookup"><span data-stu-id="3463d-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3463d-125">備註</span><span class="sxs-lookup"><span data-stu-id="3463d-125">Remarks</span></span>

<span data-ttu-id="3463d-126">此函式會包裝在呼叫[IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete)方法。</span><span class="sxs-lookup"><span data-stu-id="3463d-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="3463d-127">限定詞傳播規則，因為特定的辨識符號可能已繼承自另一個物件和只是覆寫目前的類別或執行個體中。</span><span class="sxs-lookup"><span data-stu-id="3463d-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="3463d-128">在此情況下，`QualifierSet_Delete`方法重設為其原始的繼承值的限定詞。</span><span class="sxs-lookup"><span data-stu-id="3463d-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="3463d-129">函式在此情況下會傳回狀態碼`WBEM_S_RESET_TO_DEFAULT`。</span><span class="sxs-lookup"><span data-stu-id="3463d-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="3463d-130">需求</span><span class="sxs-lookup"><span data-stu-id="3463d-130">Requirements</span></span>  
 <span data-ttu-id="3463d-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3463d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3463d-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3463d-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="3463d-133">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3463d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3463d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3463d-134">See also</span></span>  
[<span data-ttu-id="3463d-135">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="3463d-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
