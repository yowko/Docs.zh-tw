---
title: StrongNameKeyGenEx 函式
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
ms.openlocfilehash: 63ddd90f3a8090853d10f03052915d10e1503ea6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125207"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="1ca3b-102">StrongNameKeyGenEx 函式</span><span class="sxs-lookup"><span data-stu-id="1ca3b-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="1ca3b-103">產生具有指定金鑰大小的新公開/私密金鑰組，以供強式名稱使用。</span><span class="sxs-lookup"><span data-stu-id="1ca3b-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="1ca3b-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="1ca3b-104">This function has been deprecated.</span></span> <span data-ttu-id="1ca3b-105">請改用[ICLRStrongName：： StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="1ca3b-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ca3b-106">語法</span><span class="sxs-lookup"><span data-stu-id="1ca3b-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ca3b-107">參數</span><span class="sxs-lookup"><span data-stu-id="1ca3b-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="1ca3b-108">在要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="1ca3b-108">[in] The requested key container name.</span></span> <span data-ttu-id="1ca3b-109">`wszKeyContainer` 必須是非空白字串，或為 null 以產生暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="1ca3b-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1ca3b-110">在指定是否要保留註冊的金鑰。</span><span class="sxs-lookup"><span data-stu-id="1ca3b-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="1ca3b-111">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="1ca3b-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="1ca3b-112">0x00000000-在 `wszKeyContainer` 為 null 時用來產生暫存金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="1ca3b-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="1ca3b-113">0x00000001 （`SN_LEAVE_KEY`）-指定應將金鑰保留為已註冊。</span><span class="sxs-lookup"><span data-stu-id="1ca3b-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="1ca3b-114">在要求的金鑰大小（以位為單位）。</span><span class="sxs-lookup"><span data-stu-id="1ca3b-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="1ca3b-115">脫銷傳回的公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="1ca3b-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="1ca3b-116">脫銷`ppbKeyBlob`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="1ca3b-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ca3b-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="1ca3b-117">Return Value</span></span>  
 <span data-ttu-id="1ca3b-118">成功完成時 `true`;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="1ca3b-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ca3b-119">備註</span><span class="sxs-lookup"><span data-stu-id="1ca3b-119">Remarks</span></span>  
 <span data-ttu-id="1ca3b-120">.NET Framework 版本1.0 和1.1 需要1024位的 `dwKeySize`，才能以強式名稱簽署元件;2.0 版新增了2048位金鑰的支援。</span><span class="sxs-lookup"><span data-stu-id="1ca3b-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="1ca3b-121">在取得金鑰之後，您應該呼叫[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函式以釋放已配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="1ca3b-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="1ca3b-122">如果 `StrongNameKeyGenEx` 函式未順利完成，請呼叫[StrongNameErrorInfo](strongnameerrorinfo-function.md)函式，以取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1ca3b-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ca3b-123">需求</span><span class="sxs-lookup"><span data-stu-id="1ca3b-123">Requirements</span></span>  
 <span data-ttu-id="1ca3b-124">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ca3b-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ca3b-125">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="1ca3b-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="1ca3b-126">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1ca3b-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ca3b-127">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ca3b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca3b-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="1ca3b-128">See also</span></span>

- [<span data-ttu-id="1ca3b-129">StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="1ca3b-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="1ca3b-130">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="1ca3b-130">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="1ca3b-131">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="1ca3b-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
