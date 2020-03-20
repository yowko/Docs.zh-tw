---
title: 生成實例函數（非託管 API 引用）
description: SpawnInstance 函數創建類的新實例。
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: a15eb8123c1ee807444bdb4c6fe71cdccc08f434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176717"
---
# <a name="spawninstance-function"></a><span data-ttu-id="a9a40-103">SpawnInstance 函式</span><span class="sxs-lookup"><span data-stu-id="a9a40-103">SpawnInstance function</span></span>
<span data-ttu-id="a9a40-104">建立類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="a9a40-104">Creates a new instance of a class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a9a40-105">語法</span><span class="sxs-lookup"><span data-stu-id="a9a40-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance);
```  

## <a name="parameters"></a><span data-ttu-id="a9a40-106">參數</span><span class="sxs-lookup"><span data-stu-id="a9a40-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a9a40-107">[在]此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="a9a40-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a9a40-108">[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。</span><span class="sxs-lookup"><span data-stu-id="a9a40-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="a9a40-109">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="a9a40-109">[in] Reserved.</span></span> <span data-ttu-id="a9a40-110">此參數必須為 0。</span><span class="sxs-lookup"><span data-stu-id="a9a40-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="a9a40-111">[出]接收指向類新實例的指標。</span><span class="sxs-lookup"><span data-stu-id="a9a40-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="a9a40-112">如果發生錯誤，則不會返回新物件，並且`ppNewInstance`未修改。</span><span class="sxs-lookup"><span data-stu-id="a9a40-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="a9a40-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="a9a40-113">Return value</span></span>

<span data-ttu-id="a9a40-114">此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="a9a40-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a9a40-115">持續性</span><span class="sxs-lookup"><span data-stu-id="a9a40-115">Constant</span></span>  |<span data-ttu-id="a9a40-116">值</span><span class="sxs-lookup"><span data-stu-id="a9a40-116">Value</span></span>  |<span data-ttu-id="a9a40-117">描述</span><span class="sxs-lookup"><span data-stu-id="a9a40-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="a9a40-118">0 x80041020</span><span class="sxs-lookup"><span data-stu-id="a9a40-118">0x80041020</span></span> | <span data-ttu-id="a9a40-119">`ptr`不是有效的類定義，不能生成新實例。</span><span class="sxs-lookup"><span data-stu-id="a9a40-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="a9a40-120">要麼不完整，要麼沒有通過調用[PutClassWmi](putclasswmi.md)在 Windows 管理中註冊。</span><span class="sxs-lookup"><span data-stu-id="a9a40-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a9a40-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a9a40-121">0x80041006</span></span> | <span data-ttu-id="a9a40-122">可用的記憶體不足，無法完成作業。</span><span class="sxs-lookup"><span data-stu-id="a9a40-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a9a40-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a9a40-123">0x80041008</span></span> | <span data-ttu-id="a9a40-124">`ppNewClass` 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="a9a40-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="a9a40-125">0</span><span class="sxs-lookup"><span data-stu-id="a9a40-125">0</span></span> | <span data-ttu-id="a9a40-126">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="a9a40-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="a9a40-127">備註</span><span class="sxs-lookup"><span data-stu-id="a9a40-127">Remarks</span></span>

<span data-ttu-id="a9a40-128">此函數將調用包起來到[IWbem ClassObject：：spawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance)方法。</span><span class="sxs-lookup"><span data-stu-id="a9a40-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

<span data-ttu-id="a9a40-129">`ptr`必須是從 Windows 管理獲取的類定義。</span><span class="sxs-lookup"><span data-stu-id="a9a40-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="a9a40-130">（請注意，支援從實例生成實例，但返回的實例為空。然後，使用此類定義創建新實例。</span><span class="sxs-lookup"><span data-stu-id="a9a40-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="a9a40-131">如果要將實例寫入 Windows 管理，則需要調用[PutInstanceWmi](putinstancewmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="a9a40-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>

<span data-ttu-id="a9a40-132">返回`ppNewClass`的新物件將自動成為當前物件的子類。</span><span class="sxs-lookup"><span data-stu-id="a9a40-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="a9a40-133">無法重寫此行為。</span><span class="sxs-lookup"><span data-stu-id="a9a40-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="a9a40-134">沒有其他方法可以創建子類（派生類）。</span><span class="sxs-lookup"><span data-stu-id="a9a40-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="a9a40-135">需求</span><span class="sxs-lookup"><span data-stu-id="a9a40-135">Requirements</span></span>  
 <span data-ttu-id="a9a40-136">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a9a40-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9a40-137">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a9a40-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a9a40-138">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a9a40-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9a40-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9a40-139">See also</span></span>

- [<span data-ttu-id="a9a40-140">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="a9a40-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
