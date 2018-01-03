---
title: "FreeWin32ResBlob 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.FreeWin32ResBlob
api_location: alink.dll
api_type: COM
f1_keywords: FreeWin32ResBlob
helpviewer_keywords: FreeWin32ResBlob method
ms.assetid: d941102b-2679-4c49-b15e-c0fc9c53e11f
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdecedf319ad235bd635dd1d2edf600b0d00dbb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="39772-102">FreeWin32ResBlob 方法</span><span class="sxs-lookup"><span data-stu-id="39772-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="39772-103">釋放的 Win32 資源 blob 和相關聯的資源。</span><span class="sxs-lookup"><span data-stu-id="39772-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39772-104">語法</span><span class="sxs-lookup"><span data-stu-id="39772-104">Syntax</span></span>  
  
```  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39772-105">參數</span><span class="sxs-lookup"><span data-stu-id="39772-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="39772-106">釋出資源 blob。</span><span class="sxs-lookup"><span data-stu-id="39772-106">The resource blob to be released.</span></span> <span data-ttu-id="39772-107">這個方法會將 blob 指標指派給 NULL。</span><span class="sxs-lookup"><span data-stu-id="39772-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39772-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="39772-108">Return Value</span></span>  
 <span data-ttu-id="39772-109">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="39772-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39772-110">需求</span><span class="sxs-lookup"><span data-stu-id="39772-110">Requirements</span></span>  
 <span data-ttu-id="39772-111">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="39772-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39772-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="39772-112">See Also</span></span>  
 [<span data-ttu-id="39772-113">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="39772-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="39772-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="39772-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="39772-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="39772-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
