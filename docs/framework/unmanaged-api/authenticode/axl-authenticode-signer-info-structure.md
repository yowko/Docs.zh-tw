---
title: AXL_AUTHENTICODE_SIGNER_INFO 結構
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
ms.openlocfilehash: 1bb6df4aa82f8dfc367083732af2065aba9d07b1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679984"
---
# <a name="axl_authenticode_signer_info-structure"></a><span data-ttu-id="e71e1-102">AXL_AUTHENTICODE_SIGNER_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="e71e1-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>

<span data-ttu-id="e71e1-103">定義 Authenticode 簽署人資訊。</span><span class="sxs-lookup"><span data-stu-id="e71e1-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e71e1-104">語法</span><span class="sxs-lookup"><span data-stu-id="e71e1-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="e71e1-105">成員</span><span class="sxs-lookup"><span data-stu-id="e71e1-105">Members</span></span>  
  
|<span data-ttu-id="e71e1-106">member</span><span class="sxs-lookup"><span data-stu-id="e71e1-106">Member</span></span>|<span data-ttu-id="e71e1-107">描述</span><span class="sxs-lookup"><span data-stu-id="e71e1-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="e71e1-108">此結構的大小。</span><span class="sxs-lookup"><span data-stu-id="e71e1-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="e71e1-109">錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e71e1-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="e71e1-110">雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="e71e1-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="e71e1-111">雜湊。</span><span class="sxs-lookup"><span data-stu-id="e71e1-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="e71e1-112">描述。</span><span class="sxs-lookup"><span data-stu-id="e71e1-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="e71e1-113">描述的 URL。</span><span class="sxs-lookup"><span data-stu-id="e71e1-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="e71e1-114">簽署人的鏈結內容。</span><span class="sxs-lookup"><span data-stu-id="e71e1-114">The chain context of the signer.</span></span> <span data-ttu-id="e71e1-115">請參閱 [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) 結構。</span><span class="sxs-lookup"><span data-stu-id="e71e1-115">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e71e1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e71e1-116">See also</span></span>

- [<span data-ttu-id="e71e1-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="e71e1-117">Authenticode</span></span>](index.md)
