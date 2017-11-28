---
title: "ICorDebugAppDomain::Attach 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.Attach
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::Attach
helpviewer_keywords:
- ICorDebugAppDomain::Attach method [.NET Framework debugging]
- Attach method [.NET Framework debugging]
ms.assetid: 0358b84a-4236-4c34-945b-4babff7df570
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25f6d32cc1b06615c592739ffab8a87f0fe5d5b8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="1a8b9-102">ICorDebugAppDomain::Attach 方法</span><span class="sxs-lookup"><span data-stu-id="1a8b9-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="1a8b9-103">將偵錯工具附加至應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="1a8b9-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a8b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="1a8b9-104">Syntax</span></span>  
  
```  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1a8b9-105">備註</span><span class="sxs-lookup"><span data-stu-id="1a8b9-105">Remarks</span></span>  
 <span data-ttu-id="1a8b9-106">偵錯工具必須連接到接收事件，並啟用應用程式定義域的偵錯的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="1a8b9-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a8b9-107">需求</span><span class="sxs-lookup"><span data-stu-id="1a8b9-107">Requirements</span></span>  
 <span data-ttu-id="1a8b9-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1a8b9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a8b9-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a8b9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a8b9-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a8b9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a8b9-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a8b9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
