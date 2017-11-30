---
title: "QualifierSet_Delete 函式 （Unmanaged API 參考）"
description: "QualifierSet_Delete 函式會依名稱刪除限定詞。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: QualifierSet_Delete
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: QualifierSet_Delete
helpviewer_keywords: QualifierSet_Delete function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9245fc0ee109837249f1f3df400385c117a2f2d7
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="qualifiersetdelete-function"></a><span data-ttu-id="e719e-103">QualifierSet_Delete 函式</span><span class="sxs-lookup"><span data-stu-id="e719e-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="e719e-104">依名稱刪除指定的限定詞。</span><span class="sxs-lookup"><span data-stu-id="e719e-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e719e-105">語法</span><span class="sxs-lookup"><span data-stu-id="e719e-105">Syntax</span></span>  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="e719e-106">參數</span><span class="sxs-lookup"><span data-stu-id="e719e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="e719e-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="e719e-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="e719e-108">[in]指標[IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="e719e-108">[in] A pointer to an [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) instance.</span></span>

`wszName`   
<span data-ttu-id="e719e-109">[in]若要刪除限定詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="e719e-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="e719e-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="e719e-110">Return value</span></span>

<span data-ttu-id="e719e-111">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="e719e-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e719e-112">常數</span><span class="sxs-lookup"><span data-stu-id="e719e-112">Constant</span></span>  |<span data-ttu-id="e719e-113">值</span><span class="sxs-lookup"><span data-stu-id="e719e-113">Value</span></span>  |<span data-ttu-id="e719e-114">說明</span><span class="sxs-lookup"><span data-stu-id="e719e-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e719e-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e719e-115">0x80041008</span></span> | <span data-ttu-id="e719e-116">`wszName`參數無效。</span><span class="sxs-lookup"><span data-stu-id="e719e-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="e719e-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="e719e-117">0x80041016</span></span> | <span data-ttu-id="e719e-118">刪除這個限定詞是不合法的。</span><span class="sxs-lookup"><span data-stu-id="e719e-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="e719e-119">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="e719e-119">0x80041002</span></span> | <span data-ttu-id="e719e-120">找不到指定的限定詞。</span><span class="sxs-lookup"><span data-stu-id="e719e-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="e719e-121">0</span><span class="sxs-lookup"><span data-stu-id="e719e-121">0</span></span> | <span data-ttu-id="e719e-122">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="e719e-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="e719e-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="e719e-123">0x40002</span></span> | <span data-ttu-id="e719e-124">本機覆寫已刪除，並從父物件的原始限定詞已恢復範圍。</span><span class="sxs-lookup"><span data-stu-id="e719e-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="e719e-125">備註</span><span class="sxs-lookup"><span data-stu-id="e719e-125">Remarks</span></span>

<span data-ttu-id="e719e-126">此函式會包裝呼叫[IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="e719e-126">This function wraps a call to the [IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="e719e-127">限定詞傳播規則，因為特定的辨識符號可能已從另一個物件繼承和只是覆寫目前的類別或執行個體中。</span><span class="sxs-lookup"><span data-stu-id="e719e-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="e719e-128">在此情況下，`QualifierSet_Delete`方法重設這個限定詞繼承其原始值。</span><span class="sxs-lookup"><span data-stu-id="e719e-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="e719e-129">函式在此情況下會傳回狀態碼`WBEM_S_RESET_TO_DEFAULT`。</span><span class="sxs-lookup"><span data-stu-id="e719e-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="e719e-130">需求</span><span class="sxs-lookup"><span data-stu-id="e719e-130">Requirements</span></span>  
 <span data-ttu-id="e719e-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e719e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e719e-132">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e719e-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="e719e-133">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e719e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e719e-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="e719e-134">See also</span></span>  
[<span data-ttu-id="e719e-135">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="e719e-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
