---
title: StrongNameTokenFromPublicKey 函式
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
ms.openlocfilehash: 20be3114908ef78966eead05ae8ba6333a491404
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175053"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="2be16-102">StrongNameTokenFromPublicKey 函式</span><span class="sxs-lookup"><span data-stu-id="2be16-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="2be16-103">取得代表公開金鑰的權杖。</span><span class="sxs-lookup"><span data-stu-id="2be16-103">Gets a token representing a public key.</span></span> <span data-ttu-id="2be16-104">強式名稱權杖是公開金鑰的縮寫形式。</span><span class="sxs-lookup"><span data-stu-id="2be16-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="2be16-105">此函數已被棄用。</span><span class="sxs-lookup"><span data-stu-id="2be16-105">This function has been deprecated.</span></span> <span data-ttu-id="2be16-106">改用[ICLR 強式名稱：：強式名稱權杖來自公共金鑰](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="2be16-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2be16-107">語法</span><span class="sxs-lookup"><span data-stu-id="2be16-107">Syntax</span></span>  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2be16-108">參數</span><span class="sxs-lookup"><span data-stu-id="2be16-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="2be16-109">[在][公共金鑰Blob](publickeyblob-structure.md)類型的結構，其中包含用於生成強式名稱簽名的金鑰組的公共部分。</span><span class="sxs-lookup"><span data-stu-id="2be16-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="2be16-110">[在]的大小（以位元組為單位）的大小`pbPublicKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="2be16-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="2be16-111">[出]與傳入的鍵對應的強式名稱權杖`pbPublicKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="2be16-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="2be16-112">通用語言運行時分配要返回權杖的記憶體。</span><span class="sxs-lookup"><span data-stu-id="2be16-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="2be16-113">調用方必須使用[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函數釋放此記憶體。</span><span class="sxs-lookup"><span data-stu-id="2be16-113">The caller must free this memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="2be16-114">[出]返回的強式名稱權杖的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="2be16-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2be16-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="2be16-115">Return Value</span></span>  
 <span data-ttu-id="2be16-116">`true`成功完成;否則， `false`.</span><span class="sxs-lookup"><span data-stu-id="2be16-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2be16-117">備註</span><span class="sxs-lookup"><span data-stu-id="2be16-117">Remarks</span></span>  
 <span data-ttu-id="2be16-118">強式名稱權杖是公開金鑰的縮寫形式，用於在中繼資料中存儲關鍵資訊時節省空間。</span><span class="sxs-lookup"><span data-stu-id="2be16-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="2be16-119">具體而言，強式名稱權杖用於程式集引用以引用依存性程式集。</span><span class="sxs-lookup"><span data-stu-id="2be16-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="2be16-120">如果`StrongNameTokenFromPublicKey`函數未成功完成，請調用[StrongNameErrorInfo 函數](strongnameerrorinfo-function.md)以檢索上次生成的錯誤。</span><span class="sxs-lookup"><span data-stu-id="2be16-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2be16-121">需求</span><span class="sxs-lookup"><span data-stu-id="2be16-121">Requirements</span></span>  
 <span data-ttu-id="2be16-122">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2be16-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2be16-123">**標題：** 強式名稱.h</span><span class="sxs-lookup"><span data-stu-id="2be16-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2be16-124">**庫：** 作為資源包含在 mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="2be16-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="2be16-125">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2be16-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2be16-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2be16-126">See also</span></span>

- [<span data-ttu-id="2be16-127">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="2be16-127">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="2be16-128">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="2be16-128">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="2be16-129">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="2be16-129">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
