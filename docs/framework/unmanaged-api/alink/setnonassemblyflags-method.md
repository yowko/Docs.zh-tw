---
title: "SetNonAssemblyFlags 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetNonAssemblyFlags
api_location: alink.dll
api_type: COM
f1_keywords: SetNonAssemblyFlags
helpviewer_keywords: SetNonAssemblyFlags method
ms.assetid: f8ba6fc8-f5aa-4066-ac96-56332758f5ec
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7e944f285ee0925b76fdd9b95c824deee38cead2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="88cbd-102">SetNonAssemblyFlags 方法</span><span class="sxs-lookup"><span data-stu-id="88cbd-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="88cbd-103">設定不是組件特定的旗標。</span><span class="sxs-lookup"><span data-stu-id="88cbd-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88cbd-104">語法</span><span class="sxs-lookup"><span data-stu-id="88cbd-104">Syntax</span></span>  
  
```  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88cbd-105">參數</span><span class="sxs-lookup"><span data-stu-id="88cbd-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="88cbd-106">ALink 旗標。</span><span class="sxs-lookup"><span data-stu-id="88cbd-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88cbd-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="88cbd-107">Return Value</span></span>  
 <span data-ttu-id="88cbd-108">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="88cbd-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88cbd-109">需求</span><span class="sxs-lookup"><span data-stu-id="88cbd-109">Requirements</span></span>  
 <span data-ttu-id="88cbd-110">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="88cbd-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88cbd-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="88cbd-111">See Also</span></span>  
 [<span data-ttu-id="88cbd-112">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="88cbd-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="88cbd-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="88cbd-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="88cbd-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="88cbd-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
