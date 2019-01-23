---
title: CloseAssembly 方法
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa415926f4a818f697812f1a3c5531cb0ab7081b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510165"
---
# <a name="closeassembly-method"></a><span data-ttu-id="85b5d-102">CloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="85b5d-102">CloseAssembly Method</span></span>
<span data-ttu-id="85b5d-103">完成組件作業。</span><span class="sxs-lookup"><span data-stu-id="85b5d-103">Finalizes assembly operations.</span></span> <span data-ttu-id="85b5d-104">開始新的組件或未繫結的模組之前呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="85b5d-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85b5d-105">語法</span><span class="sxs-lookup"><span data-stu-id="85b5d-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85b5d-106">參數</span><span class="sxs-lookup"><span data-stu-id="85b5d-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="85b5d-107">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="85b5d-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85b5d-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="85b5d-108">Return Value</span></span>  
 <span data-ttu-id="85b5d-109">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="85b5d-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85b5d-110">需求</span><span class="sxs-lookup"><span data-stu-id="85b5d-110">Requirements</span></span>  
 <span data-ttu-id="85b5d-111">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="85b5d-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85b5d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85b5d-112">See also</span></span>
- [<span data-ttu-id="85b5d-113">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="85b5d-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="85b5d-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="85b5d-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="85b5d-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="85b5d-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
