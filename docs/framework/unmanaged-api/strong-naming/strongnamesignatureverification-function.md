---
title: StrongNameSignatureVerification 函式
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c398663b84637d2551b0d94bd59b9e0994721ba5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124757"
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="ef100-102">StrongNameSignatureVerification 函式</span><span class="sxs-lookup"><span data-stu-id="ef100-102">StrongNameSignatureVerification Function</span></span>
<span data-ttu-id="ef100-103">取得指出位於所指定路徑之組件資訊清單是否包含強式名稱簽章的值 (會根據指定的旗標驗證此值)。</span><span class="sxs-lookup"><span data-stu-id="ef100-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="ef100-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="ef100-104">This function has been deprecated.</span></span> <span data-ttu-id="ef100-105">使用[iclrstrongname:: Strongnamesignatureverification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="ef100-105">Use the [ICLRStrongName::StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef100-106">語法</span><span class="sxs-lookup"><span data-stu-id="ef100-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef100-107">參數</span><span class="sxs-lookup"><span data-stu-id="ef100-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="ef100-108">[in]可攜式可執行檔 （.dll 或.exe） 檔來確認組件路徑。</span><span class="sxs-lookup"><span data-stu-id="ef100-108">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="ef100-109">[in]若要修改的驗證行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="ef100-109">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="ef100-110">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="ef100-110">The following values are supported:</span></span>  
  
-   <span data-ttu-id="ef100-111">`SN_INFLAG_FORCE_VER` (0x00000001)-強制執行驗證，即使它是需要覆寫登錄設定。</span><span class="sxs-lookup"><span data-stu-id="ef100-111">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="ef100-112">`SN_INFLAG_INSTALL` (0x00000002)-指定驗證資訊清單的第一次。</span><span class="sxs-lookup"><span data-stu-id="ef100-112">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
-   <span data-ttu-id="ef100-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004)-指定快取可讓具有系統管理權限的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="ef100-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="ef100-114">`SN_INFLAG_USER_ACCESS` (0x00000008)-指定的組件都是僅供目前的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="ef100-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="ef100-115">`SN_INFLAG_ALL_ACCESS` (0x00000010)-指定快取會提供任何保證的存取限制。</span><span class="sxs-lookup"><span data-stu-id="ef100-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="ef100-116">`SN_INFLAG_RUNTIME` (0x80000000)-保留給內部偵錯。</span><span class="sxs-lookup"><span data-stu-id="ef100-116">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="ef100-117">[out]旗標，指出是否已驗證的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="ef100-117">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="ef100-118">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="ef100-118">The following value is supported:</span></span>  
  
-   <span data-ttu-id="ef100-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-此值設為`false`，指定驗證成功，因為登錄設定。</span><span class="sxs-lookup"><span data-stu-id="ef100-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef100-120">傳回值</span><span class="sxs-lookup"><span data-stu-id="ef100-120">Return Value</span></span>  
 <span data-ttu-id="ef100-121">`true` 如果驗證成功;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="ef100-121">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef100-122">需求</span><span class="sxs-lookup"><span data-stu-id="ef100-122">Requirements</span></span>  
 <span data-ttu-id="ef100-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ef100-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef100-124">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ef100-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ef100-125">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ef100-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ef100-126">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef100-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef100-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef100-127">See also</span></span>

- [<span data-ttu-id="ef100-128">StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="ef100-128">StrongNameSignatureVerification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="ef100-129">StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="ef100-129">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="ef100-130">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="ef100-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
