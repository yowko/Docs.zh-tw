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
ms.openlocfilehash: faf1438f56cd49b235ffbb18a0154e3e20c202b9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684963"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="1222b-102">EmitInternalExportedTypes 方法</span><span class="sxs-lookup"><span data-stu-id="1222b-102">EmitInternalExportedTypes Method</span></span>

<span data-ttu-id="1222b-103">發出加入至元件的類型。</span><span class="sxs-lookup"><span data-stu-id="1222b-103">Emits types added to the assembly.</span></span> <span data-ttu-id="1222b-104">新增已知的內部類型之後，請呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="1222b-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1222b-105">語法</span><span class="sxs-lookup"><span data-stu-id="1222b-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="1222b-106">參數</span><span class="sxs-lookup"><span data-stu-id="1222b-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="1222b-107">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1222b-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1222b-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="1222b-108">Return Value</span></span>  

 <span data-ttu-id="1222b-109">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="1222b-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1222b-110">需求</span><span class="sxs-lookup"><span data-stu-id="1222b-110">Requirements</span></span>  

 <span data-ttu-id="1222b-111">需要 alink。h</span><span class="sxs-lookup"><span data-stu-id="1222b-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1222b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1222b-112">See also</span></span>

- [<span data-ttu-id="1222b-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="1222b-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="1222b-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="1222b-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="1222b-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="1222b-115">ALink API</span></span>](index.md)
