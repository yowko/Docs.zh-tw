---
title: "AXL_AUTHENTICODE_SIGNER_INFO 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c53ca8073adda5cba497e9f45404024435cc161f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="96b3d-102">AXL_AUTHENTICODE_SIGNER_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="96b3d-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="96b3d-103">定義 Authenticode 簽署人資訊。</span><span class="sxs-lookup"><span data-stu-id="96b3d-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b3d-104">語法</span><span class="sxs-lookup"><span data-stu-id="96b3d-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    LPCWSTR pwszHash  
    LPCWSTR pwszDescription;  
    LPCWSTR pwszDescriptionUrl;  
    PCCERT_CHAIN_CONTEXT pChainContext  
} AXL_AUTHENTICODE_SIGNER_INFO, * PAXL_AUTHENTICODE_SIGNER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="96b3d-105">成員</span><span class="sxs-lookup"><span data-stu-id="96b3d-105">Members</span></span>  
  
|<span data-ttu-id="96b3d-106">成員</span><span class="sxs-lookup"><span data-stu-id="96b3d-106">Member</span></span>|<span data-ttu-id="96b3d-107">描述</span><span class="sxs-lookup"><span data-stu-id="96b3d-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="96b3d-108">此結構的大小。</span><span class="sxs-lookup"><span data-stu-id="96b3d-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="96b3d-109">錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="96b3d-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="96b3d-110">雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="96b3d-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="96b3d-111">雜湊。</span><span class="sxs-lookup"><span data-stu-id="96b3d-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="96b3d-112">描述。</span><span class="sxs-lookup"><span data-stu-id="96b3d-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="96b3d-113">描述的 URL。</span><span class="sxs-lookup"><span data-stu-id="96b3d-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="96b3d-114">簽署人的鏈結內容。</span><span class="sxs-lookup"><span data-stu-id="96b3d-114">The chain context of the signer.</span></span> <span data-ttu-id="96b3d-115">請參閱[CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx)結構。</span><span class="sxs-lookup"><span data-stu-id="96b3d-115">See the [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96b3d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96b3d-116">See Also</span></span>  
 [<span data-ttu-id="96b3d-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="96b3d-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
