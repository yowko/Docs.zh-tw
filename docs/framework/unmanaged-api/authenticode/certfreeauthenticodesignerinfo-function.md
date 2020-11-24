---
title: CertFreeAuthenticodeSignerInfo 函式
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
ms.openlocfilehash: dc6bb5a137a50ec07f89f292e5d9beac4349c3c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674173"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="6af7b-102">CertFreeAuthenticodeSignerInfo 函式</span><span class="sxs-lookup"><span data-stu-id="6af7b-102">CertFreeAuthenticodeSignerInfo Function</span></span>

<span data-ttu-id="6af7b-103">釋出配置給 [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) 結構的資源。</span><span class="sxs-lookup"><span data-stu-id="6af7b-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6af7b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6af7b-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6af7b-105">參數</span><span class="sxs-lookup"><span data-stu-id="6af7b-105">Parameters</span></span>  

 `pSignerInfo`  
 <span data-ttu-id="6af7b-106">[in, out] 所要發行的簽署人資訊。</span><span class="sxs-lookup"><span data-stu-id="6af7b-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="6af7b-107">請參閱 [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) 結構。</span><span class="sxs-lookup"><span data-stu-id="6af7b-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6af7b-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="6af7b-108">Return Value</span></span>  

 <span data-ttu-id="6af7b-109">如果函式成功，會傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="6af7b-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="6af7b-110">否則會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="6af7b-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af7b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6af7b-111">See also</span></span>

- [<span data-ttu-id="6af7b-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="6af7b-112">Authenticode</span></span>](index.md)
