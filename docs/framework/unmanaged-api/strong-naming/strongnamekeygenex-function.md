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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9ab908866402bd7a883114466f32921321a5ee6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799007"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="1ea58-102">StrongNameKeyGenEx 函式</span><span class="sxs-lookup"><span data-stu-id="1ea58-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="1ea58-103">產生具有指定金鑰大小的新公開/私密金鑰組，以供強式名稱使用。</span><span class="sxs-lookup"><span data-stu-id="1ea58-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="1ea58-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="1ea58-104">This function has been deprecated.</span></span> <span data-ttu-id="1ea58-105">請改用[ICLRStrongName：： StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="1ea58-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ea58-106">語法</span><span class="sxs-lookup"><span data-stu-id="1ea58-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ea58-107">參數</span><span class="sxs-lookup"><span data-stu-id="1ea58-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="1ea58-108">在要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="1ea58-108">[in] The requested key container name.</span></span> <span data-ttu-id="1ea58-109">`wszKeyContainer`必須是非空白字串，否則為 null，以產生暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="1ea58-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1ea58-110">在指定是否要保留註冊的金鑰。</span><span class="sxs-lookup"><span data-stu-id="1ea58-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="1ea58-111">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="1ea58-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="1ea58-112">0x00000000-在為`wszKeyContainer` null 時使用，以產生暫存金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="1ea58-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="1ea58-113">0x00000001 （`SN_LEAVE_KEY`）-指定應將金鑰保留為已註冊。</span><span class="sxs-lookup"><span data-stu-id="1ea58-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="1ea58-114">在要求的金鑰大小（以位為單位）。</span><span class="sxs-lookup"><span data-stu-id="1ea58-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="1ea58-115">脫銷傳回的公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="1ea58-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="1ea58-116">脫銷的大小（以位元組為單位`ppbKeyBlob`）。</span><span class="sxs-lookup"><span data-stu-id="1ea58-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ea58-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="1ea58-117">Return Value</span></span>  
 <span data-ttu-id="1ea58-118">`true`成功完成時;否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="1ea58-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ea58-119">備註</span><span class="sxs-lookup"><span data-stu-id="1ea58-119">Remarks</span></span>  
 <span data-ttu-id="1ea58-120">.NET Framework 版本1.0 和1.1 需要`dwKeySize` 1024 位以強式名稱簽署元件; 版本2.0 新增了支援的2048位金鑰。</span><span class="sxs-lookup"><span data-stu-id="1ea58-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="1ea58-121">在取得金鑰之後，您應該呼叫[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函式以釋放已配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="1ea58-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="1ea58-122">如果函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。`StrongNameKeyGenEx`</span><span class="sxs-lookup"><span data-stu-id="1ea58-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ea58-123">需求</span><span class="sxs-lookup"><span data-stu-id="1ea58-123">Requirements</span></span>  
 <span data-ttu-id="1ea58-124">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea58-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ea58-125">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="1ea58-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="1ea58-126">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1ea58-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ea58-127">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ea58-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea58-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ea58-128">See also</span></span>

- [<span data-ttu-id="1ea58-129">StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="1ea58-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="1ea58-130">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="1ea58-130">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="1ea58-131">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="1ea58-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
