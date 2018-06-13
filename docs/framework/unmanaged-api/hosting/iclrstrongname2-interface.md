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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432969"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="bf58f-102">ICLRStrongName2 介面</span><span class="sxs-lookup"><span data-stu-id="bf58f-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="bf58f-103">提供建立強式名稱使用 sha-2 群組 （sha-256、 sha-384 和 sha-512） 的安全雜湊演算法的能力。</span><span class="sxs-lookup"><span data-stu-id="bf58f-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf58f-104">方法</span><span class="sxs-lookup"><span data-stu-id="bf58f-104">Methods</span></span>  
  
|<span data-ttu-id="bf58f-105">方法</span><span class="sxs-lookup"><span data-stu-id="bf58f-105">Method</span></span>|<span data-ttu-id="bf58f-106">描述</span><span class="sxs-lookup"><span data-stu-id="bf58f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bf58f-107">StrongNameGetPublicKeyEx 方法</span><span class="sxs-lookup"><span data-stu-id="bf58f-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="bf58f-108">公開/私密金鑰組，從取得的公開金鑰，並指定雜湊演算法和簽章演算法。</span><span class="sxs-lookup"><span data-stu-id="bf58f-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="bf58f-109">StrongNameSignatureVerificationEx2 方法</span><span class="sxs-lookup"><span data-stu-id="bf58f-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="bf58f-110">驗證簽章是強式名稱組件，並提供從 ECMA 金鑰對應至實際的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="bf58f-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf58f-111">備註</span><span class="sxs-lookup"><span data-stu-id="bf58f-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf58f-112">需求</span><span class="sxs-lookup"><span data-stu-id="bf58f-112">Requirements</span></span>  
 <span data-ttu-id="bf58f-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bf58f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf58f-114">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="bf58f-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bf58f-115">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bf58f-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf58f-116">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf58f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
