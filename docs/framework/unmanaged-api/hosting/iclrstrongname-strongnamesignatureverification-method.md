---
title: ICLRStrongName::StrongNameSignatureVerification 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
ms.openlocfilehash: 2d53eebcc272ab87a2af5b3c081ca37dde5c74b9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674463"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="4fede-102">ICLRStrongName::StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="4fede-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>

<span data-ttu-id="4fede-103">取得值，這個值會指出所提供路徑的組件資訊清單是否包含強式名稱簽章，並根據指定的旗標進行驗證。</span><span class="sxs-lookup"><span data-stu-id="4fede-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fede-104">語法</span><span class="sxs-lookup"><span data-stu-id="4fede-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fede-105">參數</span><span class="sxs-lookup"><span data-stu-id="4fede-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="4fede-106">在可攜式可執行檔的路徑 ( .dll 或 .exe) 檔，以供元件進行驗證。</span><span class="sxs-lookup"><span data-stu-id="4fede-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="4fede-107">在用以修改驗證行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="4fede-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="4fede-108">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="4fede-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="4fede-109">`SN_INFLAG_FORCE_VER` (0x00000001) -即使必須覆寫登錄設定，仍會強制執行驗證。</span><span class="sxs-lookup"><span data-stu-id="4fede-109">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="4fede-110">`SN_INFLAG_INSTALL` (0x00000002) -指定這是資訊清單的第一次驗證。</span><span class="sxs-lookup"><span data-stu-id="4fede-110">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="4fede-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) -指定快取只允許具有系統管理許可權的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="4fede-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="4fede-112">`SN_INFLAG_USER_ACCESS` (0x00000008) -指定只有目前使用者才能存取元件。</span><span class="sxs-lookup"><span data-stu-id="4fede-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="4fede-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) -指定快取不會提供存取限制的保證。</span><span class="sxs-lookup"><span data-stu-id="4fede-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="4fede-114">`SN_INFLAG_RUNTIME` (0x80000000) -保留供內部偵錯工具之用。</span><span class="sxs-lookup"><span data-stu-id="4fede-114">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="4fede-115">擴展旗標，指出是否已驗證強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="4fede-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="4fede-116">以下是支援的值：</span><span class="sxs-lookup"><span data-stu-id="4fede-116">The following value is supported:</span></span>  
  
- <span data-ttu-id="4fede-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) -此值設定為， `false` 以指定驗證成功，因為登錄設定。</span><span class="sxs-lookup"><span data-stu-id="4fede-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4fede-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="4fede-118">Return Value</span></span>  

 <span data-ttu-id="4fede-119">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="4fede-119">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fede-120">需求</span><span class="sxs-lookup"><span data-stu-id="4fede-120">Requirements</span></span>  

 <span data-ttu-id="4fede-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4fede-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fede-122">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="4fede-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4fede-123">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="4fede-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4fede-124">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fede-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fede-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fede-125">See also</span></span>

- [<span data-ttu-id="4fede-126">StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="4fede-126">StrongNameSignatureVerificationEx Method</span></span>](iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="4fede-127">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="4fede-127">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
