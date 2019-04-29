---
title: SpawnInstance 函式 （Unmanaged API 參考）
description: SpawnInstance 函式會建立類別的新執行個體。
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
ms.openlocfilehash: 8056ef18089f56f1f9b6717d505fa3d058957541
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782522"
---
# <a name="spawninstance-function"></a><span data-ttu-id="74f49-103">SpawnInstance 函式</span><span class="sxs-lookup"><span data-stu-id="74f49-103">SpawnInstance function</span></span>
<span data-ttu-id="74f49-104">建立類別的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="74f49-104">Creates a new instance of a class.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="74f49-105">語法</span><span class="sxs-lookup"><span data-stu-id="74f49-105">Syntax</span></span>  
  
```  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a><span data-ttu-id="74f49-106">參數</span><span class="sxs-lookup"><span data-stu-id="74f49-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="74f49-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="74f49-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="74f49-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="74f49-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="74f49-109">[in] 保留。</span><span class="sxs-lookup"><span data-stu-id="74f49-109">[in] Reserved.</span></span> <span data-ttu-id="74f49-110">這個參數必須是 0。</span><span class="sxs-lookup"><span data-stu-id="74f49-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="74f49-111">[out]接收此類別的新執行個體的指標。</span><span class="sxs-lookup"><span data-stu-id="74f49-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="74f49-112">發生錯誤時，新的物件不是傳回，和`ppNewInstance`左未經修改。</span><span class="sxs-lookup"><span data-stu-id="74f49-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="74f49-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="74f49-113">Return value</span></span>

<span data-ttu-id="74f49-114">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="74f49-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="74f49-115">常數</span><span class="sxs-lookup"><span data-stu-id="74f49-115">Constant</span></span>  |<span data-ttu-id="74f49-116">值</span><span class="sxs-lookup"><span data-stu-id="74f49-116">Value</span></span>  |<span data-ttu-id="74f49-117">描述</span><span class="sxs-lookup"><span data-stu-id="74f49-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="74f49-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="74f49-118">0x80041020</span></span> | <span data-ttu-id="74f49-119">`ptr` 不是有效的類別定義，並無法繁衍 （spawn） 的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="74f49-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="74f49-120">已完成，或它尚未註冊使用 Windows Management 藉由呼叫[PutClassWmi](putclasswmi.md)。</span><span class="sxs-lookup"><span data-stu-id="74f49-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="74f49-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="74f49-121">0x80041006</span></span> | <span data-ttu-id="74f49-122">沒有足夠的記憶體可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="74f49-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="74f49-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="74f49-123">0x80041008</span></span> | <span data-ttu-id="74f49-124">`ppNewClass` 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="74f49-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="74f49-125">0</span><span class="sxs-lookup"><span data-stu-id="74f49-125">0</span></span> | <span data-ttu-id="74f49-126">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="74f49-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="74f49-127">備註</span><span class="sxs-lookup"><span data-stu-id="74f49-127">Remarks</span></span>

<span data-ttu-id="74f49-128">此函式會包裝在呼叫[IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance)方法。</span><span class="sxs-lookup"><span data-stu-id="74f49-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

<span data-ttu-id="74f49-129">`ptr` 必須在類別定義取得從 Windows 管理。</span><span class="sxs-lookup"><span data-stu-id="74f49-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="74f49-130">（請注意，支援繁衍的執行個體從執行個體，但傳回的執行個體是空的）。然後，您會使用此類別定義來建立新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="74f49-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="74f49-131">呼叫[PutInstanceWmi](putinstancewmi.md)函式是必要的如果您想要撰寫 Windows 管理的執行個體。</span><span class="sxs-lookup"><span data-stu-id="74f49-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>

<span data-ttu-id="74f49-132">新的物件中傳回`ppNewClass`會自動變成目前物件的子類別。</span><span class="sxs-lookup"><span data-stu-id="74f49-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="74f49-133">無法覆寫這個行為。</span><span class="sxs-lookup"><span data-stu-id="74f49-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="74f49-134">沒有任何其他子類別 （衍生類別） 可以建立的方法。</span><span class="sxs-lookup"><span data-stu-id="74f49-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="74f49-135">需求</span><span class="sxs-lookup"><span data-stu-id="74f49-135">Requirements</span></span>  
 <span data-ttu-id="74f49-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74f49-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74f49-137">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="74f49-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="74f49-138">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="74f49-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74f49-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74f49-139">See also</span></span>

- [<span data-ttu-id="74f49-140">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="74f49-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
