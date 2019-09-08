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
ms.openlocfilehash: 158ecc036d56e2ad9a3fa650677c04ebcbfd7696
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777221"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="a8f02-102">GetPublicKeyToken 方法</span><span class="sxs-lookup"><span data-stu-id="a8f02-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="a8f02-103">抓取指定的 keyfile 或金鑰容器的公開金鑰 token。</span><span class="sxs-lookup"><span data-stu-id="a8f02-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8f02-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8f02-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8f02-105">參數</span><span class="sxs-lookup"><span data-stu-id="a8f02-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="a8f02-106">金鑰的檔案名。</span><span class="sxs-lookup"><span data-stu-id="a8f02-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="a8f02-107">金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="a8f02-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="a8f02-108">要儲存金鑰 token 的位址。</span><span class="sxs-lookup"><span data-stu-id="a8f02-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="a8f02-109">指定所指示`pvPublicKeyToken`的緩衝區大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="a8f02-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="a8f02-110">傳回時，包含實際使用的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a8f02-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8f02-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="a8f02-111">Return Value</span></span>  
 <span data-ttu-id="a8f02-112">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="a8f02-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8f02-113">需求</span><span class="sxs-lookup"><span data-stu-id="a8f02-113">Requirements</span></span>  
 <span data-ttu-id="a8f02-114">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="a8f02-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8f02-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8f02-115">See also</span></span>

- [<span data-ttu-id="a8f02-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="a8f02-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a8f02-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="a8f02-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a8f02-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="a8f02-118">ALink API</span></span>](index.md)
