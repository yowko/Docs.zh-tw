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
ms.openlocfilehash: e41be6407076a2609a83a5be3b0c42d28914ec38
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720338"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="fdec5-102">GetPublicKeyToken 方法</span><span class="sxs-lookup"><span data-stu-id="fdec5-102">GetPublicKeyToken Method</span></span>

<span data-ttu-id="fdec5-103">抓取給定 keyfile 或金鑰容器的公開金鑰 token。</span><span class="sxs-lookup"><span data-stu-id="fdec5-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdec5-104">語法</span><span class="sxs-lookup"><span data-stu-id="fdec5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdec5-105">參數</span><span class="sxs-lookup"><span data-stu-id="fdec5-105">Parameters</span></span>  

 `pszKeyFile`  
 <span data-ttu-id="fdec5-106">金鑰的檔案名。</span><span class="sxs-lookup"><span data-stu-id="fdec5-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="fdec5-107">金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="fdec5-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="fdec5-108">要儲存金鑰權杖的位址。</span><span class="sxs-lookup"><span data-stu-id="fdec5-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="fdec5-109">指定所表示之緩衝區的大小（以位元組為單位） `pvPublicKeyToken` 。</span><span class="sxs-lookup"><span data-stu-id="fdec5-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="fdec5-110">傳回時，包含實際使用的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="fdec5-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fdec5-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="fdec5-111">Return Value</span></span>  

 <span data-ttu-id="fdec5-112">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="fdec5-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdec5-113">需求</span><span class="sxs-lookup"><span data-stu-id="fdec5-113">Requirements</span></span>  

 <span data-ttu-id="fdec5-114">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="fdec5-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdec5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fdec5-115">See also</span></span>

- [<span data-ttu-id="fdec5-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="fdec5-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="fdec5-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="fdec5-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="fdec5-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="fdec5-118">ALink API</span></span>](index.md)
