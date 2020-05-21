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
ms.openlocfilehash: 9715369f4cf1b2a7078be14a2fc597f735ab6fd3
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763159"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="ccc55-102">ICLRStrongName2 介面</span><span class="sxs-lookup"><span data-stu-id="ccc55-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="ccc55-103">提供使用 SHA-2 安全雜湊演算法（SHA-256、SHA-384 和 SHA-512）群組建立強式名稱的功能。</span><span class="sxs-lookup"><span data-stu-id="ccc55-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ccc55-104">方法</span><span class="sxs-lookup"><span data-stu-id="ccc55-104">Methods</span></span>  
  
|<span data-ttu-id="ccc55-105">方法</span><span class="sxs-lookup"><span data-stu-id="ccc55-105">Method</span></span>|<span data-ttu-id="ccc55-106">描述</span><span class="sxs-lookup"><span data-stu-id="ccc55-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ccc55-107">StrongNameGetPublicKeyEx 方法</span><span class="sxs-lookup"><span data-stu-id="ccc55-107">StrongNameGetPublicKeyEx Method</span></span>](strongnamegetpublickeyex-method.md)|<span data-ttu-id="ccc55-108">從公開/私密金鑰組取得公開金鑰，並指定雜湊演算法和簽章演算法。</span><span class="sxs-lookup"><span data-stu-id="ccc55-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="ccc55-109">StrongNameSignatureVerificationEx2 方法</span><span class="sxs-lookup"><span data-stu-id="ccc55-109">StrongNameSignatureVerificationEx2 Method</span></span>](strongnamesignatureverificationex2-method.md)|<span data-ttu-id="ccc55-110">驗證強式名稱元件的簽章，並提供從 ECMA 金鑰到實際金鑰的對應。</span><span class="sxs-lookup"><span data-stu-id="ccc55-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccc55-111">備註</span><span class="sxs-lookup"><span data-stu-id="ccc55-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccc55-112">需求</span><span class="sxs-lookup"><span data-stu-id="ccc55-112">Requirements</span></span>  
 <span data-ttu-id="ccc55-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ccc55-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccc55-114">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="ccc55-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ccc55-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ccc55-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ccc55-116">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccc55-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
