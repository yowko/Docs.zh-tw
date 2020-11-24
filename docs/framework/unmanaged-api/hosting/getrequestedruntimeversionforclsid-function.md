---
title: GetRequestedRuntimeVersionForCLSID 函式
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
ms.openlocfilehash: 3afb89a42d7e26c5e89e6f9458ef3406cc0102ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684183"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="3a63c-102">GetRequestedRuntimeVersionForCLSID 函式</span><span class="sxs-lookup"><span data-stu-id="3a63c-102">GetRequestedRuntimeVersionForCLSID Function</span></span>

<span data-ttu-id="3a63c-103">取得適當的 common language runtime (CLR) 具有指定之類別的版本資訊 `CLSID` 。</span><span class="sxs-lookup"><span data-stu-id="3a63c-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="3a63c-104">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="3a63c-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a63c-105">語法</span><span class="sxs-lookup"><span data-stu-id="3a63c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,
    [out]  LPWSTR     pVersion,
    [in]  DWORD      cchBuffer,
    [out] DWORD*     dwLength,
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a63c-106">參數</span><span class="sxs-lookup"><span data-stu-id="3a63c-106">Parameters</span></span>  

 `rclsid`  
 <span data-ttu-id="3a63c-107">在 `CLSID` 元件的。</span><span class="sxs-lookup"><span data-stu-id="3a63c-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="3a63c-108">擴展 在成功完成時包含版本號碼字串的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="3a63c-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="3a63c-109">在 緩衝區的大小（以寬字元為單位） `pVersion` 。</span><span class="sxs-lookup"><span data-stu-id="3a63c-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="3a63c-110">擴展傳回之緩衝區的長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="3a63c-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="3a63c-111">在 其中一個 CLSID_RESOLUTION_FLAGS 值。</span><span class="sxs-lookup"><span data-stu-id="3a63c-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="3a63c-112">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="3a63c-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="3a63c-113">CLSID_RESOLUTION_DEFAULT： (0x0) 指定應使用預設 interop 行為。</span><span class="sxs-lookup"><span data-stu-id="3a63c-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="3a63c-114">CLSID_RESOLUTION_REGISTERED： (0x1) 指定應搜尋登錄並套用填充碼原則。</span><span class="sxs-lookup"><span data-stu-id="3a63c-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a63c-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="3a63c-115">Return Value</span></span>  
  
|<span data-ttu-id="3a63c-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a63c-116">HRESULT</span></span>|<span data-ttu-id="3a63c-117">描述</span><span class="sxs-lookup"><span data-stu-id="3a63c-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a63c-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a63c-118">S_OK</span></span>|<span data-ttu-id="3a63c-119">函數傳回成功。</span><span class="sxs-lookup"><span data-stu-id="3a63c-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="3a63c-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3a63c-120">E_INVALIDARG</span></span>|<span data-ttu-id="3a63c-121">其中一個參數的類型或格式無效。</span><span class="sxs-lookup"><span data-stu-id="3a63c-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="3a63c-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="3a63c-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="3a63c-123">`pVersion`緩衝區不夠大，無法容納整個版本字串。</span><span class="sxs-lookup"><span data-stu-id="3a63c-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="3a63c-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="3a63c-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="3a63c-125">未向指定的註冊任何類別 `CLSID` 。</span><span class="sxs-lookup"><span data-stu-id="3a63c-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="3a63c-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="3a63c-126">E_POINTER</span></span>|<span data-ttu-id="3a63c-127">`dwLength` 為 null，或 `cchBuffer` 夠大，足以容納版本字串，但卻 `pVersion` 是 null。</span><span class="sxs-lookup"><span data-stu-id="3a63c-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a63c-128">需求</span><span class="sxs-lookup"><span data-stu-id="3a63c-128">Requirements</span></span>  

 <span data-ttu-id="3a63c-129">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3a63c-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a63c-130">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3a63c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a63c-131">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a63c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a63c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a63c-132">See also</span></span>

- [<span data-ttu-id="3a63c-133">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="3a63c-133">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
