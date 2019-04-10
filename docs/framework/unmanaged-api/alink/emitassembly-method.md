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
ms.openlocfilehash: bf7b54ab7a2318e8194bf39dbe41b864633ddb43
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212904"
---
# <a name="emitassembly-method"></a><span data-ttu-id="75f39-102">EmitAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="75f39-102">EmitAssembly Method</span></span>
<span data-ttu-id="75f39-103">建立組件。</span><span class="sxs-lookup"><span data-stu-id="75f39-103">Creates the assembly.</span></span> <span data-ttu-id="75f39-104">之後的組件檔案除外的其他所有檔案都已都關閉，請呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="75f39-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="75f39-105">產生未繫結的模組時，請勿呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="75f39-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75f39-106">語法</span><span class="sxs-lookup"><span data-stu-id="75f39-106">Syntax</span></span>  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="75f39-107">參數</span><span class="sxs-lookup"><span data-stu-id="75f39-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="75f39-108">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="75f39-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75f39-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="75f39-109">Return Value</span></span>  
 <span data-ttu-id="75f39-110">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="75f39-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75f39-111">需求</span><span class="sxs-lookup"><span data-stu-id="75f39-111">Requirements</span></span>  
 <span data-ttu-id="75f39-112">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="75f39-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75f39-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75f39-113">See also</span></span>

- [<span data-ttu-id="75f39-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="75f39-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="75f39-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="75f39-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="75f39-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="75f39-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
