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
ms.openlocfilehash: 1a361e04b6f8f39ec0083471d8cb47d5a29376c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000346"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="45ca1-102">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="45ca1-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="45ca1-103">以二進位格式，表示公用/私密金鑰組的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="45ca1-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45ca1-104">語法</span><span class="sxs-lookup"><span data-stu-id="45ca1-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="45ca1-105">成員</span><span class="sxs-lookup"><span data-stu-id="45ca1-105">Members</span></span>  
  
|<span data-ttu-id="45ca1-106">成員</span><span class="sxs-lookup"><span data-stu-id="45ca1-106">Member</span></span>|<span data-ttu-id="45ca1-107">描述</span><span class="sxs-lookup"><span data-stu-id="45ca1-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="45ca1-108">簽章演算法的識別項 (型別`ALG_ID`、 WinCrypt.h 中所定義) 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="45ca1-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="45ca1-109">雜湊演算法的識別項 (型別`ALG_ID`、 WinCrypt.h 中所定義) 的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="45ca1-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="45ca1-110">以位元組為單位的金鑰長度。</span><span class="sxs-lookup"><span data-stu-id="45ca1-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="45ca1-111">可變長度位元組陣列，其中包含的索引鍵值在 CryptoAPI 所傳回的格式。</span><span class="sxs-lookup"><span data-stu-id="45ca1-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45ca1-112">備註</span><span class="sxs-lookup"><span data-stu-id="45ca1-112">Remarks</span></span>  
 <span data-ttu-id="45ca1-113">`PublicKeyBlob`結構由[StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)， [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)，和其他的強式名稱函式，來代表公開/私密金鑰組的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="45ca1-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45ca1-114">需求</span><span class="sxs-lookup"><span data-stu-id="45ca1-114">Requirements</span></span>  
 <span data-ttu-id="45ca1-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="45ca1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45ca1-116">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="45ca1-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="45ca1-117">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="45ca1-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="45ca1-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45ca1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45ca1-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45ca1-119">See also</span></span>

- [<span data-ttu-id="45ca1-120">StrongNameGetPublicKey 函式</span><span class="sxs-lookup"><span data-stu-id="45ca1-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)
- [<span data-ttu-id="45ca1-121">StrongNameSignatureGeneration 函式</span><span class="sxs-lookup"><span data-stu-id="45ca1-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)
