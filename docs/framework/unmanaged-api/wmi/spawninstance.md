---
title: 'SpawnInstance 函式 (非受控 API 參考) '
description: SpawnInstance 函式會建立類別的新實例。
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
ms.openlocfilehash: 176bc83dd02381af8c2bc3995a37e7fee7c1bebf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732225"
---
# <a name="spawninstance-function"></a><span data-ttu-id="2697a-103">SpawnInstance 函式</span><span class="sxs-lookup"><span data-stu-id="2697a-103">SpawnInstance function</span></span>

<span data-ttu-id="2697a-104">建立類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="2697a-104">Creates a new instance of a class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="2697a-105">語法</span><span class="sxs-lookup"><span data-stu-id="2697a-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance);
```  

## <a name="parameters"></a><span data-ttu-id="2697a-106">參數</span><span class="sxs-lookup"><span data-stu-id="2697a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="2697a-107">在此參數未使用。</span><span class="sxs-lookup"><span data-stu-id="2697a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="2697a-108">在 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 實例的指標。</span><span class="sxs-lookup"><span data-stu-id="2697a-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="2697a-109">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="2697a-109">[in] Reserved.</span></span> <span data-ttu-id="2697a-110">此參數必須為0。</span><span class="sxs-lookup"><span data-stu-id="2697a-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="2697a-111">擴展接收類別新實例的指標。</span><span class="sxs-lookup"><span data-stu-id="2697a-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="2697a-112">如果發生錯誤，則不會傳回新的物件，而且 `ppNewInstance` 會保持未修改狀態。</span><span class="sxs-lookup"><span data-stu-id="2697a-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="2697a-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="2697a-113">Return value</span></span>

<span data-ttu-id="2697a-114">這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="2697a-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2697a-115">常數</span><span class="sxs-lookup"><span data-stu-id="2697a-115">Constant</span></span>  |<span data-ttu-id="2697a-116">值</span><span class="sxs-lookup"><span data-stu-id="2697a-116">Value</span></span>  |<span data-ttu-id="2697a-117">描述</span><span class="sxs-lookup"><span data-stu-id="2697a-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="2697a-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="2697a-118">0x80041020</span></span> | <span data-ttu-id="2697a-119">`ptr` 不是有效的類別定義，也無法產生新的實例。</span><span class="sxs-lookup"><span data-stu-id="2697a-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="2697a-120">可能是未完成，或尚未藉由呼叫 [PutClassWmi](putclasswmi.md)向 Windows 管理註冊。</span><span class="sxs-lookup"><span data-stu-id="2697a-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2697a-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2697a-121">0x80041006</span></span> | <span data-ttu-id="2697a-122">可用的記憶體不足，無法完成作業。</span><span class="sxs-lookup"><span data-stu-id="2697a-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2697a-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2697a-123">0x80041008</span></span> | <span data-ttu-id="2697a-124">`ppNewClass` 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="2697a-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="2697a-125">0</span><span class="sxs-lookup"><span data-stu-id="2697a-125">0</span></span> | <span data-ttu-id="2697a-126">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="2697a-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2697a-127">備註</span><span class="sxs-lookup"><span data-stu-id="2697a-127">Remarks</span></span>

<span data-ttu-id="2697a-128">此函數會包裝對 [IWbemClassObject：： SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="2697a-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

<span data-ttu-id="2697a-129">`ptr` 必須是從 Windows 管理取得的類別定義。</span><span class="sxs-lookup"><span data-stu-id="2697a-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="2697a-130"> (請注意，支援從實例產生實例，但是傳回的實例是空的。 ) 您接著使用這個類別定義來建立新的實例。</span><span class="sxs-lookup"><span data-stu-id="2697a-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="2697a-131">如果您想要將實例寫入 Windows 管理，則需要呼叫 [PutInstanceWmi](putinstancewmi.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="2697a-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>

<span data-ttu-id="2697a-132">中傳回的新物件 `ppNewClass` 會自動成為目前物件的子類別。</span><span class="sxs-lookup"><span data-stu-id="2697a-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="2697a-133">無法覆寫此行為。</span><span class="sxs-lookup"><span data-stu-id="2697a-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="2697a-134">無法建立子類別 (衍生類別) 的其他方法。</span><span class="sxs-lookup"><span data-stu-id="2697a-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="2697a-135">需求</span><span class="sxs-lookup"><span data-stu-id="2697a-135">Requirements</span></span>  

 <span data-ttu-id="2697a-136">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2697a-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2697a-137">**標頭：** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="2697a-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2697a-138">**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2697a-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2697a-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2697a-139">See also</span></span>

- [<span data-ttu-id="2697a-140">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="2697a-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
