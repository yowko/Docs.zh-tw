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
ms.openlocfilehash: c89fd080e61db78ed21c03c2aa63c97337c09585
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497544"
---
# <a name="closeassembly-method"></a><span data-ttu-id="e6ae5-102">CloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="e6ae5-102">CloseAssembly Method</span></span>
<span data-ttu-id="e6ae5-103">完成組件作業。</span><span class="sxs-lookup"><span data-stu-id="e6ae5-103">Finalizes assembly operations.</span></span> <span data-ttu-id="e6ae5-104">開始新的組件或未繫結的模組之前呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="e6ae5-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6ae5-105">語法</span><span class="sxs-lookup"><span data-stu-id="e6ae5-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6ae5-106">參數</span><span class="sxs-lookup"><span data-stu-id="e6ae5-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e6ae5-107">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e6ae5-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6ae5-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e6ae5-108">Return Value</span></span>  
 <span data-ttu-id="e6ae5-109">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="e6ae5-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6ae5-110">需求</span><span class="sxs-lookup"><span data-stu-id="e6ae5-110">Requirements</span></span>  
 <span data-ttu-id="e6ae5-111">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="e6ae5-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6ae5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6ae5-112">See also</span></span>
- [<span data-ttu-id="e6ae5-113">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="e6ae5-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="e6ae5-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="e6ae5-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="e6ae5-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="e6ae5-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
