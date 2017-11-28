---
title: "PreCloseAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.PreCloseAssembly
api_location: alink.dll
api_type: COM
f1_keywords: PreCloseAssembly
helpviewer_keywords: PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8d940cbdeddc7030c679fae8c8694bb3542123b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="precloseassembly-method"></a><span data-ttu-id="81f65-102">PreCloseAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="81f65-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="81f65-103">關閉組件檔案。</span><span class="sxs-lookup"><span data-stu-id="81f65-103">Closes the assembly file.</span></span> <span data-ttu-id="81f65-104">之後關閉所有其他檔案，但在關閉的組件檔案之前，請呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="81f65-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="81f65-105">請勿呼叫這個方法未繫結的模組。</span><span class="sxs-lookup"><span data-stu-id="81f65-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81f65-106">語法</span><span class="sxs-lookup"><span data-stu-id="81f65-106">Syntax</span></span>  
  
```  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81f65-107">參數</span><span class="sxs-lookup"><span data-stu-id="81f65-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="81f65-108">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="81f65-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81f65-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="81f65-109">Return Value</span></span>  
 <span data-ttu-id="81f65-110">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="81f65-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81f65-111">需求</span><span class="sxs-lookup"><span data-stu-id="81f65-111">Requirements</span></span>  
 <span data-ttu-id="81f65-112">需要 alink.h。</span><span class="sxs-lookup"><span data-stu-id="81f65-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81f65-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81f65-113">See Also</span></span>  
 [<span data-ttu-id="81f65-114">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="81f65-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="81f65-115">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="81f65-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="81f65-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="81f65-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
