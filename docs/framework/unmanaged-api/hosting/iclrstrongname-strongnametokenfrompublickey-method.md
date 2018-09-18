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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98c0dbbbe65d8f8c0b0196c82db1a8fd2b0ee3dd
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46000592"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="af0af-102">ICLRStrongName::StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="af0af-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="af0af-103">取得代表公開金鑰 token。</span><span class="sxs-lookup"><span data-stu-id="af0af-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="af0af-104">強式名稱語彙基元是公開金鑰的縮短格式。</span><span class="sxs-lookup"><span data-stu-id="af0af-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af0af-105">語法</span><span class="sxs-lookup"><span data-stu-id="af0af-105">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af0af-106">參數</span><span class="sxs-lookup"><span data-stu-id="af0af-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="af0af-107">[in]類型的結構[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) ，其中包含用來產生強式名稱簽章金鑰組的公開部分。</span><span class="sxs-lookup"><span data-stu-id="af0af-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="af0af-108">[in]大小，以位元組為單位的`pbPublicKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="af0af-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="af0af-109">[out]對應到索引鍵的強式名稱語彙基元傳遞`pbPublicKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="af0af-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="af0af-110">Common language runtime 配置的記憶體，在其中傳回的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="af0af-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="af0af-111">呼叫端必須使用釋放這個記憶體[iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="af0af-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="af0af-112">[out]大小 （位元組），傳回的強式名稱語彙基元。</span><span class="sxs-lookup"><span data-stu-id="af0af-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af0af-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="af0af-113">Return Value</span></span>  
 <span data-ttu-id="af0af-114">`S_OK` 如果這個方法順利完成否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="af0af-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af0af-115">備註</span><span class="sxs-lookup"><span data-stu-id="af0af-115">Remarks</span></span>  
 <span data-ttu-id="af0af-116">強式名稱語彙基元是公開金鑰的用來儲存空間，將金鑰資訊儲存在中繼資料中的縮短格式。</span><span class="sxs-lookup"><span data-stu-id="af0af-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="af0af-117">具體來說，強式名稱語彙基元會在組件參考中用來參考相依的組件。</span><span class="sxs-lookup"><span data-stu-id="af0af-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af0af-118">需求</span><span class="sxs-lookup"><span data-stu-id="af0af-118">Requirements</span></span>  
 <span data-ttu-id="af0af-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af0af-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af0af-120">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="af0af-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="af0af-121">**程式庫：** 包含做為 mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="af0af-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="af0af-122">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af0af-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af0af-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af0af-123">See Also</span></span>  
 [<span data-ttu-id="af0af-124">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="af0af-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="af0af-125">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="af0af-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="af0af-126">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="af0af-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
