---
title: PublicKeyBlob 結構
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd7a4b19613ea771a055af7dd91ec368859ee191
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43475968"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="938c4-102">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="938c4-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="938c4-103">以二進位格式，表示公用/私密金鑰組的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="938c4-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="938c4-104">語法</span><span class="sxs-lookup"><span data-stu-id="938c4-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="938c4-105">成員</span><span class="sxs-lookup"><span data-stu-id="938c4-105">Members</span></span>  
  
|<span data-ttu-id="938c4-106">成員</span><span class="sxs-lookup"><span data-stu-id="938c4-106">Member</span></span>|<span data-ttu-id="938c4-107">描述</span><span class="sxs-lookup"><span data-stu-id="938c4-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="938c4-108">簽章演算法的識別項 (型別`ALG_ID`、 WinCrypt.h 中所定義) 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="938c4-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="938c4-109">雜湊演算法的識別項 (型別`ALG_ID`、 WinCrypt.h 中所定義) 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="938c4-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="938c4-110">以位元組為單位的金鑰長度。</span><span class="sxs-lookup"><span data-stu-id="938c4-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="938c4-111">可變長度位元組陣列，其中包含的索引鍵值在 CryptoAPI 所傳回的格式。</span><span class="sxs-lookup"><span data-stu-id="938c4-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="938c4-112">備註</span><span class="sxs-lookup"><span data-stu-id="938c4-112">Remarks</span></span>  
 <span data-ttu-id="938c4-113">`PublicKeyBlob`結構由[StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)， [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)，和其他的強式名稱函式，來代表公開/私密金鑰組的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="938c4-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="938c4-114">需求</span><span class="sxs-lookup"><span data-stu-id="938c4-114">Requirements</span></span>  
 <span data-ttu-id="938c4-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="938c4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="938c4-116">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="938c4-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="938c4-117">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="938c4-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="938c4-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="938c4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="938c4-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="938c4-119">See Also</span></span>  
 [<span data-ttu-id="938c4-120">StrongNameGetPublicKey 函式</span><span class="sxs-lookup"><span data-stu-id="938c4-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 [<span data-ttu-id="938c4-121">StrongNameSignatureGeneration 函式</span><span class="sxs-lookup"><span data-stu-id="938c4-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 [<span data-ttu-id="938c4-122">強式命名結構</span><span class="sxs-lookup"><span data-stu-id="938c4-122">Strong Naming Structures</span></span>](https://msdn.microsoft.com/library/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)
