---
title: BlessIWbemServicesObject 函式 （Unmanaged API 參考）
description: BlessIWbemServicesObject 函式表示的使用者認證是否允許 IWbemServices 物件的存取權
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1380d03d4456e0695777775ae786a19982d691b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864403"
---
# <a name="blessiwbemservicesobject-function"></a><span data-ttu-id="04bb2-103">BlessIWbemServicesObject 函式</span><span class="sxs-lookup"><span data-stu-id="04bb2-103">BlessIWbemServicesObject function</span></span>
<span data-ttu-id="04bb2-104">表示使用者認證是否允許指定的存取[IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices)物件。</span><span class="sxs-lookup"><span data-stu-id="04bb2-104">Indicates whether the user credentials permit access to a specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="04bb2-105">語法</span><span class="sxs-lookup"><span data-stu-id="04bb2-105">Syntax</span></span>  
  
```  
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a><span data-ttu-id="04bb2-106">參數</span><span class="sxs-lookup"><span data-stu-id="04bb2-106">Parameters</span></span>

`pIWbemServices`  
<span data-ttu-id="04bb2-107">[in]WMI 服務物件的指標。</span><span class="sxs-lookup"><span data-stu-id="04bb2-107">[in] A pointer to a WMI service object.</span></span>

`strUser`  
<span data-ttu-id="04bb2-108">[in]使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="04bb2-108">[in] The user name.</span></span>

`strPassword`  
<span data-ttu-id="04bb2-109">[in]與相關聯的密碼`strUser`。</span><span class="sxs-lookup"><span data-stu-id="04bb2-109">[in] The password associated with `strUser`.</span></span>

<span data-ttu-id="04bb2-110">`strAuthority` [in]使用者的網域名稱。</span><span class="sxs-lookup"><span data-stu-id="04bb2-110">`strAuthority` [in] The domain name of the user.</span></span> <span data-ttu-id="04bb2-111">請參閱[ConnectServerWmi](connectserverwmi.md)函式，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="04bb2-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="04bb2-112">`impLevel` [in]模擬等級。</span><span class="sxs-lookup"><span data-stu-id="04bb2-112">`impLevel` [in] The impersonation level.</span></span>

<span data-ttu-id="04bb2-113">`authnLevel` [in]授權層級。</span><span class="sxs-lookup"><span data-stu-id="04bb2-113">`authnLevel` [in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="04bb2-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="04bb2-114">Return value</span></span>

<span data-ttu-id="04bb2-115">此函式所傳回的下列值中定義*WinError.h*標頭檔，或者您可以將其定義為常數中程式碼：</span><span class="sxs-lookup"><span data-stu-id="04bb2-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="04bb2-116">常數</span><span class="sxs-lookup"><span data-stu-id="04bb2-116">Constant</span></span>  |<span data-ttu-id="04bb2-117">值</span><span class="sxs-lookup"><span data-stu-id="04bb2-117">Value</span></span>  |<span data-ttu-id="04bb2-118">描述</span><span class="sxs-lookup"><span data-stu-id="04bb2-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="04bb2-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="04bb2-119">0x80070057</span></span> | <span data-ttu-id="04bb2-120">一或多個引數均為無效。</span><span class="sxs-lookup"><span data-stu-id="04bb2-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="04bb2-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="04bb2-121">0x80004003</span></span> | <span data-ttu-id="04bb2-122">`pIWbemServices` 為 `null`。</span><span class="sxs-lookup"><span data-stu-id="04bb2-122">`pIWbemServices` is `null`.</span></span> | 
| `E_FAIL` | <span data-ttu-id="04bb2-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="04bb2-123">0x80000008</span></span> | <span data-ttu-id="04bb2-124">發生未指定的錯誤。</span><span class="sxs-lookup"><span data-stu-id="04bb2-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="04bb2-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="04bb2-125">0x80000002</span></span> | <span data-ttu-id="04bb2-126">沒有足夠的記憶體可供執行作業。</span><span class="sxs-lookup"><span data-stu-id="04bb2-126">Insufficient memory is available to perform the operation.</span></span> | 
| `S_OK` | <span data-ttu-id="04bb2-127">0</span><span class="sxs-lookup"><span data-stu-id="04bb2-127">0</span></span> | <span data-ttu-id="04bb2-128">函式呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="04bb2-128">The function call was successful.</span></span> | 

## <a name="requirements"></a><span data-ttu-id="04bb2-129">需求</span><span class="sxs-lookup"><span data-stu-id="04bb2-129">Requirements</span></span>  
 <span data-ttu-id="04bb2-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="04bb2-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04bb2-131">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="04bb2-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="04bb2-132">**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="04bb2-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04bb2-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04bb2-133">See also</span></span>  
[<span data-ttu-id="04bb2-134">WMI 和效能計數器 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="04bb2-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
