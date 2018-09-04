---
title: ICLRStrongName::StrongNameSignatureVerificationFromImage 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdbf2126d3da152ce68b6dbb47f5772e3b13d2c6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43660303"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="c4dad-102">ICLRStrongName::StrongNameSignatureVerificationFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="c4dad-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="c4dad-103">驗證已對應到記憶體的組件對關聯的公開金鑰而言有效。</span><span class="sxs-lookup"><span data-stu-id="c4dad-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4dad-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4dad-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4dad-105">參數</span><span class="sxs-lookup"><span data-stu-id="c4dad-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="c4dad-106">[in]對應的組件資訊清單的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="c4dad-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="c4dad-107">[in]以位元組為單位，對應的映像的大小。</span><span class="sxs-lookup"><span data-stu-id="c4dad-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="c4dad-108">[in]影響驗證行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="c4dad-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="c4dad-109">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="c4dad-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="c4dad-110">`SN_INFLAG_FORCE_VER` (0x00000001)-強制執行驗證，即使它是需要覆寫登錄設定。</span><span class="sxs-lookup"><span data-stu-id="c4dad-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="c4dad-111">`SN_INFLAG_INSTALL` (0x00000002)-指定此映像上執行的第一次驗證。</span><span class="sxs-lookup"><span data-stu-id="c4dad-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   <span data-ttu-id="c4dad-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004)-指定快取可讓具有系統管理權限的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="c4dad-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="c4dad-113">`SN_INFLAG_USER_ACCESS` (0x00000008)-指定的組件都是僅供目前的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="c4dad-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="c4dad-114">`SN_INFLAG_ALL_ACCESS` (0x00000010)-指定快取會提供任何保證的存取限制。</span><span class="sxs-lookup"><span data-stu-id="c4dad-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="c4dad-115">`SN_INFLAG_RUNTIME` (0x80000000)-保留給內部偵錯。</span><span class="sxs-lookup"><span data-stu-id="c4dad-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="c4dad-116">[out]其他輸出資訊之旗標。</span><span class="sxs-lookup"><span data-stu-id="c4dad-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="c4dad-117">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="c4dad-117">The following value is supported:</span></span>  
  
-   <span data-ttu-id="c4dad-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-此值設為`false`，指定驗證成功，因為登錄設定。</span><span class="sxs-lookup"><span data-stu-id="c4dad-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4dad-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="c4dad-119">Return Value</span></span>  
 <span data-ttu-id="c4dad-120">`S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="c4dad-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4dad-121">需求</span><span class="sxs-lookup"><span data-stu-id="c4dad-121">Requirements</span></span>  
 <span data-ttu-id="c4dad-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4dad-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4dad-123">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c4dad-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c4dad-124">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c4dad-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4dad-125">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4dad-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4dad-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4dad-126">See Also</span></span>  
 [<span data-ttu-id="c4dad-127">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="c4dad-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
