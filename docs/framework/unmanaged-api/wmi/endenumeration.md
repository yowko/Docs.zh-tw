---
title: EndEnumeration 函式 （Unmanaged API 參考）
description: EndEnumeration 函式會終止列舉型別。
ms.date: 11/06/2017
api_name:
- EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndEnumeration
helpviewer_keywords:
- EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65904da9efea90d31960d71ae0da8c81dffeccf1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000463"
---
# <a name="endenumeration-function"></a><span data-ttu-id="6a655-103">EndEnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="6a655-103">EndEnumeration function</span></span>

<span data-ttu-id="6a655-104">結束藉由呼叫啟動列舉順序[BeginEnumeration 函式](beginenumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="6a655-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="6a655-105">語法</span><span class="sxs-lookup"><span data-stu-id="6a655-105">Syntax</span></span>

```cpp
HRESULT EndEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```

## <a name="parameters"></a><span data-ttu-id="6a655-106">參數</span><span class="sxs-lookup"><span data-stu-id="6a655-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="6a655-107">[in]未使用此參數。</span><span class="sxs-lookup"><span data-stu-id="6a655-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="6a655-108">[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。</span><span class="sxs-lookup"><span data-stu-id="6a655-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="6a655-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6a655-109">Return value</span></span>

<span data-ttu-id="6a655-110">此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="6a655-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6a655-111">常數</span><span class="sxs-lookup"><span data-stu-id="6a655-111">Constant</span></span>  |<span data-ttu-id="6a655-112">值</span><span class="sxs-lookup"><span data-stu-id="6a655-112">Value</span></span>  |<span data-ttu-id="6a655-113">描述</span><span class="sxs-lookup"><span data-stu-id="6a655-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="6a655-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="6a655-114">0x80041001</span></span> | <span data-ttu-id="6a655-115">已有一般失敗。</span><span class="sxs-lookup"><span data-stu-id="6a655-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6a655-116">0</span><span class="sxs-lookup"><span data-stu-id="6a655-116">0</span></span> | <span data-ttu-id="6a655-117">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="6a655-117">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="6a655-118">備註</span><span class="sxs-lookup"><span data-stu-id="6a655-118">Remarks</span></span>

<span data-ttu-id="6a655-119">此函式會包裝在呼叫[IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)方法。</span><span class="sxs-lookup"><span data-stu-id="6a655-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="6a655-120">呼叫`EndEnumeration`函式不是必要項，但它建議，因為它會釋放與列舉相關聯的資源。</span><span class="sxs-lookup"><span data-stu-id="6a655-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="6a655-121">不過，資源會自動解除配置時啟動下一次列舉或釋放物件。</span><span class="sxs-lookup"><span data-stu-id="6a655-121">However, the resources are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="6a655-122">需求</span><span class="sxs-lookup"><span data-stu-id="6a655-122">Requirements</span></span>

<span data-ttu-id="6a655-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a655-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="6a655-124">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="6a655-124">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="6a655-125">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6a655-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6a655-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a655-126">See also</span></span>

- [<span data-ttu-id="6a655-127">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="6a655-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)