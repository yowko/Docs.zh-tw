---
title: "CertVerifyAuthenticodeLicense 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertVerifyAuthenticodeLicense
api_location: clr.dll
api_type: DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16d8067b4cd5d0a7b3db5be5b3b9ed4d689e1b0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="certverifyauthenticodelicense-function"></a><span data-ttu-id="890ec-102">CertVerifyAuthenticodeLicense 函式</span><span class="sxs-lookup"><span data-stu-id="890ec-102">CertVerifyAuthenticodeLicense Function</span></span>
<span data-ttu-id="890ec-103">驗證 Authenticode XrML 授權的有效性。</span><span class="sxs-lookup"><span data-stu-id="890ec-103">Verifies the validity of an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="890ec-104">語法</span><span class="sxs-lookup"><span data-stu-id="890ec-104">Syntax</span></span>  
  
```  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="890ec-105">參數</span><span class="sxs-lookup"><span data-stu-id="890ec-105">Parameters</span></span>  
 `pLicenseBlob`  
 <span data-ttu-id="890ec-106">[in] 要驗證的 Authenticode XrML 授權。</span><span class="sxs-lookup"><span data-stu-id="890ec-106">[in] The Authenticode XrML license to be verified.</span></span>  
  
 <span data-ttu-id="890ec-107">請參閱[CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)結構。</span><span class="sxs-lookup"><span data-stu-id="890ec-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="890ec-108">[in] 選用。</span><span class="sxs-lookup"><span data-stu-id="890ec-108">[in] Optional.</span></span> <span data-ttu-id="890ec-109">下列值的組合：</span><span class="sxs-lookup"><span data-stu-id="890ec-109">A combination of following values:</span></span>  
  
-   <span data-ttu-id="890ec-110">AXL_REVOCATION_NO_CHECK</span><span class="sxs-lookup"><span data-stu-id="890ec-110">AXL_REVOCATION_NO_CHECK</span></span>  
  
-   <span data-ttu-id="890ec-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span><span class="sxs-lookup"><span data-stu-id="890ec-111">AXL_REVOCATION_CHECK_END_CERT_ONLY</span></span>  
  
-   <span data-ttu-id="890ec-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span><span class="sxs-lookup"><span data-stu-id="890ec-112">AXL_REVOCATION_CHECK_ENTIRE_CHAIN</span></span>  
  
-   <span data-ttu-id="890ec-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span><span class="sxs-lookup"><span data-stu-id="890ec-113">AXL_URL_CACHE_ONLY_RETRIEVAL</span></span>  
  
-   <span data-ttu-id="890ec-114">AXL_LIFETIME_SIGNING</span><span class="sxs-lookup"><span data-stu-id="890ec-114">AXL_LIFETIME_SIGNING</span></span>  
  
-   <span data-ttu-id="890ec-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span><span class="sxs-lookup"><span data-stu-id="890ec-115">AXL_TRUST_MICROSOFT_ROOT_ONLY</span></span>  
  
 `pSignerInfo`  
 <span data-ttu-id="890ec-116">[out] 接收簽署者的資訊。</span><span class="sxs-lookup"><span data-stu-id="890ec-116">[out] To receive the signer's information.</span></span> <span data-ttu-id="890ec-117">若授權未經簽署，`dwError` 會設為 TRUST_E_NOSIGNATURE。</span><span class="sxs-lookup"><span data-stu-id="890ec-117">If the license wasn't signed, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="890ec-118">它是使用釋放資源的呼叫端的責任[CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)之後使用的函式。</span><span class="sxs-lookup"><span data-stu-id="890ec-118">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="890ec-119">請參閱[AXL_AUTHENTICODE_SIGNER_INFO 結構](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="890ec-119">See [AXL_AUTHENTICODE_SIGNER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md).</span></span>  
  
 `pTimestamperInfo`  
 <span data-ttu-id="890ec-120">[out] 接收時間戳記設定者的資訊 (如有提供)。</span><span class="sxs-lookup"><span data-stu-id="890ec-120">[out] To receive time stamper's information, if available.</span></span> <span data-ttu-id="890ec-121">若授權未設定時間戳記，`dwError` 會設為 TRUST_E_NOSIGNATURE。</span><span class="sxs-lookup"><span data-stu-id="890ec-121">If the license was not time-stamped, `dwError` is set to TRUST_E_NOSIGNATURE.</span></span> <span data-ttu-id="890ec-122">它是使用釋放資源的呼叫端的責任[CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)之後使用的函式。</span><span class="sxs-lookup"><span data-stu-id="890ec-122">It is the caller's responsibility to free resources by using the [CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md) function after use.</span></span>  
  
 <span data-ttu-id="890ec-123">請參閱[AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="890ec-123">See [AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="890ec-124">傳回值</span><span class="sxs-lookup"><span data-stu-id="890ec-124">Return Value</span></span>  
 <span data-ttu-id="890ec-125">若成功，會傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="890ec-125">Returns `S_OK` if successful.</span></span> <span data-ttu-id="890ec-126">反之則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="890ec-126">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="890ec-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="890ec-127">See Also</span></span>  
 [<span data-ttu-id="890ec-128">Authenticode</span><span class="sxs-lookup"><span data-stu-id="890ec-128">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)  
 [<span data-ttu-id="890ec-129">GetHashFromHandle 方法</span><span class="sxs-lookup"><span data-stu-id="890ec-129">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)  
 [<span data-ttu-id="890ec-130">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="890ec-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
