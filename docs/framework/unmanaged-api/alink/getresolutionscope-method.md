---
title: GetResolutionScope 方法
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
ms.openlocfilehash: f2b78b35db6306c82e389955c4824875bcf25334
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447233"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="ea5f8-102">GetResolutionScope 方法</span><span class="sxs-lookup"><span data-stu-id="ea5f8-102">GetResolutionScope Method</span></span>
<span data-ttu-id="ea5f8-103">Retrieves the scope of a given type.</span><span class="sxs-lookup"><span data-stu-id="ea5f8-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea5f8-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea5f8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea5f8-105">參數</span><span class="sxs-lookup"><span data-stu-id="ea5f8-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ea5f8-106">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="ea5f8-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ea5f8-107">File that is in need of a reference.</span><span class="sxs-lookup"><span data-stu-id="ea5f8-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="ea5f8-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="ea5f8-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="ea5f8-109">Receives the assembly or module reference.</span><span class="sxs-lookup"><span data-stu-id="ea5f8-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea5f8-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="ea5f8-110">Return Value</span></span>  
 <span data-ttu-id="ea5f8-111">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="ea5f8-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea5f8-112">需求</span><span class="sxs-lookup"><span data-stu-id="ea5f8-112">Requirements</span></span>  
 <span data-ttu-id="ea5f8-113">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="ea5f8-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea5f8-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea5f8-114">See also</span></span>

- [<span data-ttu-id="ea5f8-115">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="ea5f8-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ea5f8-116">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="ea5f8-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ea5f8-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="ea5f8-117">ALink API</span></span>](index.md)
