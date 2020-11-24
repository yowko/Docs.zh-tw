---
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
ms.openlocfilehash: b6852519da6cf4e12669aa2efa24862053adbc03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674238"
---
# <a name="axl_authenticode_timestamper_info-structure"></a><span data-ttu-id="8d351-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="8d351-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>

<span data-ttu-id="8d351-103">定義 Authenticode 時間戳記程式資訊。</span><span class="sxs-lookup"><span data-stu-id="8d351-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d351-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d351-104">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="8d351-105">成員</span><span class="sxs-lookup"><span data-stu-id="8d351-105">Members</span></span>  
  
|<span data-ttu-id="8d351-106">member</span><span class="sxs-lookup"><span data-stu-id="8d351-106">Member</span></span>|<span data-ttu-id="8d351-107">描述</span><span class="sxs-lookup"><span data-stu-id="8d351-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="8d351-108">此結構的大小。</span><span class="sxs-lookup"><span data-stu-id="8d351-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="8d351-109">錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8d351-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="8d351-110">雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="8d351-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="8d351-111">時間戳記的時間。</span><span class="sxs-lookup"><span data-stu-id="8d351-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="8d351-112">時間戳記程式的鏈結內容。</span><span class="sxs-lookup"><span data-stu-id="8d351-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="8d351-113">請參閱 [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) 結構。</span><span class="sxs-lookup"><span data-stu-id="8d351-113">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d351-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d351-114">See also</span></span>

- [<span data-ttu-id="8d351-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="8d351-115">Authenticode</span></span>](index.md)
