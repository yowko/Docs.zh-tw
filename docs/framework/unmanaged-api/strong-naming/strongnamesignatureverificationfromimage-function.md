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
ms.openlocfilehash: 5c12ca20deee06fcaca68365644fd9dff95379ff
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121138"
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="660a8-102">StrongNameSignatureVerificationFromImage 函式</span><span class="sxs-lookup"><span data-stu-id="660a8-102">StrongNameSignatureVerificationFromImage Function</span></span>
<span data-ttu-id="660a8-103">驗證已對應到記憶體的組件對關聯的公開金鑰而言有效。</span><span class="sxs-lookup"><span data-stu-id="660a8-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="660a8-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="660a8-104">This function has been deprecated.</span></span> <span data-ttu-id="660a8-105">請改用[ICLRStrongName：： StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="660a8-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="660a8-106">語法</span><span class="sxs-lookup"><span data-stu-id="660a8-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="660a8-107">參數</span><span class="sxs-lookup"><span data-stu-id="660a8-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="660a8-108">在對應之組件資訊清單的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="660a8-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="660a8-109">在對應影像的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="660a8-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="660a8-110">在會影響驗證行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="660a8-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="660a8-111">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="660a8-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="660a8-112">`SN_INFLAG_FORCE_VER` （0x00000001）-即使需要覆寫登錄設定，也會強制執行驗證。</span><span class="sxs-lookup"><span data-stu-id="660a8-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="660a8-113">`SN_INFLAG_INSTALL` （0x00000002）-指定這是在此影像上執行的第一次驗證。</span><span class="sxs-lookup"><span data-stu-id="660a8-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="660a8-114">`SN_INFLAG_ADMIN_ACCESS` （0x00000004）-指定快取只允許具有系統管理許可權的使用者進行存取。</span><span class="sxs-lookup"><span data-stu-id="660a8-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="660a8-115">`SN_INFLAG_USER_ACCESS` （0x00000008）-指定只有目前使用者可以存取元件。</span><span class="sxs-lookup"><span data-stu-id="660a8-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="660a8-116">`SN_INFLAG_ALL_ACCESS` （0x00000010）-指定快取不會提供存取限制的保證。</span><span class="sxs-lookup"><span data-stu-id="660a8-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="660a8-117">`SN_INFLAG_RUNTIME` （0x80000000）-保留供內部偵錯工具之用。</span><span class="sxs-lookup"><span data-stu-id="660a8-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="660a8-118">脫銷其他輸出資訊的旗標。</span><span class="sxs-lookup"><span data-stu-id="660a8-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="660a8-119">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="660a8-119">The following value is supported:</span></span>  
  
- <span data-ttu-id="660a8-120">`SN_OUTFLAG_WAS_VERIFIED` （0x00000001）-此值設定為 `false`，指定驗證是因為登錄設定而成功。</span><span class="sxs-lookup"><span data-stu-id="660a8-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="660a8-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="660a8-121">Return Value</span></span>  
 <span data-ttu-id="660a8-122">成功完成時 `true`;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="660a8-122">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="660a8-123">備註</span><span class="sxs-lookup"><span data-stu-id="660a8-123">Remarks</span></span>  
 <span data-ttu-id="660a8-124">如果 `StrongNameSignatureVerificationFromImage` 函式未順利完成，請呼叫[StrongNameErrorInfo](strongnameerrorinfo-function.md)函式，以取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="660a8-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="660a8-125">需求</span><span class="sxs-lookup"><span data-stu-id="660a8-125">Requirements</span></span>  
 <span data-ttu-id="660a8-126">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="660a8-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="660a8-127">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="660a8-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="660a8-128">連結**庫：** 包含為 mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="660a8-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="660a8-129">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="660a8-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="660a8-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="660a8-130">See also</span></span>

- [<span data-ttu-id="660a8-131">StrongNameSignatureVerificationFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="660a8-131">StrongNameSignatureVerificationFromImage Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [<span data-ttu-id="660a8-132">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="660a8-132">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
