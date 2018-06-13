---
title: EmitAssembly 方法
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1cd1c077a8f2a5fe3b2b46c2e1da2e92b5a797a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402053"
---
# <a name="emitassembly-method"></a><span data-ttu-id="5f9bf-102">EmitAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="5f9bf-102">EmitAssembly Method</span></span>
<span data-ttu-id="5f9bf-103">建立組件。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-103">Creates the assembly.</span></span> <span data-ttu-id="5f9bf-104">其他所有檔案都已都關閉的組件檔案除外之後呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="5f9bf-105">產生未繫結的模組時，請勿呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f9bf-106">語法</span><span class="sxs-lookup"><span data-stu-id="5f9bf-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f9bf-107">參數</span><span class="sxs-lookup"><span data-stu-id="5f9bf-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="5f9bf-108">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f9bf-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="5f9bf-109">Return Value</span></span>  
 <span data-ttu-id="5f9bf-110">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="5f9bf-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f9bf-111">需求</span><span class="sxs-lookup"><span data-stu-id="5f9bf-111">Requirements</span></span>  
 <span data-ttu-id="5f9bf-112">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="5f9bf-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f9bf-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f9bf-113">See Also</span></span>  
 [<span data-ttu-id="5f9bf-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="5f9bf-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="5f9bf-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="5f9bf-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="5f9bf-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="5f9bf-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
