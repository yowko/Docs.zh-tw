---
title: AXL_AUTHENTICODE_SIGNER_INFO 結構
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff50ee18dc3155bf784d6b752da8efc841aa6ce5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559433"
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="b6abc-102">AXL_AUTHENTICODE_SIGNER_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="b6abc-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="b6abc-103">定義 Authenticode 簽署人資訊。</span><span class="sxs-lookup"><span data-stu-id="b6abc-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6abc-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6abc-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b6abc-105">成員</span><span class="sxs-lookup"><span data-stu-id="b6abc-105">Members</span></span>  
  
|<span data-ttu-id="b6abc-106">成員</span><span class="sxs-lookup"><span data-stu-id="b6abc-106">Member</span></span>|<span data-ttu-id="b6abc-107">描述</span><span class="sxs-lookup"><span data-stu-id="b6abc-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="b6abc-108">此結構的大小。</span><span class="sxs-lookup"><span data-stu-id="b6abc-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="b6abc-109">錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="b6abc-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="b6abc-110">雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="b6abc-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="b6abc-111">雜湊。</span><span class="sxs-lookup"><span data-stu-id="b6abc-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="b6abc-112">描述。</span><span class="sxs-lookup"><span data-stu-id="b6abc-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="b6abc-113">描述的 URL。</span><span class="sxs-lookup"><span data-stu-id="b6abc-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="b6abc-114">簽署人的鏈結內容。</span><span class="sxs-lookup"><span data-stu-id="b6abc-114">The chain context of the signer.</span></span> <span data-ttu-id="b6abc-115">請參閱[CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context)結構。</span><span class="sxs-lookup"><span data-stu-id="b6abc-115">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6abc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6abc-116">See also</span></span>
- [<span data-ttu-id="b6abc-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="b6abc-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
