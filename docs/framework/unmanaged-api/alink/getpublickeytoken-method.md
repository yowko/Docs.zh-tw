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
ms.openlocfilehash: 2e7ed4e1529104db30b0b06665f74342d9ca9a01
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447238"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="87e64-102">GetPublicKeyToken 方法</span><span class="sxs-lookup"><span data-stu-id="87e64-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="87e64-103">抓取指定的 keyfile 或金鑰容器的公開金鑰 token。</span><span class="sxs-lookup"><span data-stu-id="87e64-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e64-104">語法</span><span class="sxs-lookup"><span data-stu-id="87e64-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="87e64-105">參數</span><span class="sxs-lookup"><span data-stu-id="87e64-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="87e64-106">金鑰的檔案名。</span><span class="sxs-lookup"><span data-stu-id="87e64-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="87e64-107">金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="87e64-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="87e64-108">要儲存金鑰 token 的位址。</span><span class="sxs-lookup"><span data-stu-id="87e64-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="87e64-109">指定 `pvPublicKeyToken`所指示的緩衝區大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="87e64-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="87e64-110">傳回時，包含實際使用的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="87e64-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87e64-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="87e64-111">Return Value</span></span>  
 <span data-ttu-id="87e64-112">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="87e64-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87e64-113">需求</span><span class="sxs-lookup"><span data-stu-id="87e64-113">Requirements</span></span>  
 <span data-ttu-id="87e64-114">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="87e64-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e64-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87e64-115">See also</span></span>

- [<span data-ttu-id="87e64-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="87e64-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="87e64-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="87e64-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="87e64-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="87e64-118">ALink API</span></span>](index.md)
