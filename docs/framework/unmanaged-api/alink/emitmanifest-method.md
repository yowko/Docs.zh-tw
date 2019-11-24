---
title: EmitManifest 方法
ms.date: 03/30/2017
api_name:
- EmitManifest
- IALink.EmitManifest
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitManifest
helpviewer_keywords:
- EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type:
- apiref
ms.openlocfilehash: f3bb978b8358992fd9aa7da922e28efc1ed1a951
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446489"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="c8a9a-102">EmitManifest 方法</span><span class="sxs-lookup"><span data-stu-id="c8a9a-102">EmitManifest Method</span></span>
<span data-ttu-id="c8a9a-103">Emits the final manifest.</span><span class="sxs-lookup"><span data-stu-id="c8a9a-103">Emits the final manifest.</span></span> <span data-ttu-id="c8a9a-104">Call this method after importing all other files and setting all options.</span><span class="sxs-lookup"><span data-stu-id="c8a9a-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="c8a9a-105">Do not call this method for unbound modules.</span><span class="sxs-lookup"><span data-stu-id="c8a9a-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8a9a-106">語法</span><span class="sxs-lookup"><span data-stu-id="c8a9a-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8a9a-107">參數</span><span class="sxs-lookup"><span data-stu-id="c8a9a-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c8a9a-108">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="c8a9a-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="c8a9a-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="c8a9a-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="c8a9a-110">Optionally receives the assembly manifest token.</span><span class="sxs-lookup"><span data-stu-id="c8a9a-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8a9a-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="c8a9a-111">Return Value</span></span>  
 <span data-ttu-id="c8a9a-112">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="c8a9a-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8a9a-113">需求</span><span class="sxs-lookup"><span data-stu-id="c8a9a-113">Requirements</span></span>  
 <span data-ttu-id="c8a9a-114">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="c8a9a-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8a9a-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="c8a9a-115">See also</span></span>

- [<span data-ttu-id="c8a9a-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="c8a9a-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c8a9a-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="c8a9a-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c8a9a-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="c8a9a-118">ALink API</span></span>](index.md)
