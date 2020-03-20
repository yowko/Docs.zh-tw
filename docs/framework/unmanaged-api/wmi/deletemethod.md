---
title: 刪除方法函數（非託管 API 引用）
description: DeleteMethod 函數從 CIM 類定義中刪除指定的方法。
ms.date: 11/06/2017
api_name:
- DeleteMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- DeleteMethod
helpviewer_keywords:
- DeleteMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4059555d74c0b0f151332ddcf9faedecf238e795
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174988"
---
# <a name="deletemethod-function"></a><span data-ttu-id="52a12-103">DeleteMethod 函式</span><span class="sxs-lookup"><span data-stu-id="52a12-103">DeleteMethod function</span></span>
<span data-ttu-id="52a12-104">從 CIM 類定義中刪除指定的方法。</span><span class="sxs-lookup"><span data-stu-id="52a12-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="52a12-105">語法</span><span class="sxs-lookup"><span data-stu-id="52a12-105">Syntax</span></span>  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="52a12-106">參數</span><span class="sxs-lookup"><span data-stu-id="52a12-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="52a12-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="52a12-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="52a12-108">[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="52a12-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="52a12-109">[在]要從類表中刪除的方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="52a12-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="52a12-110">`wszName`必須是指向有效`LPCWSTR`指標的 指標。</span><span class="sxs-lookup"><span data-stu-id="52a12-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="52a12-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="52a12-111">Return value</span></span>

<span data-ttu-id="52a12-112">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="52a12-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="52a12-113">持續性</span><span class="sxs-lookup"><span data-stu-id="52a12-113">Constant</span></span>  |<span data-ttu-id="52a12-114">值</span><span class="sxs-lookup"><span data-stu-id="52a12-114">Value</span></span>  |<span data-ttu-id="52a12-115">描述</span><span class="sxs-lookup"><span data-stu-id="52a12-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="52a12-116">0 x80041002</span><span class="sxs-lookup"><span data-stu-id="52a12-116">0x80041002</span></span> | <span data-ttu-id="52a12-117">指定的方法不存在。</span><span class="sxs-lookup"><span data-stu-id="52a12-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="52a12-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="52a12-118">0x80041006</span></span> | <span data-ttu-id="52a12-119">記憶體不足，無法完成此作業。</span><span class="sxs-lookup"><span data-stu-id="52a12-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="52a12-120">0</span><span class="sxs-lookup"><span data-stu-id="52a12-120">0</span></span> | <span data-ttu-id="52a12-121">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="52a12-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="52a12-122">備註</span><span class="sxs-lookup"><span data-stu-id="52a12-122">Remarks</span></span>

<span data-ttu-id="52a12-123">此函數包裝對[IWbemClassObject：:Delete 方法的](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod)調用。</span><span class="sxs-lookup"><span data-stu-id="52a12-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="52a12-124">對於指向 CIM 實例的[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指標，不支援方法刪除。</span><span class="sxs-lookup"><span data-stu-id="52a12-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="52a12-125">需求</span><span class="sxs-lookup"><span data-stu-id="52a12-125">Requirements</span></span>  
 <span data-ttu-id="52a12-126">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="52a12-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52a12-127">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="52a12-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="52a12-128">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="52a12-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52a12-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52a12-129">See also</span></span>

- [<span data-ttu-id="52a12-130">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="52a12-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
