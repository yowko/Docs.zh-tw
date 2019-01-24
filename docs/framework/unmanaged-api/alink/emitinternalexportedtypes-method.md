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
ms.openlocfilehash: 68373e9277a9d87bba6941259588f25a92af90a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710543"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="9c639-102">EmitInternalExportedTypes 方法</span><span class="sxs-lookup"><span data-stu-id="9c639-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="9c639-103">會發出新增至組件的類型。</span><span class="sxs-lookup"><span data-stu-id="9c639-103">Emits types added to the assembly.</span></span> <span data-ttu-id="9c639-104">呼叫這個方法之後稱為已加入內部的類型。</span><span class="sxs-lookup"><span data-stu-id="9c639-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c639-105">語法</span><span class="sxs-lookup"><span data-stu-id="9c639-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c639-106">參數</span><span class="sxs-lookup"><span data-stu-id="9c639-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9c639-107">組件識別碼。</span><span class="sxs-lookup"><span data-stu-id="9c639-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c639-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="9c639-108">Return Value</span></span>  
 <span data-ttu-id="9c639-109">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="9c639-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c639-110">需求</span><span class="sxs-lookup"><span data-stu-id="9c639-110">Requirements</span></span>  
 <span data-ttu-id="9c639-111">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="9c639-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c639-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c639-112">See also</span></span>
- [<span data-ttu-id="9c639-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="9c639-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="9c639-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="9c639-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="9c639-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="9c639-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
