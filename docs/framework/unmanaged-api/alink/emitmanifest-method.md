---
title: "EmitManifest 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EmitManifest
- IALink.EmitManifest
api_location: alink.dll
api_type: COM
f1_keywords: EmitManifest
helpviewer_keywords: EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11966eccfdbbdbab29d305915afd904a54f9c57b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="emitmanifest-method"></a><span data-ttu-id="8dc62-102">EmitManifest 方法</span><span class="sxs-lookup"><span data-stu-id="8dc62-102">EmitManifest Method</span></span>
<span data-ttu-id="8dc62-103">發出的最後一個資訊清單。</span><span class="sxs-lookup"><span data-stu-id="8dc62-103">Emits the final manifest.</span></span> <span data-ttu-id="8dc62-104">匯入所有其他檔案，並設定所有選項之後呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="8dc62-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="8dc62-105">請勿呼叫這個方法未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="8dc62-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dc62-106">語法</span><span class="sxs-lookup"><span data-stu-id="8dc62-106">Syntax</span></span>  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8dc62-107">參數</span><span class="sxs-lookup"><span data-stu-id="8dc62-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8dc62-108">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="8dc62-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="8dc62-109">要保留在組件檔案中，從擷取大小[StrongNameSignatureSize 函式](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)。</span><span class="sxs-lookup"><span data-stu-id="8dc62-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="8dc62-110">選擇性地接收組件資訊清單語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8dc62-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8dc62-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="8dc62-111">Return Value</span></span>  
 <span data-ttu-id="8dc62-112">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="8dc62-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dc62-113">需求</span><span class="sxs-lookup"><span data-stu-id="8dc62-113">Requirements</span></span>  
 <span data-ttu-id="8dc62-114">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="8dc62-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dc62-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="8dc62-115">See Also</span></span>  
 [<span data-ttu-id="8dc62-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="8dc62-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="8dc62-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="8dc62-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="8dc62-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="8dc62-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
