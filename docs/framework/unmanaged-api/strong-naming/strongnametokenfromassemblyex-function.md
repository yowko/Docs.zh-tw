---
title: StrongNameTokenFromAssemblyEx 函式
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c000aad12000a9c76fb6dd805a9b002c021be6ef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798837"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="f89ce-102">StrongNameTokenFromAssemblyEx 函式</span><span class="sxs-lookup"><span data-stu-id="f89ce-102">StrongNameTokenFromAssemblyEx Function</span></span>
<span data-ttu-id="f89ce-103">從指定的元件檔案建立強式名稱 token，並傳回權杖所代表的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="f89ce-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="f89ce-104">這個函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="f89ce-104">This function has been deprecated.</span></span> <span data-ttu-id="f89ce-105">請改用[ICLRStrongName：： StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="f89ce-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f89ce-106">語法</span><span class="sxs-lookup"><span data-stu-id="f89ce-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f89ce-107">參數</span><span class="sxs-lookup"><span data-stu-id="f89ce-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="f89ce-108">在元件的可移植執行檔（PE）路徑。</span><span class="sxs-lookup"><span data-stu-id="f89ce-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="f89ce-109">脫銷傳回的強式名稱 token。</span><span class="sxs-lookup"><span data-stu-id="f89ce-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="f89ce-110">脫銷強式名稱 token 的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="f89ce-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="f89ce-111">脫銷傳回的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="f89ce-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="f89ce-112">脫銷公用金鑰的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="f89ce-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f89ce-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="f89ce-113">Return Value</span></span>  
 <span data-ttu-id="f89ce-114">`true`成功完成時;否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="f89ce-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f89ce-115">備註</span><span class="sxs-lookup"><span data-stu-id="f89ce-115">Remarks</span></span>  
 <span data-ttu-id="f89ce-116">強式名稱 token 是公用金鑰的縮寫格式。</span><span class="sxs-lookup"><span data-stu-id="f89ce-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="f89ce-117">Token 是從用來簽署元件的公開金鑰所建立的64位雜湊。</span><span class="sxs-lookup"><span data-stu-id="f89ce-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="f89ce-118">Token 是元件強式名稱的一部分，而且可以從元件中繼資料讀取。</span><span class="sxs-lookup"><span data-stu-id="f89ce-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="f89ce-119">在取得金鑰並建立權杖之後，您應該呼叫[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函式以釋放已配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="f89ce-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="f89ce-120">如果函式未順利完成，請呼叫 [StrongNameErrorInfo](strongnameerrorinfo-function.md) 函式，以取出最後產生的錯誤。`StrongNameTokenFromAssemblyEx`</span><span class="sxs-lookup"><span data-stu-id="f89ce-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f89ce-121">需求</span><span class="sxs-lookup"><span data-stu-id="f89ce-121">Requirements</span></span>  
 <span data-ttu-id="f89ce-122">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f89ce-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f89ce-123">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="f89ce-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f89ce-124">**LIBRARY:** 包含為 mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f89ce-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="f89ce-125">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f89ce-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f89ce-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f89ce-126">See also</span></span>

- [<span data-ttu-id="f89ce-127">StrongNameTokenFromAssemblyEx 方法</span><span class="sxs-lookup"><span data-stu-id="f89ce-127">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="f89ce-128">StrongNameTokenFromAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="f89ce-128">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="f89ce-129">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="f89ce-129">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
