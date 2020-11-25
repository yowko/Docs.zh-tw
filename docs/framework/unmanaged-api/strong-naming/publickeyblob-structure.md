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
ms.openlocfilehash: 42cd3cc22fbbb8eb3d5ac44544fce36650b6461f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705926"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="38d17-102">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="38d17-102">PublicKeyBlob Structure</span></span>

<span data-ttu-id="38d17-103">以二進位格式表示公開/私密金鑰組的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="38d17-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38d17-104">語法</span><span class="sxs-lookup"><span data-stu-id="38d17-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;
```  
  
## <a name="members"></a><span data-ttu-id="38d17-105">成員</span><span class="sxs-lookup"><span data-stu-id="38d17-105">Members</span></span>  
  
|<span data-ttu-id="38d17-106">member</span><span class="sxs-lookup"><span data-stu-id="38d17-106">Member</span></span>|<span data-ttu-id="38d17-107">描述</span><span class="sxs-lookup"><span data-stu-id="38d17-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="38d17-108">型別之簽章演算法 (的識別碼 `ALG_ID` ，如公開金鑰) WinCrypt 中所定義。</span><span class="sxs-lookup"><span data-stu-id="38d17-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="38d17-109">雜湊演算法 (的識別碼 `ALG_ID` ，如公開金鑰的 WinCrypt) 中所定義。</span><span class="sxs-lookup"><span data-stu-id="38d17-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="38d17-110">金鑰的長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="38d17-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="38d17-111">可變長度位元組陣列，其中包含 CryptoAPI 傳回之格式的索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="38d17-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38d17-112">備註</span><span class="sxs-lookup"><span data-stu-id="38d17-112">Remarks</span></span>  

 <span data-ttu-id="38d17-113">`PublicKeyBlob` [StrongNameGetPublicKey](strongnamegetpublickey-function.md)、 [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)和其他強式名稱函數會使用此結構來代表公開/私密金鑰組的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="38d17-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38d17-114">需求</span><span class="sxs-lookup"><span data-stu-id="38d17-114">Requirements</span></span>  

 <span data-ttu-id="38d17-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38d17-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38d17-116">**標頭：** Stackexchange.redis.strongname。h</span><span class="sxs-lookup"><span data-stu-id="38d17-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="38d17-117">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="38d17-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38d17-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38d17-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d17-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38d17-119">See also</span></span>

- [<span data-ttu-id="38d17-120">StrongNameGetPublicKey 函式</span><span class="sxs-lookup"><span data-stu-id="38d17-120">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="38d17-121">StrongNameSignatureGeneration 函式</span><span class="sxs-lookup"><span data-stu-id="38d17-121">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
