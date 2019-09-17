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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f062f47790136e8cd39c6751b7c75eef660c2b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799146"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="a66e7-102">StrongNameKeyGen 函式</span><span class="sxs-lookup"><span data-stu-id="a66e7-102">StrongNameKeyGen Function</span></span>
<span data-ttu-id="a66e7-103">建立將供強式名稱使用的新公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="a66e7-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="a66e7-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="a66e7-104">This function has been deprecated.</span></span> <span data-ttu-id="a66e7-105">請改用[ICLRStrongName：： StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a66e7-105">Use the [ICLRStrongName::StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a66e7-106">語法</span><span class="sxs-lookup"><span data-stu-id="a66e7-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a66e7-107">參數</span><span class="sxs-lookup"><span data-stu-id="a66e7-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="a66e7-108">在要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="a66e7-108">[in] The requested key container name.</span></span> <span data-ttu-id="a66e7-109">`wszKeyContainer`必須是非空白字串，否則為 null，以產生暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="a66e7-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a66e7-110">在指定是否要保留註冊的金鑰。</span><span class="sxs-lookup"><span data-stu-id="a66e7-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="a66e7-111">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="a66e7-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="a66e7-112">0x00000000-在為`wszKeyContainer` null 時使用，以產生暫存金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="a66e7-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="a66e7-113">0x00000001 （`SN_LEAVE_KEY`）-指定應將金鑰保留為已註冊。</span><span class="sxs-lookup"><span data-stu-id="a66e7-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="a66e7-114">脫銷傳回的公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="a66e7-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="a66e7-115">脫銷的大小（以位元組為單位`ppbKeyBlob`）。</span><span class="sxs-lookup"><span data-stu-id="a66e7-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a66e7-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="a66e7-116">Return Value</span></span>  
 <span data-ttu-id="a66e7-117">`true`成功完成時;否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="a66e7-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a66e7-118">備註</span><span class="sxs-lookup"><span data-stu-id="a66e7-118">Remarks</span></span>  
 <span data-ttu-id="a66e7-119">`StrongNameKeyGen`函式會建立1024位金鑰。</span><span class="sxs-lookup"><span data-stu-id="a66e7-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="a66e7-120">在取得金鑰之後，您應該呼叫[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函式以釋放已配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="a66e7-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="a66e7-121">如果 `StrongNameKeyGen` 函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="a66e7-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a66e7-122">需求</span><span class="sxs-lookup"><span data-stu-id="a66e7-122">Requirements</span></span>  
 <span data-ttu-id="a66e7-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a66e7-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a66e7-124">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="a66e7-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a66e7-125">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a66e7-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a66e7-126">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a66e7-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a66e7-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a66e7-127">See also</span></span>

- [<span data-ttu-id="a66e7-128">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="a66e7-128">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="a66e7-129">StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="a66e7-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="a66e7-130">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="a66e7-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
