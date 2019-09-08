---
title: SpawnInstance 函式（非受控 API 參考）
description: SpawnInstance 函數會建立類別的新實例。
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 529905bd9286520a8e09479bfc95ef0b614f53e9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798214"
---
# <a name="spawninstance-function"></a><span data-ttu-id="1e438-103">SpawnInstance 函式</span><span class="sxs-lookup"><span data-stu-id="1e438-103">SpawnInstance function</span></span>
<span data-ttu-id="1e438-104">建立類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="1e438-104">Creates a new instance of a class.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="1e438-105">語法</span><span class="sxs-lookup"><span data-stu-id="1e438-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a><span data-ttu-id="1e438-106">參數</span><span class="sxs-lookup"><span data-stu-id="1e438-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="1e438-107">在未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="1e438-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="1e438-108">在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。</span><span class="sxs-lookup"><span data-stu-id="1e438-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="1e438-109">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="1e438-109">[in] Reserved.</span></span> <span data-ttu-id="1e438-110">這個參數必須是0。</span><span class="sxs-lookup"><span data-stu-id="1e438-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="1e438-111">脫銷接收類別之新實例的指標。</span><span class="sxs-lookup"><span data-stu-id="1e438-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="1e438-112">如果發生錯誤，則不會傳回新的物件，且`ppNewInstance`會將其保留為未修改。</span><span class="sxs-lookup"><span data-stu-id="1e438-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="1e438-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="1e438-113">Return value</span></span>

<span data-ttu-id="1e438-114">這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：</span><span class="sxs-lookup"><span data-stu-id="1e438-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1e438-115">常數</span><span class="sxs-lookup"><span data-stu-id="1e438-115">Constant</span></span>  |<span data-ttu-id="1e438-116">值</span><span class="sxs-lookup"><span data-stu-id="1e438-116">Value</span></span>  |<span data-ttu-id="1e438-117">描述</span><span class="sxs-lookup"><span data-stu-id="1e438-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="1e438-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="1e438-118">0x80041020</span></span> | <span data-ttu-id="1e438-119">`ptr`不是有效的類別定義，而且無法產生新的實例。</span><span class="sxs-lookup"><span data-stu-id="1e438-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="1e438-120">可能是未完成，或未透過呼叫[PutClassWmi](putclasswmi.md)向 Windows 管理註冊。</span><span class="sxs-lookup"><span data-stu-id="1e438-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="1e438-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="1e438-121">0x80041006</span></span> | <span data-ttu-id="1e438-122">沒有足夠的記憶體可完成作業。</span><span class="sxs-lookup"><span data-stu-id="1e438-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1e438-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1e438-123">0x80041008</span></span> | <span data-ttu-id="1e438-124">`ppNewClass` 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="1e438-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="1e438-125">0</span><span class="sxs-lookup"><span data-stu-id="1e438-125">0</span></span> | <span data-ttu-id="1e438-126">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="1e438-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="1e438-127">備註</span><span class="sxs-lookup"><span data-stu-id="1e438-127">Remarks</span></span>

<span data-ttu-id="1e438-128">此函式會包裝對[IWbemClassObject：： SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance)方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="1e438-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

<span data-ttu-id="1e438-129">`ptr`必須是從 Windows 管理取得的類別定義。</span><span class="sxs-lookup"><span data-stu-id="1e438-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="1e438-130">（請注意，支援從實例產生實例，但傳回的實例是空的）。接著，您可以使用此類別定義來建立新的實例。</span><span class="sxs-lookup"><span data-stu-id="1e438-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="1e438-131">如果您想要將實例寫入 Windows 管理，則需要呼叫[PutInstanceWmi](putinstancewmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="1e438-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>

<span data-ttu-id="1e438-132">在中`ppNewClass`傳回的新物件會自動成為目前物件的子類別。</span><span class="sxs-lookup"><span data-stu-id="1e438-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="1e438-133">無法覆寫此行為。</span><span class="sxs-lookup"><span data-stu-id="1e438-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="1e438-134">沒有其他方法可建立子類別（衍生類別）。</span><span class="sxs-lookup"><span data-stu-id="1e438-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="1e438-135">需求</span><span class="sxs-lookup"><span data-stu-id="1e438-135">Requirements</span></span>  
 <span data-ttu-id="1e438-136">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1e438-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e438-137">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1e438-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1e438-138">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1e438-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e438-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e438-139">See also</span></span>

- [<span data-ttu-id="1e438-140">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="1e438-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
