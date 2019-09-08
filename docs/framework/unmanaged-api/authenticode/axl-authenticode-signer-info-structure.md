---
title: AXL_AUTHENTICODE_SIGNER_INFO 結構
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9aaa0258b53b6b39874c8c99c71ecf53cbdb8f97
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787073"
---
# <a name="axl_authenticode_signer_info-structure"></a><span data-ttu-id="ef66e-102">AXL_AUTHENTICODE_SIGNER_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="ef66e-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="ef66e-103">定義 Authenticode 簽署人資訊。</span><span class="sxs-lookup"><span data-stu-id="ef66e-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef66e-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef66e-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="ef66e-105">成員</span><span class="sxs-lookup"><span data-stu-id="ef66e-105">Members</span></span>  
  
|<span data-ttu-id="ef66e-106">成員</span><span class="sxs-lookup"><span data-stu-id="ef66e-106">Member</span></span>|<span data-ttu-id="ef66e-107">描述</span><span class="sxs-lookup"><span data-stu-id="ef66e-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="ef66e-108">此結構的大小。</span><span class="sxs-lookup"><span data-stu-id="ef66e-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="ef66e-109">錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ef66e-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="ef66e-110">雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="ef66e-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="ef66e-111">雜湊。</span><span class="sxs-lookup"><span data-stu-id="ef66e-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="ef66e-112">描述。</span><span class="sxs-lookup"><span data-stu-id="ef66e-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="ef66e-113">描述的 URL。</span><span class="sxs-lookup"><span data-stu-id="ef66e-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="ef66e-114">簽署人的鏈結內容。</span><span class="sxs-lookup"><span data-stu-id="ef66e-114">The chain context of the signer.</span></span> <span data-ttu-id="ef66e-115">請參閱[CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context)結構。</span><span class="sxs-lookup"><span data-stu-id="ef66e-115">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef66e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef66e-116">See also</span></span>

- [<span data-ttu-id="ef66e-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="ef66e-117">Authenticode</span></span>](index.md)
