---
title: "CloseEnum 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CloseEnum
- IALink.CloseEnum
api_location: alink.dll
api_type: COM
f1_keywords: CloseEnum
helpviewer_keywords: CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6ade939969069fb35221d83f8c7e4e380e903a00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="closeenum-method"></a><span data-ttu-id="2b09d-102">CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="2b09d-102">CloseEnum Method</span></span>
<span data-ttu-id="2b09d-103">關閉指定的列舉型別，並釋放相關聯的資源。</span><span class="sxs-lookup"><span data-stu-id="2b09d-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b09d-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b09d-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b09d-105">參數</span><span class="sxs-lookup"><span data-stu-id="2b09d-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="2b09d-106">要關閉的列舉控制代碼。</span><span class="sxs-lookup"><span data-stu-id="2b09d-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b09d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="2b09d-107">Return Value</span></span>  
 <span data-ttu-id="2b09d-108">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="2b09d-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b09d-109">需求</span><span class="sxs-lookup"><span data-stu-id="2b09d-109">Requirements</span></span>  
 <span data-ttu-id="2b09d-110">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="2b09d-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b09d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b09d-111">See Also</span></span>  
 [<span data-ttu-id="2b09d-112">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="2b09d-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="2b09d-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="2b09d-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="2b09d-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="2b09d-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
