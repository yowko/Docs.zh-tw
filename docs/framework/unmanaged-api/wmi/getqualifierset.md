---
title: 獲取限定詞集功能（非託管 API 引用）
description: GetQualifierSet 函數檢索類或實例的限定詞集。
ms.date: 11/06/2017
api_name:
- GetQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetQualifierSet
helpviewer_keywords:
- GetQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 368f0a13871bd48780fa30b370d37157d2724bb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176769"
---
# <a name="getqualifierset-function"></a><span data-ttu-id="6f7e0-103">GetQualifierSet 函式</span><span class="sxs-lookup"><span data-stu-id="6f7e0-103">GetQualifierSet function</span></span>
<span data-ttu-id="6f7e0-104">擷取類別執行個體或類別定義的限定詞集合。</span><span class="sxs-lookup"><span data-stu-id="6f7e0-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="6f7e0-105">語法</span><span class="sxs-lookup"><span data-stu-id="6f7e0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [out] IWbemQualifierSet  **ppQualSet
);
```  

## <a name="parameters"></a><span data-ttu-id="6f7e0-106">參數</span><span class="sxs-lookup"><span data-stu-id="6f7e0-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="6f7e0-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="6f7e0-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="6f7e0-108">[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="6f7e0-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="6f7e0-109">[出]接收允許訪問類物件的限定詞的介面指標。</span><span class="sxs-lookup"><span data-stu-id="6f7e0-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="6f7e0-110">`ppQualSet` 不可以是 `null`。</span><span class="sxs-lookup"><span data-stu-id="6f7e0-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="6f7e0-111">如果發生錯誤，則不返回新物件，並且指標未修改。</span><span class="sxs-lookup"><span data-stu-id="6f7e0-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="6f7e0-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="6f7e0-112">Return value</span></span>

<span data-ttu-id="6f7e0-113">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="6f7e0-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6f7e0-114">持續性</span><span class="sxs-lookup"><span data-stu-id="6f7e0-114">Constant</span></span>  |<span data-ttu-id="6f7e0-115">值</span><span class="sxs-lookup"><span data-stu-id="6f7e0-115">Value</span></span>  |<span data-ttu-id="6f7e0-116">描述</span><span class="sxs-lookup"><span data-stu-id="6f7e0-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="6f7e0-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="6f7e0-117">0x80041001</span></span> | <span data-ttu-id="6f7e0-118">出現了一個普遍的失敗。</span><span class="sxs-lookup"><span data-stu-id="6f7e0-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="6f7e0-119">0 x80041002</span><span class="sxs-lookup"><span data-stu-id="6f7e0-119">0x80041002</span></span> | <span data-ttu-id="6f7e0-120">指定的方法不存在。</span><span class="sxs-lookup"><span data-stu-id="6f7e0-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6f7e0-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6f7e0-121">0x80041006</span></span> | <span data-ttu-id="6f7e0-122">可用的記憶體不足，無法完成作業。</span><span class="sxs-lookup"><span data-stu-id="6f7e0-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6f7e0-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6f7e0-123">0x80041008</span></span> | <span data-ttu-id="6f7e0-124">參數為`null`。</span><span class="sxs-lookup"><span data-stu-id="6f7e0-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6f7e0-125">0</span><span class="sxs-lookup"><span data-stu-id="6f7e0-125">0</span></span> | <span data-ttu-id="6f7e0-126">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="6f7e0-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="6f7e0-127">備註</span><span class="sxs-lookup"><span data-stu-id="6f7e0-127">Remarks</span></span>

<span data-ttu-id="6f7e0-128">此函數包裝對[IWbem ClassObject 的調用：：getQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset)方法。</span><span class="sxs-lookup"><span data-stu-id="6f7e0-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) method.</span></span>

<span data-ttu-id="6f7e0-129">[IWbemQualifierSet 指標](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)允許調用方添加、編輯或刪除這些限定詞。</span><span class="sxs-lookup"><span data-stu-id="6f7e0-129">The [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="6f7e0-130">此類添加、編輯或刪除的限定詞適用于整個實例或類定義。</span><span class="sxs-lookup"><span data-stu-id="6f7e0-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="6f7e0-131">需求</span><span class="sxs-lookup"><span data-stu-id="6f7e0-131">Requirements</span></span>  
<span data-ttu-id="6f7e0-132">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f7e0-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f7e0-133">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6f7e0-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6f7e0-134">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6f7e0-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f7e0-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f7e0-135">See also</span></span>

- [<span data-ttu-id="6f7e0-136">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="6f7e0-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
