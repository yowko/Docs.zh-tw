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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c15b8e416a5070f59a4df44b3e670e2eb9316b5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630539"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="a7693-102">ICLRStrongName::StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="a7693-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>
<span data-ttu-id="a7693-103">取得值，指出是否提供之路徑上的組件資訊清單包含強式名稱簽章，根據指定的旗標加以確認。</span><span class="sxs-lookup"><span data-stu-id="a7693-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7693-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7693-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7693-105">參數</span><span class="sxs-lookup"><span data-stu-id="a7693-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="a7693-106">[in]可攜式可執行檔 （.dll 或.exe） 檔來確認組件路徑。</span><span class="sxs-lookup"><span data-stu-id="a7693-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="a7693-107">[in]若要修改的驗證行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="a7693-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="a7693-108">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="a7693-108">The following values are supported:</span></span>  
  
- <span data-ttu-id="a7693-109">`SN_INFLAG_FORCE_VER` (0x00000001)-強制執行驗證，即使它是需要覆寫登錄設定。</span><span class="sxs-lookup"><span data-stu-id="a7693-109">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="a7693-110">`SN_INFLAG_INSTALL` (0x00000002)-指定驗證資訊清單的第一次。</span><span class="sxs-lookup"><span data-stu-id="a7693-110">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="a7693-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004)-指定快取可讓具有系統管理權限的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="a7693-111">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="a7693-112">`SN_INFLAG_USER_ACCESS` (0x00000008)-指定的組件都是僅供目前的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="a7693-112">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="a7693-113">`SN_INFLAG_ALL_ACCESS` (0x00000010)-指定快取會提供任何保證的存取限制。</span><span class="sxs-lookup"><span data-stu-id="a7693-113">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="a7693-114">`SN_INFLAG_RUNTIME` (0x80000000)-保留給內部偵錯。</span><span class="sxs-lookup"><span data-stu-id="a7693-114">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="a7693-115">[out]旗標，指出是否已驗證的強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="a7693-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="a7693-116">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="a7693-116">The following value is supported:</span></span>  
  
- <span data-ttu-id="a7693-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-此值設為`false`，指定驗證成功，因為登錄設定。</span><span class="sxs-lookup"><span data-stu-id="a7693-117">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7693-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="a7693-118">Return Value</span></span>  
 <span data-ttu-id="a7693-119">`S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="a7693-119">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7693-120">需求</span><span class="sxs-lookup"><span data-stu-id="a7693-120">Requirements</span></span>  
 <span data-ttu-id="a7693-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7693-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7693-122">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a7693-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a7693-123">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a7693-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7693-124">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7693-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7693-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7693-125">See also</span></span>

- [<span data-ttu-id="a7693-126">StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="a7693-126">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="a7693-127">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="a7693-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
