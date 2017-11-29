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
ms.openlocfilehash: c5f8761259e89b4befd0eeaf893ffbe5d4142350
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="setnonassemblyflags-method"></a><span data-ttu-id="461db-102">SetNonAssemblyFlags 方法</span><span class="sxs-lookup"><span data-stu-id="461db-102">SetNonAssemblyFlags Method</span></span>
<span data-ttu-id="461db-103">設定不是組件特定的旗標。</span><span class="sxs-lookup"><span data-stu-id="461db-103">Sets flags that are not assembly-specific.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="461db-104">語法</span><span class="sxs-lookup"><span data-stu-id="461db-104">Syntax</span></span>  
  
```  
HRESULT SetNonAssemblyFlags(  
    AssemblyFlags afFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="461db-105">參數</span><span class="sxs-lookup"><span data-stu-id="461db-105">Parameters</span></span>  
 `afFlags`  
 <span data-ttu-id="461db-106">ALink 旗標。</span><span class="sxs-lookup"><span data-stu-id="461db-106">ALink flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="461db-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="461db-107">Return Value</span></span>  
 <span data-ttu-id="461db-108">如果方法成功則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="461db-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="461db-109">需求</span><span class="sxs-lookup"><span data-stu-id="461db-109">Requirements</span></span>  
 <span data-ttu-id="461db-110">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="461db-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="461db-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="461db-111">See Also</span></span>  
 [<span data-ttu-id="461db-112">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="461db-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="461db-113">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="461db-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="461db-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="461db-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
