---
title: ICLRStrongName::StrongNameTokenFromAssemblyEx 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 00e425b56ae555b153685b5af0ac58b6ab4c335b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43391642"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a><span data-ttu-id="58a00-102">ICLRStrongName::StrongNameTokenFromAssemblyEx 方法</span><span class="sxs-lookup"><span data-stu-id="58a00-102">ICLRStrongName::StrongNameTokenFromAssemblyEx Method</span></span>
<span data-ttu-id="58a00-103">從指定的組件檔案中，建立強式名稱語彙基元，並傳回語彙基元所代表的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="58a00-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58a00-104">語法</span><span class="sxs-lookup"><span data-stu-id="58a00-104">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58a00-105">參數</span><span class="sxs-lookup"><span data-stu-id="58a00-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="58a00-106">[in]組件的可攜式執行檔 (PE) 檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="58a00-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="58a00-107">[out]傳回的強式名稱語彙基元。</span><span class="sxs-lookup"><span data-stu-id="58a00-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="58a00-108">[out]大小，以位元組為單位的強式名稱語彙基元。</span><span class="sxs-lookup"><span data-stu-id="58a00-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="58a00-109">[out]傳回的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="58a00-109">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="58a00-110">[out]以位元組為單位的公開金鑰大小。</span><span class="sxs-lookup"><span data-stu-id="58a00-110">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58a00-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="58a00-111">Return Value</span></span>  
 <span data-ttu-id="58a00-112">`S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="58a00-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58a00-113">備註</span><span class="sxs-lookup"><span data-stu-id="58a00-113">Remarks</span></span>  
 <span data-ttu-id="58a00-114">強式名稱語彙基元是公開金鑰的縮短格式。</span><span class="sxs-lookup"><span data-stu-id="58a00-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="58a00-115">64 位元雜湊建立用來簽署組件的公開金鑰權杖。</span><span class="sxs-lookup"><span data-stu-id="58a00-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="58a00-116">此權杖是組件的強式名稱的一部分，而且可以讀取組件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="58a00-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="58a00-117">擷取索引鍵，並建立權杖之後，您應該呼叫[iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法來釋放配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="58a00-117">After the key is retrieved and the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58a00-118">需求</span><span class="sxs-lookup"><span data-stu-id="58a00-118">Requirements</span></span>  
 <span data-ttu-id="58a00-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58a00-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58a00-120">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="58a00-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="58a00-121">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="58a00-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="58a00-122">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58a00-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58a00-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58a00-123">See Also</span></span>  
 [<span data-ttu-id="58a00-124">StrongNameTokenFromAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="58a00-124">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [<span data-ttu-id="58a00-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="58a00-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
