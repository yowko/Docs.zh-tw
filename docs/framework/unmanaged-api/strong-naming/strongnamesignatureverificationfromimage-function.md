---
title: StrongNameSignatureVerificationFromImage 函式
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
ms.openlocfilehash: b90cc6fe99cf592f1b3fd117888462a957e4ce35
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708422"
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="353e5-102">StrongNameSignatureVerificationFromImage 函式</span><span class="sxs-lookup"><span data-stu-id="353e5-102">StrongNameSignatureVerificationFromImage Function</span></span>

<span data-ttu-id="353e5-103">驗證已對應到記憶體的組件對關聯的公開金鑰而言有效。</span><span class="sxs-lookup"><span data-stu-id="353e5-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="353e5-104">此函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="353e5-104">This function has been deprecated.</span></span> <span data-ttu-id="353e5-105">請改用 [ICLRStrongName：： StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="353e5-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="353e5-106">語法</span><span class="sxs-lookup"><span data-stu-id="353e5-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="353e5-107">參數</span><span class="sxs-lookup"><span data-stu-id="353e5-107">Parameters</span></span>  

 `pbBase`  
 <span data-ttu-id="353e5-108">在對應的組件資訊清單的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="353e5-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="353e5-109">在對應影像的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="353e5-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="353e5-110">在影響驗證行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="353e5-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="353e5-111">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="353e5-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="353e5-112">`SN_INFLAG_FORCE_VER` (0x00000001) -即使必須覆寫登錄設定，仍會強制執行驗證。</span><span class="sxs-lookup"><span data-stu-id="353e5-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="353e5-113">`SN_INFLAG_INSTALL` (0x00000002) -指定這是在此映射上執行的第一次驗證。</span><span class="sxs-lookup"><span data-stu-id="353e5-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="353e5-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) -指定快取只允許具有系統管理許可權的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="353e5-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="353e5-115">`SN_INFLAG_USER_ACCESS` (0x00000008) -指定只有目前使用者才能存取元件。</span><span class="sxs-lookup"><span data-stu-id="353e5-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="353e5-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) -指定快取不會提供存取限制的保證。</span><span class="sxs-lookup"><span data-stu-id="353e5-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="353e5-117">`SN_INFLAG_RUNTIME` (0x80000000) -保留供內部偵錯工具之用。</span><span class="sxs-lookup"><span data-stu-id="353e5-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="353e5-118">擴展額外輸出資訊的旗標。</span><span class="sxs-lookup"><span data-stu-id="353e5-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="353e5-119">以下是支援的值：</span><span class="sxs-lookup"><span data-stu-id="353e5-119">The following value is supported:</span></span>  
  
- <span data-ttu-id="353e5-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) -此值設定為， `false` 以指定驗證成功，因為登錄設定。</span><span class="sxs-lookup"><span data-stu-id="353e5-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="353e5-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="353e5-121">Return Value</span></span>  

 <span data-ttu-id="353e5-122">`true` 成功完成時;否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="353e5-122">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="353e5-123">備註</span><span class="sxs-lookup"><span data-stu-id="353e5-123">Remarks</span></span>  

 <span data-ttu-id="353e5-124">如果函式 `StrongNameSignatureVerificationFromImage` 未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式來取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="353e5-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="353e5-125">需求</span><span class="sxs-lookup"><span data-stu-id="353e5-125">Requirements</span></span>  

 <span data-ttu-id="353e5-126">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="353e5-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="353e5-127">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="353e5-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="353e5-128">連結 **庫：** 以資源的形式包含在 mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="353e5-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="353e5-129">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="353e5-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="353e5-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="353e5-130">See also</span></span>

- [<span data-ttu-id="353e5-131">StrongNameSignatureVerificationFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="353e5-131">StrongNameSignatureVerificationFromImage Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [<span data-ttu-id="353e5-132">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="353e5-132">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
