---
title: PreCloseAssembly 方法
ms.date: 03/30/2017
api_name:
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82421fa83a6f0d24492d70f961e731b679c25728
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400714"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="52c0e-102">PreCloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="52c0e-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="52c0e-103">關閉組件檔案。</span><span class="sxs-lookup"><span data-stu-id="52c0e-103">Closes the assembly file.</span></span> <span data-ttu-id="52c0e-104">之後關閉所有其他檔案，但在關閉的組件檔案之前，請呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="52c0e-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="52c0e-105">請勿呼叫這個方法未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="52c0e-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52c0e-106">語法</span><span class="sxs-lookup"><span data-stu-id="52c0e-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52c0e-107">參數</span><span class="sxs-lookup"><span data-stu-id="52c0e-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="52c0e-108">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="52c0e-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52c0e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="52c0e-109">Return Value</span></span>  
 <span data-ttu-id="52c0e-110">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="52c0e-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52c0e-111">需求</span><span class="sxs-lookup"><span data-stu-id="52c0e-111">Requirements</span></span>  
 <span data-ttu-id="52c0e-112">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="52c0e-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c0e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52c0e-113">See Also</span></span>  
 [<span data-ttu-id="52c0e-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="52c0e-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="52c0e-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="52c0e-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="52c0e-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="52c0e-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
