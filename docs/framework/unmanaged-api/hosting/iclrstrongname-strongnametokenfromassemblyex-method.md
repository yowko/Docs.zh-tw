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
ms.openlocfilehash: 71fda266c22c4beb1e1f9c81c84d6c56a0a6110e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092578"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a><span data-ttu-id="c53ad-102">ICLRStrongName::StrongNameTokenFromAssemblyEx 方法</span><span class="sxs-lookup"><span data-stu-id="c53ad-102">ICLRStrongName::StrongNameTokenFromAssemblyEx Method</span></span>
<span data-ttu-id="c53ad-103">從指定的元件檔案建立強式名稱 token，並傳回權杖所代表的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="c53ad-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c53ad-104">語法</span><span class="sxs-lookup"><span data-stu-id="c53ad-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c53ad-105">參數</span><span class="sxs-lookup"><span data-stu-id="c53ad-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="c53ad-106">在元件的可移植執行檔（PE）路徑。</span><span class="sxs-lookup"><span data-stu-id="c53ad-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="c53ad-107">脫銷傳回的強式名稱 token。</span><span class="sxs-lookup"><span data-stu-id="c53ad-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="c53ad-108">脫銷強式名稱 token 的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="c53ad-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="c53ad-109">脫銷傳回的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="c53ad-109">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="c53ad-110">脫銷公用金鑰的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="c53ad-110">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c53ad-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="c53ad-111">Return Value</span></span>  
 <span data-ttu-id="c53ad-112">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)）。</span><span class="sxs-lookup"><span data-stu-id="c53ad-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c53ad-113">備註</span><span class="sxs-lookup"><span data-stu-id="c53ad-113">Remarks</span></span>  
 <span data-ttu-id="c53ad-114">強式名稱 token 是公用金鑰的縮寫格式。</span><span class="sxs-lookup"><span data-stu-id="c53ad-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="c53ad-115">Token 是從用來簽署元件的公開金鑰所建立的64位雜湊。</span><span class="sxs-lookup"><span data-stu-id="c53ad-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="c53ad-116">Token 是元件強式名稱的一部分，而且可以從元件中繼資料讀取。</span><span class="sxs-lookup"><span data-stu-id="c53ad-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="c53ad-117">在取得金鑰並建立權杖之後，您應該呼叫[ICLRStrongName：： StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法來釋放已配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="c53ad-117">After the key is retrieved and the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c53ad-118">需求</span><span class="sxs-lookup"><span data-stu-id="c53ad-118">Requirements</span></span>  
 <span data-ttu-id="c53ad-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c53ad-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c53ad-120">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="c53ad-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c53ad-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c53ad-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c53ad-122">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c53ad-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c53ad-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="c53ad-123">See also</span></span>

- [<span data-ttu-id="c53ad-124">StrongNameTokenFromAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="c53ad-124">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="c53ad-125">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="c53ad-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
