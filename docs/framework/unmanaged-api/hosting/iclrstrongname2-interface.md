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
ms.openlocfilehash: df570f32d694ec21e9642e75b4965e169afaccfc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677644"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="64947-102">ICLRStrongName2 介面</span><span class="sxs-lookup"><span data-stu-id="64947-102">ICLRStrongName2 Interface</span></span>

<span data-ttu-id="64947-103">提供使用安全雜湊演算法的 SHA-1 群組來建立強式名稱的功能， (SHA-256、SHA-384 和 SHA-512) 。</span><span class="sxs-lookup"><span data-stu-id="64947-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="64947-104">方法</span><span class="sxs-lookup"><span data-stu-id="64947-104">Methods</span></span>  
  
|<span data-ttu-id="64947-105">方法</span><span class="sxs-lookup"><span data-stu-id="64947-105">Method</span></span>|<span data-ttu-id="64947-106">描述</span><span class="sxs-lookup"><span data-stu-id="64947-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64947-107">StrongNameGetPublicKeyEx 方法</span><span class="sxs-lookup"><span data-stu-id="64947-107">StrongNameGetPublicKeyEx Method</span></span>](strongnamegetpublickeyex-method.md)|<span data-ttu-id="64947-108">從公開/私密金鑰組取得公開金鑰，並指定雜湊演算法和簽章演算法。</span><span class="sxs-lookup"><span data-stu-id="64947-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="64947-109">StrongNameSignatureVerificationEx2 方法</span><span class="sxs-lookup"><span data-stu-id="64947-109">StrongNameSignatureVerificationEx2 Method</span></span>](strongnamesignatureverificationex2-method.md)|<span data-ttu-id="64947-110">驗證強式名稱元件的簽章，並提供從 ECMA 金鑰到實際金鑰的對應。</span><span class="sxs-lookup"><span data-stu-id="64947-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64947-111">備註</span><span class="sxs-lookup"><span data-stu-id="64947-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64947-112">需求</span><span class="sxs-lookup"><span data-stu-id="64947-112">Requirements</span></span>  

 <span data-ttu-id="64947-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="64947-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64947-114">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="64947-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="64947-115">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="64947-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64947-116">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64947-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
