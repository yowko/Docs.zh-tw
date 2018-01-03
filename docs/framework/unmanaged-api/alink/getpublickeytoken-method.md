---
title: "GetPublicKeyToken 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.GetPublicKeyToken
api_location: alink.dll
api_type: COM
f1_keywords: GetPublicKeyToken
helpviewer_keywords: GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 230c98e85bd0aa3bd2f368965b6f7ac028e43df4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="83091-102">GetPublicKeyToken 方法</span><span class="sxs-lookup"><span data-stu-id="83091-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="83091-103">擷取指定的 keyfile 或金鑰容器的公用金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="83091-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83091-104">語法</span><span class="sxs-lookup"><span data-stu-id="83091-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83091-105">參數</span><span class="sxs-lookup"><span data-stu-id="83091-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="83091-106">金鑰的檔名。</span><span class="sxs-lookup"><span data-stu-id="83091-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="83091-107">金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="83091-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="83091-108">儲存語彙基元的位址。</span><span class="sxs-lookup"><span data-stu-id="83091-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="83091-109">指定的大小，以位元組為單位，所指定的緩衝區`pvPublicKeyToken`。</span><span class="sxs-lookup"><span data-stu-id="83091-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="83091-110">傳回時，包含實際使用的位元組的數目。</span><span class="sxs-lookup"><span data-stu-id="83091-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83091-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="83091-111">Return Value</span></span>  
 <span data-ttu-id="83091-112">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="83091-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83091-113">需求</span><span class="sxs-lookup"><span data-stu-id="83091-113">Requirements</span></span>  
 <span data-ttu-id="83091-114">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="83091-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83091-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="83091-115">See Also</span></span>  
 [<span data-ttu-id="83091-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="83091-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="83091-117">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="83091-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="83091-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="83091-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
