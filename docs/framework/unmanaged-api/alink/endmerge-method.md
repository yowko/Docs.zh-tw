---
title: "EndMerge 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EndMerge
- EndMerge
api_location: alink.dll
api_type: COM
f1_keywords: EndMerge
helpviewer_keywords: EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58e9cecae43fb69f1ce2e90eb9d6551d287ca7b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="endmerge-method"></a><span data-ttu-id="8a964-102">EndMerge 方法</span><span class="sxs-lookup"><span data-stu-id="8a964-102">EndMerge Method</span></span>
<span data-ttu-id="8a964-103">表示所有自訂屬性，已合併到發出範圍。</span><span class="sxs-lookup"><span data-stu-id="8a964-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a964-104">語法</span><span class="sxs-lookup"><span data-stu-id="8a964-104">Syntax</span></span>  
  
```  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a964-105">參數</span><span class="sxs-lookup"><span data-stu-id="8a964-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8a964-106">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="8a964-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a964-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="8a964-107">Return Value</span></span>  
 <span data-ttu-id="8a964-108">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="8a964-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a964-109">需求</span><span class="sxs-lookup"><span data-stu-id="8a964-109">Requirements</span></span>  
 <span data-ttu-id="8a964-110">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="8a964-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a964-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="8a964-111">See Also</span></span>  
 [<span data-ttu-id="8a964-112">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="8a964-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="8a964-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="8a964-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="8a964-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="8a964-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
