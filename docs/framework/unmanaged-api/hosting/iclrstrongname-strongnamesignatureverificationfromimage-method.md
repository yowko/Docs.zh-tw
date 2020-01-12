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
ms.openlocfilehash: 1bfc41fdad35a7e0560d251179ea035c96aecab7
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899524"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="16e90-102">ICLRStrongName::StrongNameSignatureVerificationFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="16e90-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="16e90-103">驗證已對應到記憶體的組件對關聯的公開金鑰而言有效。</span><span class="sxs-lookup"><span data-stu-id="16e90-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16e90-104">語法</span><span class="sxs-lookup"><span data-stu-id="16e90-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16e90-105">參數</span><span class="sxs-lookup"><span data-stu-id="16e90-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="16e90-106">在對應之組件資訊清單的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="16e90-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="16e90-107">在對應影像的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="16e90-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="16e90-108">在會影響驗證行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="16e90-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="16e90-109">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="16e90-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="16e90-110">`SN_INFLAG_FORCE_VER` （0x00000001）-即使需要覆寫登錄設定，也會強制執行驗證。</span><span class="sxs-lookup"><span data-stu-id="16e90-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="16e90-111">`SN_INFLAG_INSTALL` （0x00000002）-指定這是在此影像上執行的第一次驗證。</span><span class="sxs-lookup"><span data-stu-id="16e90-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="16e90-112">`SN_INFLAG_ADMIN_ACCESS` （0x00000004）-指定快取只允許具有系統管理許可權的使用者進行存取。</span><span class="sxs-lookup"><span data-stu-id="16e90-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="16e90-113">`SN_INFLAG_USER_ACCESS` （0x00000008）-指定只有目前使用者可以存取元件。</span><span class="sxs-lookup"><span data-stu-id="16e90-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="16e90-114">`SN_INFLAG_ALL_ACCESS` （0x00000010）-指定快取不會提供存取限制的保證。</span><span class="sxs-lookup"><span data-stu-id="16e90-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="16e90-115">`SN_INFLAG_RUNTIME` （0x80000000）-保留供內部偵錯工具之用。</span><span class="sxs-lookup"><span data-stu-id="16e90-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="16e90-116">脫銷其他輸出資訊的旗標。</span><span class="sxs-lookup"><span data-stu-id="16e90-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="16e90-117">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="16e90-117">The following value is supported:</span></span>  
  
- <span data-ttu-id="16e90-118">`SN_OUTFLAG_WAS_VERIFIED` （0x00000001）-此值設定為 `false`，指定驗證是因為登錄設定而成功。</span><span class="sxs-lookup"><span data-stu-id="16e90-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16e90-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="16e90-119">Return Value</span></span>  
 <span data-ttu-id="16e90-120">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="16e90-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16e90-121">需求</span><span class="sxs-lookup"><span data-stu-id="16e90-121">Requirements</span></span>  
 <span data-ttu-id="16e90-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="16e90-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16e90-123">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="16e90-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="16e90-124">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="16e90-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16e90-125">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16e90-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16e90-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="16e90-126">See also</span></span>

- [<span data-ttu-id="16e90-127">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="16e90-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
