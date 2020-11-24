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
ms.openlocfilehash: 44c5228f7ee467abd02a9ec09590d0352fc82036
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684755"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="310ce-102">FreeWin32ResBlob 方法</span><span class="sxs-lookup"><span data-stu-id="310ce-102">FreeWin32ResBlob Method</span></span>

<span data-ttu-id="310ce-103">釋放 Win32 資源 blob 和相關聯的資源。</span><span class="sxs-lookup"><span data-stu-id="310ce-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="310ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="310ce-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="310ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="310ce-105">Parameters</span></span>  

 `ppResBlob`  
 <span data-ttu-id="310ce-106">要釋放的資源 blob。</span><span class="sxs-lookup"><span data-stu-id="310ce-106">The resource blob to be released.</span></span> <span data-ttu-id="310ce-107">這個方法會將 blob 指標指派給 Null。</span><span class="sxs-lookup"><span data-stu-id="310ce-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="310ce-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="310ce-108">Return Value</span></span>  

 <span data-ttu-id="310ce-109">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="310ce-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="310ce-110">需求</span><span class="sxs-lookup"><span data-stu-id="310ce-110">Requirements</span></span>  

 <span data-ttu-id="310ce-111">需要 alink。h</span><span class="sxs-lookup"><span data-stu-id="310ce-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="310ce-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="310ce-112">See also</span></span>

- [<span data-ttu-id="310ce-113">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="310ce-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="310ce-114">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="310ce-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="310ce-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="310ce-115">ALink API</span></span>](index.md)
