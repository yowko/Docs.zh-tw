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
ms.openlocfilehash: 94c1c083d010cd82fd9e9e2f02b23e81d88fedd5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790087"
---
# <a name="closeassembly-method"></a><span data-ttu-id="0439f-102">CloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="0439f-102">CloseAssembly Method</span></span>
<span data-ttu-id="0439f-103">完成組件作業。</span><span class="sxs-lookup"><span data-stu-id="0439f-103">Finalizes assembly operations.</span></span> <span data-ttu-id="0439f-104">開始新的組件或未繫結的模組之前呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="0439f-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0439f-105">語法</span><span class="sxs-lookup"><span data-stu-id="0439f-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0439f-106">參數</span><span class="sxs-lookup"><span data-stu-id="0439f-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="0439f-107">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0439f-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0439f-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="0439f-108">Return Value</span></span>  
 <span data-ttu-id="0439f-109">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="0439f-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0439f-110">需求</span><span class="sxs-lookup"><span data-stu-id="0439f-110">Requirements</span></span>  
 <span data-ttu-id="0439f-111">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="0439f-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0439f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0439f-112">See also</span></span>

- [<span data-ttu-id="0439f-113">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="0439f-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="0439f-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="0439f-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="0439f-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="0439f-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
