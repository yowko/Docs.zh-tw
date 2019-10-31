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
ms.openlocfilehash: 7dd61be008ba08ca2b28ae3e7e8ff6326f8a41d9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129238"
---
# <a name="strongnamesignatureverification-function"></a><span data-ttu-id="b6ffd-102">StrongNameSignatureVerification 函式</span><span class="sxs-lookup"><span data-stu-id="b6ffd-102">StrongNameSignatureVerification Function</span></span>
<span data-ttu-id="b6ffd-103">取得指出位於所指定路徑之組件資訊清單是否包含強式名稱簽章的值 (會根據指定的旗標驗證此值)。</span><span class="sxs-lookup"><span data-stu-id="b6ffd-103">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
 <span data-ttu-id="b6ffd-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="b6ffd-104">This function has been deprecated.</span></span> <span data-ttu-id="b6ffd-105">請改用[ICLRStrongName：： StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b6ffd-105">Use the [ICLRStrongName::StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ffd-106">語法</span><span class="sxs-lookup"><span data-stu-id="b6ffd-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6ffd-107">參數</span><span class="sxs-lookup"><span data-stu-id="b6ffd-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b6ffd-108">在要驗證之元件的可攜式可執行檔（.dll 或 .exe）的路徑。</span><span class="sxs-lookup"><span data-stu-id="b6ffd-108">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="b6ffd-109">在用來修改驗證行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="b6ffd-109">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="b6ffd-110">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="b6ffd-110">The following values are supported:</span></span>  
  
- <span data-ttu-id="b6ffd-111">`SN_INFLAG_FORCE_VER` （0x00000001）-即使需要覆寫登錄設定，也會強制執行驗證。</span><span class="sxs-lookup"><span data-stu-id="b6ffd-111">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="b6ffd-112">`SN_INFLAG_INSTALL` （0x00000002）-指定這是第一次驗證資訊清單。</span><span class="sxs-lookup"><span data-stu-id="b6ffd-112">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
- <span data-ttu-id="b6ffd-113">`SN_INFLAG_ADMIN_ACCESS` （0x00000004）-指定快取只允許具有系統管理許可權的使用者進行存取。</span><span class="sxs-lookup"><span data-stu-id="b6ffd-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="b6ffd-114">`SN_INFLAG_USER_ACCESS` （0x00000008）-指定只有目前使用者可以存取元件。</span><span class="sxs-lookup"><span data-stu-id="b6ffd-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="b6ffd-115">`SN_INFLAG_ALL_ACCESS` （0x00000010）-指定快取不會提供存取限制的保證。</span><span class="sxs-lookup"><span data-stu-id="b6ffd-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="b6ffd-116">`SN_INFLAG_RUNTIME` （0x80000000）-保留供內部偵錯工具之用。</span><span class="sxs-lookup"><span data-stu-id="b6ffd-116">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="b6ffd-117">脫銷旗標，指出是否已驗證強式名稱簽章。</span><span class="sxs-lookup"><span data-stu-id="b6ffd-117">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="b6ffd-118">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="b6ffd-118">The following value is supported:</span></span>  
  
- <span data-ttu-id="b6ffd-119">`SN_OUTFLAG_WAS_VERIFIED` （0x00000001）-此值設定為 `false`，指定驗證是因為登錄設定而成功。</span><span class="sxs-lookup"><span data-stu-id="b6ffd-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6ffd-120">傳回值</span><span class="sxs-lookup"><span data-stu-id="b6ffd-120">Return Value</span></span>  
 <span data-ttu-id="b6ffd-121">如果驗證成功，則 `true`;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="b6ffd-121">`true` if the verification was successful; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6ffd-122">需求</span><span class="sxs-lookup"><span data-stu-id="b6ffd-122">Requirements</span></span>  
 <span data-ttu-id="b6ffd-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6ffd-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6ffd-124">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="b6ffd-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b6ffd-125">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b6ffd-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6ffd-126">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6ffd-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ffd-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="b6ffd-127">See also</span></span>

- [<span data-ttu-id="b6ffd-128">StrongNameSignatureVerification 方法</span><span class="sxs-lookup"><span data-stu-id="b6ffd-128">StrongNameSignatureVerification Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="b6ffd-129">StrongNameSignatureVerificationEx 方法</span><span class="sxs-lookup"><span data-stu-id="b6ffd-129">StrongNameSignatureVerificationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="b6ffd-130">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="b6ffd-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
