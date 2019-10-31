---
title: CertFreeAuthenticodeTimestamperInfo 函式
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
ms.openlocfilehash: 4f0806e0273b111e3398fb8f2884231b96cf1116
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099776"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="a4ce6-102">CertFreeAuthenticodeTimestamperInfo 函式</span><span class="sxs-lookup"><span data-stu-id="a4ce6-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="a4ce6-103">釋放配置給[AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md)結構的資源。</span><span class="sxs-lookup"><span data-stu-id="a4ce6-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4ce6-104">語法</span><span class="sxs-lookup"><span data-stu-id="a4ce6-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4ce6-105">參數</span><span class="sxs-lookup"><span data-stu-id="a4ce6-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="a4ce6-106">[in, out] 所要發行的時間戳記程式資訊。</span><span class="sxs-lookup"><span data-stu-id="a4ce6-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="a4ce6-107">請參閱[AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="a4ce6-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4ce6-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a4ce6-108">Return Value</span></span>  
 <span data-ttu-id="a4ce6-109">如果函式成功，會傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="a4ce6-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="a4ce6-110">否則會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="a4ce6-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4ce6-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="a4ce6-111">See also</span></span>

- [<span data-ttu-id="a4ce6-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="a4ce6-112">Authenticode</span></span>](index.md)
