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
ms.openlocfilehash: 1ef71b14faf66c179030dff2a7d953e27463c1f7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674160"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="ed07b-102">CertFreeAuthenticodeTimestamperInfo 函式</span><span class="sxs-lookup"><span data-stu-id="ed07b-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>

<span data-ttu-id="ed07b-103">釋出配置給 [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) 結構的資源。</span><span class="sxs-lookup"><span data-stu-id="ed07b-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed07b-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed07b-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed07b-105">參數</span><span class="sxs-lookup"><span data-stu-id="ed07b-105">Parameters</span></span>  

 `pTimestamperInfo`  
 <span data-ttu-id="ed07b-106">[in, out] 所要發行的時間戳記程式資訊。</span><span class="sxs-lookup"><span data-stu-id="ed07b-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="ed07b-107">請參閱 [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) 結構。</span><span class="sxs-lookup"><span data-stu-id="ed07b-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed07b-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="ed07b-108">Return Value</span></span>  

 <span data-ttu-id="ed07b-109">如果函式成功，會傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="ed07b-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="ed07b-110">否則會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ed07b-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed07b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed07b-111">See also</span></span>

- [<span data-ttu-id="ed07b-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="ed07b-112">Authenticode</span></span>](index.md)
