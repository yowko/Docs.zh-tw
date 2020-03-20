---
title: 祝福IWbem服務物件功能（非託管 API 引用）
description: 祝福IWbem服務物件功能指示使用者憑據是否允許訪問 IWbem 服務物件
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fd822f78d29ad3a75fb5e57dd7c23b7049d445b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175027"
---
# <a name="blessiwbemservicesobject-function"></a><span data-ttu-id="fc6ac-103">BlessIWbemServicesObject 函式</span><span class="sxs-lookup"><span data-stu-id="fc6ac-103">BlessIWbemServicesObject function</span></span>
<span data-ttu-id="fc6ac-104">指示使用者憑據是否允許訪問指定的[IWbem 服務](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)物件。</span><span class="sxs-lookup"><span data-stu-id="fc6ac-104">Indicates whether the user credentials permit access to a specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="fc6ac-105">語法</span><span class="sxs-lookup"><span data-stu-id="fc6ac-105">Syntax</span></span>

```cpp
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```

## <a name="parameters"></a><span data-ttu-id="fc6ac-106">參數</span><span class="sxs-lookup"><span data-stu-id="fc6ac-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="fc6ac-107">[在]指向 WMI 服務物件的指標。</span><span class="sxs-lookup"><span data-stu-id="fc6ac-107">[in] A pointer to a WMI service object.</span></span>

`strUser`\
<span data-ttu-id="fc6ac-108">[在]使用者名。</span><span class="sxs-lookup"><span data-stu-id="fc6ac-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="fc6ac-109">[在]與`strUser`關聯的密碼。</span><span class="sxs-lookup"><span data-stu-id="fc6ac-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="fc6ac-110">[在]使用者的功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="fc6ac-110">[in] The domain name of the user.</span></span> <span data-ttu-id="fc6ac-111">有關詳細資訊，請參閱[ConnectServerWmi](connectserverwmi.md)函數。</span><span class="sxs-lookup"><span data-stu-id="fc6ac-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="fc6ac-112">[在]類比級別。</span><span class="sxs-lookup"><span data-stu-id="fc6ac-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="fc6ac-113">[在]授權級別。</span><span class="sxs-lookup"><span data-stu-id="fc6ac-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="fc6ac-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="fc6ac-114">Return value</span></span>

<span data-ttu-id="fc6ac-115">此函數返回的以下值在*WinError.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：</span><span class="sxs-lookup"><span data-stu-id="fc6ac-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="fc6ac-116">持續性</span><span class="sxs-lookup"><span data-stu-id="fc6ac-116">Constant</span></span>  |<span data-ttu-id="fc6ac-117">值</span><span class="sxs-lookup"><span data-stu-id="fc6ac-117">Value</span></span>  |<span data-ttu-id="fc6ac-118">描述</span><span class="sxs-lookup"><span data-stu-id="fc6ac-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="fc6ac-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="fc6ac-119">0x80070057</span></span> | <span data-ttu-id="fc6ac-120">一個或多個參數無效。</span><span class="sxs-lookup"><span data-stu-id="fc6ac-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="fc6ac-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="fc6ac-121">0x80004003</span></span> | <span data-ttu-id="fc6ac-122">`pIWbemServices` 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="fc6ac-122">`pIWbemServices` is `null`.</span></span> |
| `E_FAIL` | <span data-ttu-id="fc6ac-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="fc6ac-123">0x80000008</span></span> | <span data-ttu-id="fc6ac-124">發生未指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="fc6ac-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="fc6ac-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="fc6ac-125">0x80000002</span></span> | <span data-ttu-id="fc6ac-126">可用記憶體不足以執行操作。</span><span class="sxs-lookup"><span data-stu-id="fc6ac-126">Insufficient memory is available to perform the operation.</span></span> |
| `S_OK` | <span data-ttu-id="fc6ac-127">0</span><span class="sxs-lookup"><span data-stu-id="fc6ac-127">0</span></span> | <span data-ttu-id="fc6ac-128">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="fc6ac-128">The function call was successful.</span></span> |

## <a name="requirements"></a><span data-ttu-id="fc6ac-129">需求</span><span class="sxs-lookup"><span data-stu-id="fc6ac-129">Requirements</span></span>

 <span data-ttu-id="fc6ac-130">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc6ac-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="fc6ac-131">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="fc6ac-131">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="fc6ac-132">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fc6ac-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="fc6ac-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc6ac-133">See also</span></span>

- [<span data-ttu-id="fc6ac-134">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="fc6ac-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
