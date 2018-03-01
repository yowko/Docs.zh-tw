---
title: "CloseAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 160ec53440f4ecdb924537c732a367881e75acf9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="closeassembly-method"></a><span data-ttu-id="c4c46-102">CloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="c4c46-102">CloseAssembly Method</span></span>
<span data-ttu-id="c4c46-103">完成組件作業。</span><span class="sxs-lookup"><span data-stu-id="c4c46-103">Finalizes assembly operations.</span></span> <span data-ttu-id="c4c46-104">開始新的組件或未繫結的模組之前呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="c4c46-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4c46-105">語法</span><span class="sxs-lookup"><span data-stu-id="c4c46-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c4c46-106">參數</span><span class="sxs-lookup"><span data-stu-id="c4c46-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c4c46-107">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c4c46-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4c46-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="c4c46-108">Return Value</span></span>  
 <span data-ttu-id="c4c46-109">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="c4c46-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4c46-110">需求</span><span class="sxs-lookup"><span data-stu-id="c4c46-110">Requirements</span></span>  
 <span data-ttu-id="c4c46-111">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="c4c46-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c46-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="c4c46-112">See Also</span></span>  
 [<span data-ttu-id="c4c46-113">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="c4c46-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="c4c46-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="c4c46-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="c4c46-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="c4c46-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
