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
ms.openlocfilehash: e1aeffbd5d5b22bea87dd7a49a3268822ce84d38
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481168"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="71eb0-102">PreCloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="71eb0-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="71eb0-103">關閉組件檔案。</span><span class="sxs-lookup"><span data-stu-id="71eb0-103">Closes the assembly file.</span></span> <span data-ttu-id="71eb0-104">關閉所有其他檔案之後, 但在關閉的組件檔案之前，請呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="71eb0-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="71eb0-105">請勿呼叫這個方法的未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="71eb0-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71eb0-106">語法</span><span class="sxs-lookup"><span data-stu-id="71eb0-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="71eb0-107">參數</span><span class="sxs-lookup"><span data-stu-id="71eb0-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="71eb0-108">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="71eb0-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71eb0-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="71eb0-109">Return Value</span></span>  
 <span data-ttu-id="71eb0-110">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="71eb0-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71eb0-111">需求</span><span class="sxs-lookup"><span data-stu-id="71eb0-111">Requirements</span></span>  
 <span data-ttu-id="71eb0-112">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="71eb0-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71eb0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71eb0-113">See also</span></span>
- [<span data-ttu-id="71eb0-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="71eb0-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="71eb0-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="71eb0-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="71eb0-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="71eb0-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
