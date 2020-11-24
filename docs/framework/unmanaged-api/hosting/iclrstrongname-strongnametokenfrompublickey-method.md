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
ms.openlocfilehash: c727d4524bc40ab90eee90faf16788140a73ad9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677657"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="bdeb2-102">ICLRStrongName::StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="bdeb2-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>

<span data-ttu-id="bdeb2-103">取得代表公開金鑰的 token。</span><span class="sxs-lookup"><span data-stu-id="bdeb2-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="bdeb2-104">強式名稱權杖是公開金鑰的縮寫形式。</span><span class="sxs-lookup"><span data-stu-id="bdeb2-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdeb2-105">語法</span><span class="sxs-lookup"><span data-stu-id="bdeb2-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdeb2-106">參數</span><span class="sxs-lookup"><span data-stu-id="bdeb2-106">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="bdeb2-107">在 [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) 類型的結構，其中包含用來產生強式名稱簽章之金鑰組的公開部分。</span><span class="sxs-lookup"><span data-stu-id="bdeb2-107">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="bdeb2-108">在的大小（以位元組為單位） `pbPublicKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="bdeb2-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="bdeb2-109">擴展與傳入的金鑰組應的強式名稱標記 `pbPublicKeyBlob` 。</span><span class="sxs-lookup"><span data-stu-id="bdeb2-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="bdeb2-110">Common language runtime 會配置要傳回權杖的記憶體。</span><span class="sxs-lookup"><span data-stu-id="bdeb2-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="bdeb2-111">呼叫端必須使用 [ICLRStrongName：： StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) 方法釋放這個記憶體。</span><span class="sxs-lookup"><span data-stu-id="bdeb2-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="bdeb2-112">擴展傳回之強式名稱 token 的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="bdeb2-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bdeb2-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="bdeb2-113">Return Value</span></span>  

 <span data-ttu-id="bdeb2-114">`S_OK` 如果方法成功完成，則為，否則，表示失敗 (的 HRESULT 值會看到清單) 的 [一般 HRESULT 值](/windows/win32/seccrypto/common-hresult-values) 。</span><span class="sxs-lookup"><span data-stu-id="bdeb2-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdeb2-115">備註</span><span class="sxs-lookup"><span data-stu-id="bdeb2-115">Remarks</span></span>  

 <span data-ttu-id="bdeb2-116">強式名稱權杖是公開金鑰的縮寫形式，用來節省在中繼資料中儲存金鑰資訊時的空間。</span><span class="sxs-lookup"><span data-stu-id="bdeb2-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="bdeb2-117">具體而言，強式名稱標記會在元件參考中用來參考相依元件。</span><span class="sxs-lookup"><span data-stu-id="bdeb2-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdeb2-118">需求</span><span class="sxs-lookup"><span data-stu-id="bdeb2-118">Requirements</span></span>  

 <span data-ttu-id="bdeb2-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bdeb2-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdeb2-120">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="bdeb2-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bdeb2-121">連結 **庫：** 以資源的形式包含在 mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="bdeb2-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="bdeb2-122">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdeb2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdeb2-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdeb2-123">See also</span></span>

- [<span data-ttu-id="bdeb2-124">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="bdeb2-124">StrongNameGetPublicKey Method</span></span>](iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="bdeb2-125">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="bdeb2-125">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="bdeb2-126">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="bdeb2-126">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
