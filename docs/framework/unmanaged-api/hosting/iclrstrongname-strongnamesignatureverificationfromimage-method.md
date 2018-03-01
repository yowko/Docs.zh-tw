---
title: "ICLRStrongName::StrongNameSignatureVerificationFromImage 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 57c8422d59a07de9ad045f2043594cb8d01f2f74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="11e63-102">ICLRStrongName::StrongNameSignatureVerificationFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="11e63-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="11e63-103">請確認已對應到記憶體的組件適用於相關聯的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="11e63-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11e63-104">語法</span><span class="sxs-lookup"><span data-stu-id="11e63-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11e63-105">參數</span><span class="sxs-lookup"><span data-stu-id="11e63-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="11e63-106">[in]對應的組件資訊清單的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="11e63-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="11e63-107">[in]以位元組為單位的對應影像大小。</span><span class="sxs-lookup"><span data-stu-id="11e63-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="11e63-108">[in]影響驗證行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="11e63-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="11e63-109">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="11e63-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="11e63-110">`SN_INFLAG_FORCE_VER`(0x00000001)-強制執行驗證，即使它是需要覆寫登錄設定。</span><span class="sxs-lookup"><span data-stu-id="11e63-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="11e63-111">`SN_INFLAG_INSTALL`(0x00000002)-指定此映像上執行的第一個驗證。</span><span class="sxs-lookup"><span data-stu-id="11e63-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   <span data-ttu-id="11e63-112">`SN_INFLAG_ADMIN_ACCESS`(0x00000004)-指定快取可讓擁有系統管理權限的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="11e63-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="11e63-113">`SN_INFLAG_USER_ACCESS`(0x00000008)-指定的組件都是只能由目前的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="11e63-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="11e63-114">`SN_INFLAG_ALL_ACCESS`(0x00000010)-指定快取會提供任何保證的存取限制。</span><span class="sxs-lookup"><span data-stu-id="11e63-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="11e63-115">`SN_INFLAG_RUNTIME`(0x80000000)-保留供內部偵錯。</span><span class="sxs-lookup"><span data-stu-id="11e63-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="11e63-116">[out]其他輸出資訊的旗標。</span><span class="sxs-lookup"><span data-stu-id="11e63-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="11e63-117">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="11e63-117">The following value is supported:</span></span>  
  
-   <span data-ttu-id="11e63-118">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001)-此值設為`false`來指定驗證成功登錄設定所造成。</span><span class="sxs-lookup"><span data-stu-id="11e63-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11e63-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="11e63-119">Return Value</span></span>  
 <span data-ttu-id="11e63-120">`S_OK`如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="11e63-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11e63-121">需求</span><span class="sxs-lookup"><span data-stu-id="11e63-121">Requirements</span></span>  
 <span data-ttu-id="11e63-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11e63-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11e63-123">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="11e63-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="11e63-124">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="11e63-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11e63-125">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11e63-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e63-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="11e63-126">See Also</span></span>  
 [<span data-ttu-id="11e63-127">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="11e63-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
