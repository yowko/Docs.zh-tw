---
title: "EmitInternalExportedTypes 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location: alink.dll
api_type: COM
f1_keywords: EmitInternalExportedTypes
helpviewer_keywords: EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 48ad5e34b926cf3dab562f57bb9206fa0ba70e6b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="e78a0-102">EmitInternalExportedTypes 方法</span><span class="sxs-lookup"><span data-stu-id="e78a0-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="e78a0-103">會發出型別新增至組件。</span><span class="sxs-lookup"><span data-stu-id="e78a0-103">Emits types added to the assembly.</span></span> <span data-ttu-id="e78a0-104">呼叫這個方法之後已知已加入內部型別。</span><span class="sxs-lookup"><span data-stu-id="e78a0-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e78a0-105">語法</span><span class="sxs-lookup"><span data-stu-id="e78a0-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e78a0-106">參數</span><span class="sxs-lookup"><span data-stu-id="e78a0-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e78a0-107">組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="e78a0-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e78a0-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e78a0-108">Return Value</span></span>  
 <span data-ttu-id="e78a0-109">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="e78a0-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e78a0-110">需求</span><span class="sxs-lookup"><span data-stu-id="e78a0-110">Requirements</span></span>  
 <span data-ttu-id="e78a0-111">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="e78a0-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e78a0-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="e78a0-112">See Also</span></span>  
 [<span data-ttu-id="e78a0-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="e78a0-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e78a0-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="e78a0-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e78a0-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="e78a0-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
