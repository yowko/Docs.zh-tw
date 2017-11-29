---
title: "EmitAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location: alink.dll
api_type: COM
f1_keywords: EmitAssembly
helpviewer_keywords: EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3471c4ad2d06443e0f05dc344be5f791817f2d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="emitassembly-method"></a><span data-ttu-id="1e418-102">EmitAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="1e418-102">EmitAssembly Method</span></span>
<span data-ttu-id="1e418-103">建立組件。</span><span class="sxs-lookup"><span data-stu-id="1e418-103">Creates the assembly.</span></span> <span data-ttu-id="1e418-104">其他所有檔案都已都關閉的組件檔案除外之後呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="1e418-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="1e418-105">產生未繫結的模組時，請勿呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="1e418-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e418-106">語法</span><span class="sxs-lookup"><span data-stu-id="1e418-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1e418-107">參數</span><span class="sxs-lookup"><span data-stu-id="1e418-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1e418-108">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1e418-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e418-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="1e418-109">Return Value</span></span>  
 <span data-ttu-id="1e418-110">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="1e418-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e418-111">需求</span><span class="sxs-lookup"><span data-stu-id="1e418-111">Requirements</span></span>  
 <span data-ttu-id="1e418-112">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="1e418-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e418-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e418-113">See Also</span></span>  
 [<span data-ttu-id="1e418-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="1e418-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="1e418-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="1e418-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="1e418-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="1e418-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
