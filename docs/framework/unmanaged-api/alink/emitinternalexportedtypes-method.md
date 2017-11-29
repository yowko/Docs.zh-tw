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
ms.openlocfilehash: f354058e0de944bbce9d128d3f4baa9b941fda08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="4d4dd-102">EmitInternalExportedTypes 方法</span><span class="sxs-lookup"><span data-stu-id="4d4dd-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="4d4dd-103">會發出型別新增至組件。</span><span class="sxs-lookup"><span data-stu-id="4d4dd-103">Emits types added to the assembly.</span></span> <span data-ttu-id="4d4dd-104">呼叫這個方法之後已知已加入內部型別。</span><span class="sxs-lookup"><span data-stu-id="4d4dd-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d4dd-105">語法</span><span class="sxs-lookup"><span data-stu-id="4d4dd-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d4dd-106">參數</span><span class="sxs-lookup"><span data-stu-id="4d4dd-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4d4dd-107">組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="4d4dd-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d4dd-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="4d4dd-108">Return Value</span></span>  
 <span data-ttu-id="4d4dd-109">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="4d4dd-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d4dd-110">需求</span><span class="sxs-lookup"><span data-stu-id="4d4dd-110">Requirements</span></span>  
 <span data-ttu-id="4d4dd-111">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="4d4dd-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d4dd-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d4dd-112">See Also</span></span>  
 [<span data-ttu-id="4d4dd-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="4d4dd-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="4d4dd-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="4d4dd-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="4d4dd-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="4d4dd-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
