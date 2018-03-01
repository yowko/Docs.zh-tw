---
title: "EmitAssembly 方法"
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
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f012ea89fec0e64bc1639e6c47fb79249c25411a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="emitassembly-method"></a><span data-ttu-id="f10d0-102">EmitAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="f10d0-102">EmitAssembly Method</span></span>
<span data-ttu-id="f10d0-103">建立組件。</span><span class="sxs-lookup"><span data-stu-id="f10d0-103">Creates the assembly.</span></span> <span data-ttu-id="f10d0-104">其他所有檔案都已都關閉的組件檔案除外之後呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="f10d0-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="f10d0-105">產生未繫結的模組時，請勿呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="f10d0-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f10d0-106">語法</span><span class="sxs-lookup"><span data-stu-id="f10d0-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f10d0-107">參數</span><span class="sxs-lookup"><span data-stu-id="f10d0-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f10d0-108">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f10d0-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f10d0-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="f10d0-109">Return Value</span></span>  
 <span data-ttu-id="f10d0-110">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="f10d0-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f10d0-111">需求</span><span class="sxs-lookup"><span data-stu-id="f10d0-111">Requirements</span></span>  
 <span data-ttu-id="f10d0-112">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="f10d0-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f10d0-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="f10d0-113">See Also</span></span>  
 [<span data-ttu-id="f10d0-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="f10d0-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f10d0-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="f10d0-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f10d0-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="f10d0-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
