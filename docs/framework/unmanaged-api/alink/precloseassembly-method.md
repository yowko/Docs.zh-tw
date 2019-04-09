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
ms.openlocfilehash: aab42e939651d75b1933962d72ba8bec1090f52d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184505"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="d51dc-102">PreCloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="d51dc-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="d51dc-103">關閉組件檔案。</span><span class="sxs-lookup"><span data-stu-id="d51dc-103">Closes the assembly file.</span></span> <span data-ttu-id="d51dc-104">關閉所有其他檔案之後, 但在關閉的組件檔案之前，請呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="d51dc-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="d51dc-105">請勿呼叫這個方法的未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="d51dc-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d51dc-106">語法</span><span class="sxs-lookup"><span data-stu-id="d51dc-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d51dc-107">參數</span><span class="sxs-lookup"><span data-stu-id="d51dc-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d51dc-108">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="d51dc-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d51dc-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="d51dc-109">Return Value</span></span>  
 <span data-ttu-id="d51dc-110">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="d51dc-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d51dc-111">需求</span><span class="sxs-lookup"><span data-stu-id="d51dc-111">Requirements</span></span>  
 <span data-ttu-id="d51dc-112">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="d51dc-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d51dc-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d51dc-113">See also</span></span>

- [<span data-ttu-id="d51dc-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="d51dc-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="d51dc-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="d51dc-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="d51dc-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="d51dc-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
