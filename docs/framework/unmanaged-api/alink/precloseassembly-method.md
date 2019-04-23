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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184505"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="6c482-102">PreCloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="6c482-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="6c482-103">關閉組件檔案。</span><span class="sxs-lookup"><span data-stu-id="6c482-103">Closes the assembly file.</span></span> <span data-ttu-id="6c482-104">關閉所有其他檔案之後, 但在關閉的組件檔案之前，請呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="6c482-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="6c482-105">請勿呼叫這個方法的未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="6c482-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c482-106">語法</span><span class="sxs-lookup"><span data-stu-id="6c482-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c482-107">參數</span><span class="sxs-lookup"><span data-stu-id="6c482-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6c482-108">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6c482-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c482-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6c482-109">Return Value</span></span>  
 <span data-ttu-id="6c482-110">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="6c482-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c482-111">需求</span><span class="sxs-lookup"><span data-stu-id="6c482-111">Requirements</span></span>  
 <span data-ttu-id="6c482-112">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="6c482-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c482-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c482-113">See also</span></span>

- [<span data-ttu-id="6c482-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="6c482-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="6c482-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="6c482-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="6c482-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="6c482-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
