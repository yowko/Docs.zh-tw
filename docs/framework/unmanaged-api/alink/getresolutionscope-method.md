---
title: "GetResolutionScope 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetResolutionScope
api_location: alink.dll
api_type: COM
f1_keywords: GetResolutionScope
helpviewer_keywords: GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9dc63a7165ab472e973e0bc4f3e4cbb99e5d828
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="19055-102">GetResolutionScope 方法</span><span class="sxs-lookup"><span data-stu-id="19055-102">GetResolutionScope Method</span></span>
<span data-ttu-id="19055-103">擷取給定類型的範圍。</span><span class="sxs-lookup"><span data-stu-id="19055-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19055-104">語法</span><span class="sxs-lookup"><span data-stu-id="19055-104">Syntax</span></span>  
  
```  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19055-105">參數</span><span class="sxs-lookup"><span data-stu-id="19055-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="19055-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="19055-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="19055-107">需要參考的檔案。</span><span class="sxs-lookup"><span data-stu-id="19055-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="19055-108">檔案的語彙基元的類型定義中，通常是擷取[ImportFile 方法](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)。</span><span class="sxs-lookup"><span data-stu-id="19055-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="19055-109">接收的組件或模組參考。</span><span class="sxs-lookup"><span data-stu-id="19055-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19055-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="19055-110">Return Value</span></span>  
 <span data-ttu-id="19055-111">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="19055-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19055-112">需求</span><span class="sxs-lookup"><span data-stu-id="19055-112">Requirements</span></span>  
 <span data-ttu-id="19055-113">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="19055-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19055-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="19055-114">See Also</span></span>  
 [<span data-ttu-id="19055-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="19055-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="19055-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="19055-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="19055-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="19055-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
