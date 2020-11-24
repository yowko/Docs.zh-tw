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
ms.openlocfilehash: 4844701784a3e6a1008a5deb2bdff3b3ba47aa7e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691405"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="aaf64-102">StrongNameKeyGen 函式</span><span class="sxs-lookup"><span data-stu-id="aaf64-102">StrongNameKeyGen Function</span></span>

<span data-ttu-id="aaf64-103">建立將供強式名稱使用的新公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="aaf64-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="aaf64-104">此函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="aaf64-104">This function has been deprecated.</span></span> <span data-ttu-id="aaf64-105">請改用 [ICLRStrongName：： StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="aaf64-105">Use the [ICLRStrongName::StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaf64-106">語法</span><span class="sxs-lookup"><span data-stu-id="aaf64-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaf64-107">參數</span><span class="sxs-lookup"><span data-stu-id="aaf64-107">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="aaf64-108">在要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="aaf64-108">[in] The requested key container name.</span></span> <span data-ttu-id="aaf64-109">`wszKeyContainer` 必須是非空白字串，或 null 以產生暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="aaf64-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="aaf64-110">在指定是否保留註冊的金鑰。</span><span class="sxs-lookup"><span data-stu-id="aaf64-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="aaf64-111">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="aaf64-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="aaf64-112">0x00000000-當 `wszKeyContainer` 為 null 時，用來產生暫存金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="aaf64-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="aaf64-113">0x00000001 (`SN_LEAVE_KEY`) -指定應該將金鑰保持在註冊。</span><span class="sxs-lookup"><span data-stu-id="aaf64-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="aaf64-114">擴展傳回的公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="aaf64-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="aaf64-115">擴展的大小（以位元組為單位） `ppbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="aaf64-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aaf64-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="aaf64-116">Return Value</span></span>  

 <span data-ttu-id="aaf64-117">`true` 成功完成時;否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="aaf64-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaf64-118">備註</span><span class="sxs-lookup"><span data-stu-id="aaf64-118">Remarks</span></span>  

 <span data-ttu-id="aaf64-119">`StrongNameKeyGen`函數會建立1024位的金鑰。</span><span class="sxs-lookup"><span data-stu-id="aaf64-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="aaf64-120">在抓取金鑰之後，您應該呼叫 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 函式來釋放配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="aaf64-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="aaf64-121">如果函式 `StrongNameKeyGen` 未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式來取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="aaf64-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaf64-122">需求</span><span class="sxs-lookup"><span data-stu-id="aaf64-122">Requirements</span></span>  

 <span data-ttu-id="aaf64-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aaf64-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaf64-124">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="aaf64-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="aaf64-125">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="aaf64-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aaf64-126">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaf64-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaf64-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aaf64-127">See also</span></span>

- [<span data-ttu-id="aaf64-128">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="aaf64-128">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="aaf64-129">StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="aaf64-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="aaf64-130">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="aaf64-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
