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
ms.openlocfilehash: 3b00bf8295a635871bd7263928ff21c97053cc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176951"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="0f0b1-102">PublicKeyBlob 結構</span><span class="sxs-lookup"><span data-stu-id="0f0b1-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="0f0b1-103">以二進位格式表示公開金鑰/私密金鑰對的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="0f0b1-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f0b1-104">語法</span><span class="sxs-lookup"><span data-stu-id="0f0b1-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;
```  
  
## <a name="members"></a><span data-ttu-id="0f0b1-105">成員</span><span class="sxs-lookup"><span data-stu-id="0f0b1-105">Members</span></span>  
  
|<span data-ttu-id="0f0b1-106">member</span><span class="sxs-lookup"><span data-stu-id="0f0b1-106">Member</span></span>|<span data-ttu-id="0f0b1-107">描述</span><span class="sxs-lookup"><span data-stu-id="0f0b1-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="0f0b1-108">公開金鑰的簽名演算法（類型`ALG_ID`，如 WinCrypt.h 中定義的）的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0f0b1-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="0f0b1-109">公開金鑰的雜湊演算法（類型`ALG_ID`，在 WinCrypt.h 中定義）的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0f0b1-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="0f0b1-110">鍵的長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="0f0b1-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="0f0b1-111">一個可變長度位元組陣列，包含 CryptoAPI 返回的格式中的鍵值。</span><span class="sxs-lookup"><span data-stu-id="0f0b1-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f0b1-112">備註</span><span class="sxs-lookup"><span data-stu-id="0f0b1-112">Remarks</span></span>  
 <span data-ttu-id="0f0b1-113">該`PublicKeyBlob`結構由[StrongNameGetPublicKey、](strongnamegetpublickey-function.md)[強式名稱簽名生成](strongnamesignaturegeneration-function.md)和其他強式名稱函數使用，以表示公開金鑰/私密金鑰對的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="0f0b1-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f0b1-114">需求</span><span class="sxs-lookup"><span data-stu-id="0f0b1-114">Requirements</span></span>  
 <span data-ttu-id="0f0b1-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0f0b1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f0b1-116">**標題：** 強式名稱.h</span><span class="sxs-lookup"><span data-stu-id="0f0b1-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0f0b1-117">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="0f0b1-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0f0b1-118">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f0b1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f0b1-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f0b1-119">See also</span></span>

- [<span data-ttu-id="0f0b1-120">StrongNameGetPublicKey 函式</span><span class="sxs-lookup"><span data-stu-id="0f0b1-120">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="0f0b1-121">StrongNameSignatureGeneration 函式</span><span class="sxs-lookup"><span data-stu-id="0f0b1-121">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
