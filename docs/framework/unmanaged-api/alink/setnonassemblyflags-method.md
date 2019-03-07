---
title: SetNonAssemblyFlags 方法
ms.date: 03/30/2017
api_name:
- IALink.SetNonAssemblyFlags
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetNonAssemblyFlags
helpviewer_keywords:
- SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d6c07a6679326548535985e4c938c3fddbb2a0cf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500209"
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="9160e-102">SetNonAssemblyFlags 方法</span><span class="sxs-lookup"><span data-stu-id="9160e-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="9160e-103">設定不是組件特定的旗標。</span><span class="sxs-lookup"><span data-stu-id="9160e-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9160e-104">語法</span><span class="sxs-lookup"><span data-stu-id="9160e-104">Syntax</span></span>  
  
```  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9160e-105">參數</span><span class="sxs-lookup"><span data-stu-id="9160e-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="9160e-106">ALink 旗標。</span><span class="sxs-lookup"><span data-stu-id="9160e-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9160e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="9160e-107">Return Value</span></span>  
 <span data-ttu-id="9160e-108">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="9160e-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9160e-109">需求</span><span class="sxs-lookup"><span data-stu-id="9160e-109">Requirements</span></span>  
 <span data-ttu-id="9160e-110">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="9160e-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9160e-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9160e-111">See also</span></span>
- [<span data-ttu-id="9160e-112">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="9160e-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="9160e-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="9160e-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="9160e-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="9160e-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
