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
ms.openlocfilehash: 21aeceff72ea6222992cb6f3d055ed6f71cda9bf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759250"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="8d157-102">ICLRStrongName::StrongNameSignatureVerificationFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="8d157-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="8d157-103">驗證已對應到記憶體的組件對關聯的公開金鑰而言有效。</span><span class="sxs-lookup"><span data-stu-id="8d157-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d157-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d157-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d157-105">參數</span><span class="sxs-lookup"><span data-stu-id="8d157-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="8d157-106">[in]對應的組件資訊清單的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="8d157-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="8d157-107">[in]以位元組為單位，對應的映像的大小。</span><span class="sxs-lookup"><span data-stu-id="8d157-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="8d157-108">[in]影響驗證行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="8d157-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="8d157-109">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="8d157-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="8d157-110">`SN_INFLAG_FORCE_VER` (0x00000001)-強制執行驗證，即使它是需要覆寫登錄設定。</span><span class="sxs-lookup"><span data-stu-id="8d157-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="8d157-111">`SN_INFLAG_INSTALL` (0x00000002)-指定此映像上執行的第一次驗證。</span><span class="sxs-lookup"><span data-stu-id="8d157-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="8d157-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004)-指定快取可讓具有系統管理權限的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="8d157-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="8d157-113">`SN_INFLAG_USER_ACCESS` (0x00000008)-指定的組件都是僅供目前的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="8d157-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="8d157-114">`SN_INFLAG_ALL_ACCESS` (0x00000010)-指定快取會提供任何保證的存取限制。</span><span class="sxs-lookup"><span data-stu-id="8d157-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="8d157-115">`SN_INFLAG_RUNTIME` (0x80000000)-保留給內部偵錯。</span><span class="sxs-lookup"><span data-stu-id="8d157-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="8d157-116">[out]其他輸出資訊之旗標。</span><span class="sxs-lookup"><span data-stu-id="8d157-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="8d157-117">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="8d157-117">The following value is supported:</span></span>  
  
- <span data-ttu-id="8d157-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-此值設為`false`，指定驗證成功，因為登錄設定。</span><span class="sxs-lookup"><span data-stu-id="8d157-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d157-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="8d157-119">Return Value</span></span>  
 <span data-ttu-id="8d157-120">`S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="8d157-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d157-121">需求</span><span class="sxs-lookup"><span data-stu-id="8d157-121">Requirements</span></span>  
 <span data-ttu-id="8d157-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d157-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d157-123">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8d157-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8d157-124">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8d157-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d157-125">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d157-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d157-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d157-126">See also</span></span>

- [<span data-ttu-id="8d157-127">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="8d157-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
