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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8d3a7168ce0ee3484384ae0e2d10ca00367fc9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432855"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="37e77-102">GetRequestedRuntimeVersionForCLSID 函式</span><span class="sxs-lookup"><span data-stu-id="37e77-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="37e77-103">取得適當 common language runtime (CLR) 版本資訊與指定類別`CLSID`。</span><span class="sxs-lookup"><span data-stu-id="37e77-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="37e77-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="37e77-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37e77-105">語法</span><span class="sxs-lookup"><span data-stu-id="37e77-105">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37e77-106">參數</span><span class="sxs-lookup"><span data-stu-id="37e77-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="37e77-107">[in] `CLSID`的元件。</span><span class="sxs-lookup"><span data-stu-id="37e77-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="37e77-108">[out] 這種緩衝區包含成功完成時的版本號碼字串。</span><span class="sxs-lookup"><span data-stu-id="37e77-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="37e77-109">[in] 大小，以寬字元為單位的`pVersion`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="37e77-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="37e77-110">[out]傳回的緩衝區長度，單位為位元組。</span><span class="sxs-lookup"><span data-stu-id="37e77-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="37e77-111">[in] CLSID_RESOLUTION_FLAGS 值的其中一個。</span><span class="sxs-lookup"><span data-stu-id="37e77-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="37e77-112">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="37e77-112">The following values are supported:</span></span>  
  
-   <span data-ttu-id="37e77-113">CLSID_RESOLUTION_DEFAULT: (0x0) 指定該預設 interop 行為應該使用。</span><span class="sxs-lookup"><span data-stu-id="37e77-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
-   <span data-ttu-id="37e77-114">CLSID_RESOLUTION_REGISTERED: (0x1) 登錄也應搜尋和填充碼原則的指定應該套用。</span><span class="sxs-lookup"><span data-stu-id="37e77-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37e77-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="37e77-115">Return Value</span></span>  
  
|<span data-ttu-id="37e77-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37e77-116">HRESULT</span></span>|<span data-ttu-id="37e77-117">描述</span><span class="sxs-lookup"><span data-stu-id="37e77-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37e77-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="37e77-118">S_OK</span></span>|<span data-ttu-id="37e77-119">此函式成功傳回。</span><span class="sxs-lookup"><span data-stu-id="37e77-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="37e77-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="37e77-120">E_INVALIDARG</span></span>|<span data-ttu-id="37e77-121">其中一個參數具有無效的類型或格式。</span><span class="sxs-lookup"><span data-stu-id="37e77-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="37e77-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="37e77-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="37e77-123">`pVersion`緩衝區不夠大，足以容納整個版本字串。</span><span class="sxs-lookup"><span data-stu-id="37e77-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="37e77-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="37e77-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="37e77-125">沒有任何類別登錄具有指定`CLSID`。</span><span class="sxs-lookup"><span data-stu-id="37e77-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="37e77-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="37e77-126">E_POINTER</span></span>|<span data-ttu-id="37e77-127">`dwLength` 為 null，或`cchBuffer`夠大，無法保存的版本字串，但`pVersion`為 null。</span><span class="sxs-lookup"><span data-stu-id="37e77-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37e77-128">需求</span><span class="sxs-lookup"><span data-stu-id="37e77-128">Requirements</span></span>  
 <span data-ttu-id="37e77-129">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="37e77-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37e77-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="37e77-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37e77-131">**.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37e77-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37e77-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37e77-132">See Also</span></span>  
 [<span data-ttu-id="37e77-133">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="37e77-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
