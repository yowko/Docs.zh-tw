---
title: ICLRStrongName::StrongNameTokenFromPublicKey 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
ms.openlocfilehash: 13c1c505d939c1048eebef3d1d6b2abe493d319e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937413"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="ce676-102">ICLRStrongName::StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="ce676-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="ce676-103">取得表示公開金鑰的 token。</span><span class="sxs-lookup"><span data-stu-id="ce676-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="ce676-104">強式名稱 token 是公用金鑰的縮寫格式。</span><span class="sxs-lookup"><span data-stu-id="ce676-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce676-105">語法</span><span class="sxs-lookup"><span data-stu-id="ce676-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce676-106">參數</span><span class="sxs-lookup"><span data-stu-id="ce676-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="ce676-107">在[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)類型的結構，其中包含用來產生強式名稱簽章之金鑰組的公開部分。</span><span class="sxs-lookup"><span data-stu-id="ce676-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="ce676-108">在`pbPublicKeyBlob`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="ce676-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="ce676-109">脫銷對應至 `pbPublicKeyBlob`中所傳遞之金鑰的強式名稱 token。</span><span class="sxs-lookup"><span data-stu-id="ce676-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="ce676-110">Common language runtime 會配置要在其中傳回 token 的記憶體。</span><span class="sxs-lookup"><span data-stu-id="ce676-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="ce676-111">呼叫端必須使用[ICLRStrongName：： StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法來釋放這個記憶體。</span><span class="sxs-lookup"><span data-stu-id="ce676-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="ce676-112">脫銷傳回之強式名稱 token 的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="ce676-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce676-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="ce676-113">Return Value</span></span>  
 <span data-ttu-id="ce676-114">如果方法順利完成，`S_OK`;否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="ce676-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce676-115">備註</span><span class="sxs-lookup"><span data-stu-id="ce676-115">Remarks</span></span>  
 <span data-ttu-id="ce676-116">強式名稱 token 是公用金鑰的簡短形式，用來儲存中繼資料中的金鑰資訊時，用來節省空間。</span><span class="sxs-lookup"><span data-stu-id="ce676-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="ce676-117">具體而言，強式名稱標記會在元件參考中用來參考相依元件。</span><span class="sxs-lookup"><span data-stu-id="ce676-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce676-118">需求</span><span class="sxs-lookup"><span data-stu-id="ce676-118">Requirements</span></span>  
 <span data-ttu-id="ce676-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce676-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce676-120">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="ce676-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ce676-121">連結**庫：** 包含為 mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ce676-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="ce676-122">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce676-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce676-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="ce676-123">See also</span></span>

- [<span data-ttu-id="ce676-124">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="ce676-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="ce676-125">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="ce676-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="ce676-126">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="ce676-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
