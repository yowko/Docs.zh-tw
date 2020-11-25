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
ms.openlocfilehash: f28ee5767997240018d182b8303e4f65be81c702
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708539"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="b64cb-102">StrongNameKeyGenEx 函式</span><span class="sxs-lookup"><span data-stu-id="b64cb-102">StrongNameKeyGenEx Function</span></span>

<span data-ttu-id="b64cb-103">使用指定的金鑰大小產生新的公開/私密金鑰組，以供強式名稱使用。</span><span class="sxs-lookup"><span data-stu-id="b64cb-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="b64cb-104">此函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="b64cb-104">This function has been deprecated.</span></span> <span data-ttu-id="b64cb-105">請改用 [ICLRStrongName：： StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="b64cb-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b64cb-106">語法</span><span class="sxs-lookup"><span data-stu-id="b64cb-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b64cb-107">參數</span><span class="sxs-lookup"><span data-stu-id="b64cb-107">Parameters</span></span>  

 `wszKeyContainer`  
 <span data-ttu-id="b64cb-108">在要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="b64cb-108">[in] The requested key container name.</span></span> <span data-ttu-id="b64cb-109">`wszKeyContainer` 必須是非空白字串，或 null 以產生暫存名稱。</span><span class="sxs-lookup"><span data-stu-id="b64cb-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b64cb-110">在指定是否保留註冊的金鑰。</span><span class="sxs-lookup"><span data-stu-id="b64cb-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="b64cb-111">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="b64cb-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="b64cb-112">0x00000000-當 `wszKeyContainer` 為 null 時，用來產生暫存金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="b64cb-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="b64cb-113">0x00000001 (`SN_LEAVE_KEY`) -指定應該將金鑰保持在註冊。</span><span class="sxs-lookup"><span data-stu-id="b64cb-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="b64cb-114">在要求的金鑰大小（以位為單位）。</span><span class="sxs-lookup"><span data-stu-id="b64cb-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="b64cb-115">擴展傳回的公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="b64cb-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="b64cb-116">擴展的大小（以位元組為單位） `ppbKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="b64cb-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b64cb-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="b64cb-117">Return Value</span></span>  

 <span data-ttu-id="b64cb-118">`true` 成功完成時;否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="b64cb-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b64cb-119">備註</span><span class="sxs-lookup"><span data-stu-id="b64cb-119">Remarks</span></span>  

 <span data-ttu-id="b64cb-120">.NET Framework 版本1.0 和1.1 需要 `dwKeySize` 1024 位來簽署具有強式名稱的元件; 2.0 版新增了針對2048位金鑰支援的功能。</span><span class="sxs-lookup"><span data-stu-id="b64cb-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="b64cb-121">在抓取金鑰之後，您應該呼叫 [StrongNameFreeBuffer](strongnamefreebuffer-function.md) 函式來釋放配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="b64cb-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="b64cb-122">如果函式 `StrongNameKeyGenEx` 未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式來取出最後產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b64cb-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b64cb-123">需求</span><span class="sxs-lookup"><span data-stu-id="b64cb-123">Requirements</span></span>  

 <span data-ttu-id="b64cb-124">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b64cb-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b64cb-125">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="b64cb-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b64cb-126">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="b64cb-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b64cb-127">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b64cb-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b64cb-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b64cb-128">See also</span></span>

- [<span data-ttu-id="b64cb-129">StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="b64cb-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="b64cb-130">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="b64cb-130">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="b64cb-131">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="b64cb-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
