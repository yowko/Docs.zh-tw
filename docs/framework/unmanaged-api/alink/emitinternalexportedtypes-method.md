---
title: EmitInternalExportedTypes 方法
ms.date: 03/30/2017
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitInternalExportedTypes
helpviewer_keywords:
- EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c196bcc159b18b9dc04329d817ebe16e07bb8bb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790009"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="e9c41-102">EmitInternalExportedTypes 方法</span><span class="sxs-lookup"><span data-stu-id="e9c41-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="e9c41-103">會發出新增至組件的類型。</span><span class="sxs-lookup"><span data-stu-id="e9c41-103">Emits types added to the assembly.</span></span> <span data-ttu-id="e9c41-104">呼叫這個方法之後稱為已加入內部的類型。</span><span class="sxs-lookup"><span data-stu-id="e9c41-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9c41-105">語法</span><span class="sxs-lookup"><span data-stu-id="e9c41-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9c41-106">參數</span><span class="sxs-lookup"><span data-stu-id="e9c41-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e9c41-107">組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="e9c41-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9c41-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e9c41-108">Return Value</span></span>  
 <span data-ttu-id="e9c41-109">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="e9c41-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9c41-110">需求</span><span class="sxs-lookup"><span data-stu-id="e9c41-110">Requirements</span></span>  
 <span data-ttu-id="e9c41-111">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="e9c41-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c41-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9c41-112">See also</span></span>

- [<span data-ttu-id="e9c41-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="e9c41-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="e9c41-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="e9c41-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="e9c41-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="e9c41-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
