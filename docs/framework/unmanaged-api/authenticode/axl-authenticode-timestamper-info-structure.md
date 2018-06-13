---
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c89845008307e4cfb00d0f9b9a168a43ba5378c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402359"
---
# <a name="axlauthenticodetimestamperinfo-structure"></a><span data-ttu-id="c2fbb-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="c2fbb-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="c2fbb-103">定義 Authenticode 時間戳記程式資訊。</span><span class="sxs-lookup"><span data-stu-id="c2fbb-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2fbb-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2fbb-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="c2fbb-105">成員</span><span class="sxs-lookup"><span data-stu-id="c2fbb-105">Members</span></span>  
  
|<span data-ttu-id="c2fbb-106">成員</span><span class="sxs-lookup"><span data-stu-id="c2fbb-106">Member</span></span>|<span data-ttu-id="c2fbb-107">描述</span><span class="sxs-lookup"><span data-stu-id="c2fbb-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="c2fbb-108">此結構的大小。</span><span class="sxs-lookup"><span data-stu-id="c2fbb-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="c2fbb-109">錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c2fbb-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="c2fbb-110">雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="c2fbb-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="c2fbb-111">時間戳記的時間。</span><span class="sxs-lookup"><span data-stu-id="c2fbb-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="c2fbb-112">時間戳記程式的鏈結內容。</span><span class="sxs-lookup"><span data-stu-id="c2fbb-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="c2fbb-113">請參閱[CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx)結構。</span><span class="sxs-lookup"><span data-stu-id="c2fbb-113">See the [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2fbb-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2fbb-114">See Also</span></span>  
 [<span data-ttu-id="c2fbb-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="c2fbb-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
