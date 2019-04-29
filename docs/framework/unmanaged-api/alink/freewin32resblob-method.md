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
ms.openlocfilehash: 196a57b3e919ea4ccbc0b91e5b6f281ad3c30b62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789879"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="c1166-102">FreeWin32ResBlob 方法</span><span class="sxs-lookup"><span data-stu-id="c1166-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="c1166-103">釋放的 Win32 資源的 blob 和相關聯的資源。</span><span class="sxs-lookup"><span data-stu-id="c1166-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1166-104">語法</span><span class="sxs-lookup"><span data-stu-id="c1166-104">Syntax</span></span>  
  
```  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1166-105">參數</span><span class="sxs-lookup"><span data-stu-id="c1166-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="c1166-106">若要釋出資源 blob。</span><span class="sxs-lookup"><span data-stu-id="c1166-106">The resource blob to be released.</span></span> <span data-ttu-id="c1166-107">這個方法會將 blob 指標指派給 NULL。</span><span class="sxs-lookup"><span data-stu-id="c1166-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1166-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="c1166-108">Return Value</span></span>  
 <span data-ttu-id="c1166-109">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="c1166-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1166-110">需求</span><span class="sxs-lookup"><span data-stu-id="c1166-110">Requirements</span></span>  
 <span data-ttu-id="c1166-111">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="c1166-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1166-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1166-112">See also</span></span>

- [<span data-ttu-id="c1166-113">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="c1166-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c1166-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="c1166-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c1166-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="c1166-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
