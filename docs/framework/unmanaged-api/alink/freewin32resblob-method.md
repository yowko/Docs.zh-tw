---
title: FreeWin32ResBlob 方法
ms.date: 03/30/2017
api_name:
- IALink.FreeWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- FreeWin32ResBlob
helpviewer_keywords:
- FreeWin32ResBlob method
ms.assetid: d941102b-2679-4c49-b15e-c0fc9c53e11f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d124ce5dd38bed7eb439a055ff9e30a75efe5891
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400740"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="86821-102">FreeWin32ResBlob 方法</span><span class="sxs-lookup"><span data-stu-id="86821-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="86821-103">釋放的 Win32 資源 blob 和相關聯的資源。</span><span class="sxs-lookup"><span data-stu-id="86821-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86821-104">語法</span><span class="sxs-lookup"><span data-stu-id="86821-104">Syntax</span></span>  
  
```  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86821-105">參數</span><span class="sxs-lookup"><span data-stu-id="86821-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="86821-106">釋出資源 blob。</span><span class="sxs-lookup"><span data-stu-id="86821-106">The resource blob to be released.</span></span> <span data-ttu-id="86821-107">這個方法會將 blob 指標指派給 NULL。</span><span class="sxs-lookup"><span data-stu-id="86821-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86821-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="86821-108">Return Value</span></span>  
 <span data-ttu-id="86821-109">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="86821-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86821-110">需求</span><span class="sxs-lookup"><span data-stu-id="86821-110">Requirements</span></span>  
 <span data-ttu-id="86821-111">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="86821-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86821-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86821-112">See Also</span></span>  
 [<span data-ttu-id="86821-113">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="86821-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="86821-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="86821-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="86821-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="86821-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
