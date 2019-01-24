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
ms.openlocfilehash: eae7831d9a6d7bdee2c632359f317515c810428b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626780"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="4a675-102">StrongNameTokenFromAssemblyEx 函式</span><span class="sxs-lookup"><span data-stu-id="4a675-102">StrongNameTokenFromAssemblyEx Function</span></span>
<span data-ttu-id="4a675-103">從指定的組件檔案中，建立強式名稱語彙基元，並傳回語彙基元所代表的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="4a675-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="4a675-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="4a675-104">This function has been deprecated.</span></span> <span data-ttu-id="4a675-105">使用[iclrstrongname:: Strongnametokenfromassemblyex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="4a675-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a675-106">語法</span><span class="sxs-lookup"><span data-stu-id="4a675-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a675-107">參數</span><span class="sxs-lookup"><span data-stu-id="4a675-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="4a675-108">[in]組件的可攜式執行檔 (PE) 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="4a675-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="4a675-109">[out]傳回的強式名稱語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4a675-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="4a675-110">[out]大小，以位元組為單位的強式名稱語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4a675-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="4a675-111">[out]傳回的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="4a675-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="4a675-112">[out]以位元組為單位的公開金鑰大小。</span><span class="sxs-lookup"><span data-stu-id="4a675-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a675-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="4a675-113">Return Value</span></span>  
 <span data-ttu-id="4a675-114">`true` 如果成功地完成;否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="4a675-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a675-115">備註</span><span class="sxs-lookup"><span data-stu-id="4a675-115">Remarks</span></span>  
 <span data-ttu-id="4a675-116">強式名稱語彙基元是公開金鑰的縮短格式。</span><span class="sxs-lookup"><span data-stu-id="4a675-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="4a675-117">64 位元雜湊建立用來簽署組件的公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="4a675-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="4a675-118">此權杖是組件的強式名稱的一部分，而且可以讀取組件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="4a675-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="4a675-119">擷取索引鍵，並建立權杖之後，您應該呼叫[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函式來釋放配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="4a675-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="4a675-120">如果`StrongNameTokenFromAssemblyEx`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式來擷取最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4a675-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a675-121">需求</span><span class="sxs-lookup"><span data-stu-id="4a675-121">Requirements</span></span>  
 <span data-ttu-id="4a675-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a675-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a675-123">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="4a675-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="4a675-124">**程式庫：** 包含做為 mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4a675-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="4a675-125">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a675-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a675-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a675-126">See also</span></span>
- [<span data-ttu-id="4a675-127">StrongNameTokenFromAssemblyEx 方法</span><span class="sxs-lookup"><span data-stu-id="4a675-127">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="4a675-128">StrongNameTokenFromAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="4a675-128">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="4a675-129">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="4a675-129">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
