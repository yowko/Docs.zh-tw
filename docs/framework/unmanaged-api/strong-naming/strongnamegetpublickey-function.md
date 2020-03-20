---
title: StrongNameGetPublicKey 函式
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
ms.openlocfilehash: fcdd4a3f07b4499fd2388b5d165c409da9150466
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176925"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="d3178-102">StrongNameGetPublicKey 函式</span><span class="sxs-lookup"><span data-stu-id="d3178-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="d3178-103">從私密/公開金鑰組取得公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="d3178-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="d3178-104">金鑰組可以作為加密服務提供者 （CSP） 中的金鑰容器名稱提供，也可以作為位元組的原創組合提供。</span><span class="sxs-lookup"><span data-stu-id="d3178-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="d3178-105">此函數已被棄用。</span><span class="sxs-lookup"><span data-stu-id="d3178-105">This function has been deprecated.</span></span> <span data-ttu-id="d3178-106">改用[ICLR 強式名稱：：強式名稱GetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d3178-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3178-107">語法</span><span class="sxs-lookup"><span data-stu-id="d3178-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3178-108">參數</span><span class="sxs-lookup"><span data-stu-id="d3178-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="d3178-109">[在]包含公開金鑰/私密金鑰對的金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="d3178-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="d3178-110">如果`pbKeyBlob`為 null，`szKeyContainer`則必須在 CSP 中指定有效的容器。</span><span class="sxs-lookup"><span data-stu-id="d3178-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="d3178-111">在這種情況下，`StrongNameGetPublicKey`從容器中存儲的金鑰組中提取公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="d3178-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="d3178-112">如果`pbKeyBlob`不是空，則假定金鑰組包含在金鑰二進位大型物件 （BLOB） 中。</span><span class="sxs-lookup"><span data-stu-id="d3178-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="d3178-113">金鑰必須是 1024 位裡維斯-沙米爾-阿德爾曼 （RSA） 簽名金鑰。</span><span class="sxs-lookup"><span data-stu-id="d3178-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="d3178-114">目前不支援其他類型的金鑰。</span><span class="sxs-lookup"><span data-stu-id="d3178-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="d3178-115">[在]指向公開金鑰/私密金鑰對的指標。</span><span class="sxs-lookup"><span data-stu-id="d3178-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="d3178-116">此對採用 Win32`CryptExportKey`函數創建的格式。</span><span class="sxs-lookup"><span data-stu-id="d3178-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="d3178-117">如果`pbKeyBlob`為 null，則假定 指定的`szKeyContainer`鍵容器包含金鑰組。</span><span class="sxs-lookup"><span data-stu-id="d3178-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="d3178-118">[在]的大小（以位元組為單位）的大小`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="d3178-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="d3178-119">[出]返回的公開金鑰 BLOB。</span><span class="sxs-lookup"><span data-stu-id="d3178-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="d3178-120">參數`ppbPublicKeyBlob`由通用語言運行時分配並返回到調用方。</span><span class="sxs-lookup"><span data-stu-id="d3178-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="d3178-121">調用方必須使用[StrongNameFreeBuffer](strongnamefreebuffer-function.md)函數釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="d3178-121">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="d3178-122">[出]返回的公開金鑰 BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="d3178-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3178-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="d3178-123">Return Value</span></span>  
 <span data-ttu-id="d3178-124">`true`成功完成;否則， `false`.</span><span class="sxs-lookup"><span data-stu-id="d3178-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3178-125">備註</span><span class="sxs-lookup"><span data-stu-id="d3178-125">Remarks</span></span>  
 <span data-ttu-id="d3178-126">公開金鑰包含在[PublicKeyBlob](publickeyblob-structure.md)結構中。</span><span class="sxs-lookup"><span data-stu-id="d3178-126">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="d3178-127">如果`StrongNameGetPublicKey`函數未成功完成，請調用[StrongNameErrorInfo 函數](strongnameerrorinfo-function.md)以檢索上次生成的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d3178-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3178-128">需求</span><span class="sxs-lookup"><span data-stu-id="d3178-128">Requirements</span></span>  
 <span data-ttu-id="d3178-129">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3178-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3178-130">**標題：** 強式名稱.h</span><span class="sxs-lookup"><span data-stu-id="d3178-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d3178-131">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="d3178-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d3178-132">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3178-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3178-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3178-133">See also</span></span>

- [<span data-ttu-id="d3178-134">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="d3178-134">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="d3178-135">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="d3178-135">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="d3178-136">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="d3178-136">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="d3178-137">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="d3178-137">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
