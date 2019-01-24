---
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8060e95f06fd53ca985f84666cc81cfe49394fc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659653"
---
# <a name="axlauthenticodetimestamperinfo-structure"></a><span data-ttu-id="3341e-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="3341e-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="3341e-103">定義 Authenticode 時間戳記程式資訊。</span><span class="sxs-lookup"><span data-stu-id="3341e-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3341e-104">語法</span><span class="sxs-lookup"><span data-stu-id="3341e-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="3341e-105">成員</span><span class="sxs-lookup"><span data-stu-id="3341e-105">Members</span></span>  
  
|<span data-ttu-id="3341e-106">成員</span><span class="sxs-lookup"><span data-stu-id="3341e-106">Member</span></span>|<span data-ttu-id="3341e-107">描述</span><span class="sxs-lookup"><span data-stu-id="3341e-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="3341e-108">此結構的大小。</span><span class="sxs-lookup"><span data-stu-id="3341e-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="3341e-109">錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="3341e-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="3341e-110">雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="3341e-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="3341e-111">時間戳記的時間。</span><span class="sxs-lookup"><span data-stu-id="3341e-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="3341e-112">時間戳記程式的鏈結內容。</span><span class="sxs-lookup"><span data-stu-id="3341e-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="3341e-113">請參閱[CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context)結構。</span><span class="sxs-lookup"><span data-stu-id="3341e-113">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3341e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3341e-114">See also</span></span>
- [<span data-ttu-id="3341e-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="3341e-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
