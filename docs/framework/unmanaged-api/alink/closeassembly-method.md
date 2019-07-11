---
title: CloseAssembly 方法
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 18e0b7b3547bb246588f6b255483d4c317e0df88
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742224"
---
# <a name="closeassembly-method"></a><span data-ttu-id="40c25-102">CloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="40c25-102">CloseAssembly Method</span></span>
<span data-ttu-id="40c25-103">完成組件作業。</span><span class="sxs-lookup"><span data-stu-id="40c25-103">Finalizes assembly operations.</span></span> <span data-ttu-id="40c25-104">開始新的組件或未繫結的模組之前呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="40c25-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40c25-105">語法</span><span class="sxs-lookup"><span data-stu-id="40c25-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="40c25-106">參數</span><span class="sxs-lookup"><span data-stu-id="40c25-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="40c25-107">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="40c25-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40c25-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="40c25-108">Return Value</span></span>  
 <span data-ttu-id="40c25-109">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="40c25-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40c25-110">需求</span><span class="sxs-lookup"><span data-stu-id="40c25-110">Requirements</span></span>  
 <span data-ttu-id="40c25-111">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="40c25-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c25-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40c25-112">See also</span></span>

- [<span data-ttu-id="40c25-113">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="40c25-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="40c25-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="40c25-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="40c25-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="40c25-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
