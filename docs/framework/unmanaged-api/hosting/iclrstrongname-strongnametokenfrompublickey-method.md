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
ms.openlocfilehash: e61a652072b424d1245518c832f9b0856e0f2021
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762600"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="5e2c3-102">ICLRStrongName::StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="5e2c3-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="5e2c3-103">取得表示公開金鑰的 token。</span><span class="sxs-lookup"><span data-stu-id="5e2c3-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="5e2c3-104">強式名稱 token 是公用金鑰的縮寫格式。</span><span class="sxs-lookup"><span data-stu-id="5e2c3-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e2c3-105">語法</span><span class="sxs-lookup"><span data-stu-id="5e2c3-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e2c3-106">參數</span><span class="sxs-lookup"><span data-stu-id="5e2c3-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="5e2c3-107">在[PublicKeyBlob](../strong-naming/publickeyblob-structure.md)類型的結構，其中包含用來產生強式名稱簽章之金鑰組的公開部分。</span><span class="sxs-lookup"><span data-stu-id="5e2c3-107">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="5e2c3-108">在的大小（以位元組為單位） `pbPublicKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="5e2c3-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="5e2c3-109">脫銷對應至傳入之金鑰的強式名稱 token `pbPublicKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="5e2c3-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="5e2c3-110">Common language runtime 會配置要在其中傳回 token 的記憶體。</span><span class="sxs-lookup"><span data-stu-id="5e2c3-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="5e2c3-111">呼叫端必須使用[ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md)方法來釋放這個記憶體。</span><span class="sxs-lookup"><span data-stu-id="5e2c3-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="5e2c3-112">脫銷傳回之強式名稱 token 的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="5e2c3-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e2c3-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="5e2c3-113">Return Value</span></span>  
 <span data-ttu-id="5e2c3-114">`S_OK`如果方法已成功完成，則為，否則，就是表示失敗的 HRESULT 值（請參閱清單的[一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="5e2c3-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e2c3-115">備註</span><span class="sxs-lookup"><span data-stu-id="5e2c3-115">Remarks</span></span>  
 <span data-ttu-id="5e2c3-116">強式名稱 token 是公用金鑰的簡短形式，用來儲存中繼資料中的金鑰資訊時，用來節省空間。</span><span class="sxs-lookup"><span data-stu-id="5e2c3-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="5e2c3-117">具體而言，強式名稱標記會在元件參考中用來參考相依元件。</span><span class="sxs-lookup"><span data-stu-id="5e2c3-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e2c3-118">規格需求</span><span class="sxs-lookup"><span data-stu-id="5e2c3-118">Requirements</span></span>  
 <span data-ttu-id="5e2c3-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e2c3-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e2c3-120">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="5e2c3-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5e2c3-121">連結**庫：** 包含為 mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5e2c3-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="5e2c3-122">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e2c3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e2c3-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e2c3-123">See also</span></span>

- [<span data-ttu-id="5e2c3-124">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="5e2c3-124">StrongNameGetPublicKey Method</span></span>](iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="5e2c3-125">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="5e2c3-125">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="5e2c3-126">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="5e2c3-126">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
