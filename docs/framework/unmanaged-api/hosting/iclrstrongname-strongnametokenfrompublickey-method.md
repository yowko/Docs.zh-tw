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
ms.openlocfilehash: 919c1321f18ca163481d27fa204c78f38af1e456
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176314"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="12133-102">ICLRStrongName::StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="12133-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="12133-103">獲取表示公開金鑰的權杖。</span><span class="sxs-lookup"><span data-stu-id="12133-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="12133-104">強式名稱權杖是公開金鑰的縮寫形式。</span><span class="sxs-lookup"><span data-stu-id="12133-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12133-105">語法</span><span class="sxs-lookup"><span data-stu-id="12133-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12133-106">參數</span><span class="sxs-lookup"><span data-stu-id="12133-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="12133-107">[在][公共金鑰Blob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)類型的結構，其中包含用於生成強式名稱簽名的金鑰組的公共部分。</span><span class="sxs-lookup"><span data-stu-id="12133-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="12133-108">[在]的大小（以位元組為單位）的大小`pbPublicKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="12133-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="12133-109">[出]與傳入的鍵對應的強式名稱權杖`pbPublicKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="12133-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="12133-110">通用語言運行時分配要返回權杖的記憶體。</span><span class="sxs-lookup"><span data-stu-id="12133-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="12133-111">調用方必須使用[ICLRStrongNameName：：StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法釋放此記憶體。</span><span class="sxs-lookup"><span data-stu-id="12133-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="12133-112">[出]返回的強式名稱權杖的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="12133-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12133-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="12133-113">Return Value</span></span>  
 <span data-ttu-id="12133-114">`S_OK`如果方法成功完成;如果方法成功完成;否則，指示失敗的 HRESULT 值（請參閱清單[的常用 HRESULT 值](/windows/win32/seccrypto/common-hresult-values)）。</span><span class="sxs-lookup"><span data-stu-id="12133-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12133-115">備註</span><span class="sxs-lookup"><span data-stu-id="12133-115">Remarks</span></span>  
 <span data-ttu-id="12133-116">強式名稱權杖是公開金鑰的縮短形式，用於在中繼資料中存儲關鍵資訊時節省空間。</span><span class="sxs-lookup"><span data-stu-id="12133-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="12133-117">具體而言，強式名稱權杖用於程式集引用以引用依存性程式集。</span><span class="sxs-lookup"><span data-stu-id="12133-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12133-118">需求</span><span class="sxs-lookup"><span data-stu-id="12133-118">Requirements</span></span>  
 <span data-ttu-id="12133-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="12133-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12133-120">**標題：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="12133-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="12133-121">**庫：** 作為資源包含在 mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="12133-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="12133-122">**.NET 框架版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12133-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12133-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12133-123">See also</span></span>

- [<span data-ttu-id="12133-124">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="12133-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="12133-125">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="12133-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="12133-126">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="12133-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
