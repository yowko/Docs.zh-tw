---
title: GetPublicKeyToken 方法
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec2c357cd56670f4f2deed8023bed7842a7f4ed7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741880"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="704f1-102">GetPublicKeyToken 方法</span><span class="sxs-lookup"><span data-stu-id="704f1-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="704f1-103">擷取指定的金鑰檔或金鑰容器的公用金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="704f1-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="704f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="704f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="704f1-105">參數</span><span class="sxs-lookup"><span data-stu-id="704f1-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="704f1-106">金鑰的檔名。</span><span class="sxs-lookup"><span data-stu-id="704f1-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="704f1-107">金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="704f1-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="704f1-108">語彙基元儲存所在的位址。</span><span class="sxs-lookup"><span data-stu-id="704f1-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="704f1-109">指定的大小，以位元組為單位所指定的緩衝區`pvPublicKeyToken`。</span><span class="sxs-lookup"><span data-stu-id="704f1-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="704f1-110">傳回時，包含實際使用的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="704f1-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="704f1-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="704f1-111">Return Value</span></span>  
 <span data-ttu-id="704f1-112">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="704f1-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="704f1-113">需求</span><span class="sxs-lookup"><span data-stu-id="704f1-113">Requirements</span></span>  
 <span data-ttu-id="704f1-114">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="704f1-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="704f1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="704f1-115">See also</span></span>

- [<span data-ttu-id="704f1-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="704f1-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="704f1-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="704f1-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="704f1-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="704f1-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
