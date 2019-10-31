---
title: StrongNameKeyGen 函式
ms.date: 03/30/2017
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
ms.openlocfilehash: 79b2235e3645c89c2cd9ebcce079d5eb7efdd162
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128744"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="e88fb-102">StrongNameKeyGen 函式</span><span class="sxs-lookup"><span data-stu-id="e88fb-102">StrongNameKeyGen Function</span></span>
<span data-ttu-id="e88fb-103">建立將供強式名稱使用的新公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="e88fb-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="e88fb-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="e88fb-104">This function has been deprecated.</span></span> <span data-ttu-id="e88fb-105">請改用[ICLRStrongName：： StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="e88fb-105">Use the [ICLRStrongName::StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e88fb-106">語法</span><span class="sxs-lookup"><span data-stu-id="e88fb-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e88fb-107">參數</span><span class="sxs-lookup"><span data-stu-id="e88fb-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="e88fb-108">在要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="e88fb-108">[in] The requested key container name.</span></span> <span data-ttu-id="e88fb-109">`wszKeyContainer` 必須是非空白字串，或為 null 以產生暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="e88fb-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e88fb-110">在指定是否要保留註冊的金鑰。</span><span class="sxs-lookup"><span data-stu-id="e88fb-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="e88fb-111">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="e88fb-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="e88fb-112">0x00000000-在 `wszKeyContainer` 為 null 時用來產生暫存金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="e88fb-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="e88fb-113">0x00000001 （`SN_LEAVE_KEY`）-指定應將金鑰保留為已註冊。</span><span class="sxs-lookup"><span data-stu-id="e88fb-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="e88fb-114">脫銷傳回的公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="e88fb-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="e88fb-115">脫銷`ppbKeyBlob`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="e88fb-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e88fb-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="e88fb-116">Return Value</span></span>  
 <span data-ttu-id="e88fb-117">成功完成時 `true`;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="e88fb-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e88fb-118">備註</span><span class="sxs-lookup"><span data-stu-id="e88fb-118">Remarks</span></span>  
 <span data-ttu-id="e88fb-119">`StrongNameKeyGen` 函式會建立1024位金鑰。</span><span class="sxs-lookup"><span data-stu-id="e88fb-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="e88fb-120">在取得金鑰之後，您應該呼叫[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函式以釋放已配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="e88fb-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="e88fb-121">如果 `StrongNameKeyGen` 函式未順利完成，請呼叫[StrongNameErrorInfo](strongnameerrorinfo-function.md)函式，以取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="e88fb-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e88fb-122">需求</span><span class="sxs-lookup"><span data-stu-id="e88fb-122">Requirements</span></span>  
 <span data-ttu-id="e88fb-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e88fb-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e88fb-124">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="e88fb-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e88fb-125">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e88fb-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e88fb-126">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e88fb-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e88fb-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="e88fb-127">See also</span></span>

- [<span data-ttu-id="e88fb-128">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="e88fb-128">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="e88fb-129">StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="e88fb-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="e88fb-130">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="e88fb-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
