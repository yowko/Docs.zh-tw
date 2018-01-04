---
title: "DeleteMethod 函式 （Unmanaged API 參考）"
description: "DeleteMethod 函式會從 CIM 類別定義中刪除指定的方法。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: DeleteMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: DeleteMethod
helpviewer_keywords: DeleteMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03b147d2fd76e34c6152a0b41ee14319811e9300
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="deletemethod-function"></a><span data-ttu-id="ea4bf-103">DeleteMethod 函式</span><span class="sxs-lookup"><span data-stu-id="ea4bf-103">DeleteMethod function</span></span>
<span data-ttu-id="ea4bf-104">從 CIM 類別定義中刪除指定的方法。</span><span class="sxs-lookup"><span data-stu-id="ea4bf-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="ea4bf-105">語法</span><span class="sxs-lookup"><span data-stu-id="ea4bf-105">Syntax</span></span>  
  
```  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="ea4bf-106">參數</span><span class="sxs-lookup"><span data-stu-id="ea4bf-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="ea4bf-107">[in]未使用這個參數。</span><span class="sxs-lookup"><span data-stu-id="ea4bf-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="ea4bf-108">[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。</span><span class="sxs-lookup"><span data-stu-id="ea4bf-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`wszName`  
<span data-ttu-id="ea4bf-109">[in]要移除類別資料表中的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="ea4bf-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="ea4bf-110">`wszName`必須是有效的指標`LPCWSTR`。</span><span class="sxs-lookup"><span data-stu-id="ea4bf-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="ea4bf-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="ea4bf-111">Return value</span></span>

<span data-ttu-id="ea4bf-112">這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：</span><span class="sxs-lookup"><span data-stu-id="ea4bf-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ea4bf-113">常數</span><span class="sxs-lookup"><span data-stu-id="ea4bf-113">Constant</span></span>  |<span data-ttu-id="ea4bf-114">值</span><span class="sxs-lookup"><span data-stu-id="ea4bf-114">Value</span></span>  |<span data-ttu-id="ea4bf-115">描述</span><span class="sxs-lookup"><span data-stu-id="ea4bf-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="ea4bf-116">而會收到 0x80041002</span><span class="sxs-lookup"><span data-stu-id="ea4bf-116">0x80041002</span></span> | <span data-ttu-id="ea4bf-117">指定的方法不存在。</span><span class="sxs-lookup"><span data-stu-id="ea4bf-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ea4bf-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ea4bf-118">0x80041006</span></span> | <span data-ttu-id="ea4bf-119">不是記憶體不足，無法完成作業。</span><span class="sxs-lookup"><span data-stu-id="ea4bf-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="ea4bf-120">0</span><span class="sxs-lookup"><span data-stu-id="ea4bf-120">0</span></span> | <span data-ttu-id="ea4bf-121">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="ea4bf-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="ea4bf-122">備註</span><span class="sxs-lookup"><span data-stu-id="ea4bf-122">Remarks</span></span>

<span data-ttu-id="ea4bf-123">此函式會包裝呼叫[IWbemClassObject::DeleteMethod](https://msdn.microsoft.com/library/aa391439(v=vs.85).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="ea4bf-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](https://msdn.microsoft.com/library/aa391439(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="ea4bf-124">不支援方法刪除[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)指向 CIM 執行個體的指標。</span><span class="sxs-lookup"><span data-stu-id="ea4bf-124">Method deletion is not supported for [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="ea4bf-125">需求</span><span class="sxs-lookup"><span data-stu-id="ea4bf-125">Requirements</span></span>  
 <span data-ttu-id="ea4bf-126">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea4bf-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea4bf-127">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ea4bf-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ea4bf-128">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ea4bf-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea4bf-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea4bf-129">See also</span></span>  
[<span data-ttu-id="ea4bf-130">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="ea4bf-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
