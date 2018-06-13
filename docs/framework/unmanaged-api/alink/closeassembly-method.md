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
ms.openlocfilehash: 68698aab0fd0872c6e6f67e4ec531ab0226e784f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401949"
---
# <a name="closeassembly-method"></a><span data-ttu-id="1993b-102">CloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="1993b-102">CloseAssembly Method</span></span>
<span data-ttu-id="1993b-103">完成組件作業。</span><span class="sxs-lookup"><span data-stu-id="1993b-103">Finalizes assembly operations.</span></span> <span data-ttu-id="1993b-104">開始新的組件或未繫結的模組之前呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="1993b-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1993b-105">語法</span><span class="sxs-lookup"><span data-stu-id="1993b-105">Syntax</span></span>  
  
```  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1993b-106">參數</span><span class="sxs-lookup"><span data-stu-id="1993b-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1993b-107">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1993b-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1993b-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="1993b-108">Return Value</span></span>  
 <span data-ttu-id="1993b-109">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="1993b-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1993b-110">需求</span><span class="sxs-lookup"><span data-stu-id="1993b-110">Requirements</span></span>  
 <span data-ttu-id="1993b-111">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="1993b-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1993b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1993b-112">See Also</span></span>  
 [<span data-ttu-id="1993b-113">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="1993b-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="1993b-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="1993b-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="1993b-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="1993b-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
