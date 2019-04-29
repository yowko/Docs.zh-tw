---
title: ICLRStrongName2 介面
ms.date: 03/30/2017
api_name:
- ICLRStrongName2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName2
helpviewer_keywords:
- ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bf9e3d2df8f507e118b393007c3958358a830cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763720"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="185c9-102">ICLRStrongName2 介面</span><span class="sxs-lookup"><span data-stu-id="185c9-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="185c9-103">讓您能夠建立使用 sha-2 群組的安全雜湊演算法 （SHA-256、 SHA-384 和 SHA-512） 的強式名稱。</span><span class="sxs-lookup"><span data-stu-id="185c9-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="185c9-104">方法</span><span class="sxs-lookup"><span data-stu-id="185c9-104">Methods</span></span>  
  
|<span data-ttu-id="185c9-105">方法</span><span class="sxs-lookup"><span data-stu-id="185c9-105">Method</span></span>|<span data-ttu-id="185c9-106">描述</span><span class="sxs-lookup"><span data-stu-id="185c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="185c9-107">StrongNameGetPublicKeyEx 方法</span><span class="sxs-lookup"><span data-stu-id="185c9-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="185c9-108">公開/私密金鑰組，從取得的公開金鑰，並指定雜湊演算法和簽章演算法。</span><span class="sxs-lookup"><span data-stu-id="185c9-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="185c9-109">StrongNameSignatureVerificationEx2 方法</span><span class="sxs-lookup"><span data-stu-id="185c9-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="185c9-110">驗證強式名稱的組件中，簽章，並提供實際的索引鍵與 ECMA 索引鍵的對應。</span><span class="sxs-lookup"><span data-stu-id="185c9-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="185c9-111">備註</span><span class="sxs-lookup"><span data-stu-id="185c9-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="185c9-112">需求</span><span class="sxs-lookup"><span data-stu-id="185c9-112">Requirements</span></span>  
 <span data-ttu-id="185c9-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="185c9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="185c9-114">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="185c9-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="185c9-115">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="185c9-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="185c9-116">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="185c9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
