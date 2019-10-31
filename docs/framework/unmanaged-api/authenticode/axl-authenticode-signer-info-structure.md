---
title: AXL_AUTHENTICODE_SIGNER_INFO 結構
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
ms.openlocfilehash: 00132bb378d69c0db9fe9d762407707346238917
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132518"
---
# <a name="axl_authenticode_signer_info-structure"></a><span data-ttu-id="156ef-102">AXL_AUTHENTICODE_SIGNER_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="156ef-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="156ef-103">定義 Authenticode 簽署人資訊。</span><span class="sxs-lookup"><span data-stu-id="156ef-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="156ef-104">語法</span><span class="sxs-lookup"><span data-stu-id="156ef-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="156ef-105">Members</span><span class="sxs-lookup"><span data-stu-id="156ef-105">Members</span></span>  
  
|<span data-ttu-id="156ef-106">成員</span><span class="sxs-lookup"><span data-stu-id="156ef-106">Member</span></span>|<span data-ttu-id="156ef-107">描述</span><span class="sxs-lookup"><span data-stu-id="156ef-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="156ef-108">此結構的大小。</span><span class="sxs-lookup"><span data-stu-id="156ef-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="156ef-109">錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="156ef-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="156ef-110">雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="156ef-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="156ef-111">雜湊。</span><span class="sxs-lookup"><span data-stu-id="156ef-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="156ef-112">描述。</span><span class="sxs-lookup"><span data-stu-id="156ef-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="156ef-113">描述的 URL。</span><span class="sxs-lookup"><span data-stu-id="156ef-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="156ef-114">簽署人的鏈結內容。</span><span class="sxs-lookup"><span data-stu-id="156ef-114">The chain context of the signer.</span></span> <span data-ttu-id="156ef-115">請參閱[CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context)結構。</span><span class="sxs-lookup"><span data-stu-id="156ef-115">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="156ef-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="156ef-116">See also</span></span>

- [<span data-ttu-id="156ef-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="156ef-117">Authenticode</span></span>](index.md)
