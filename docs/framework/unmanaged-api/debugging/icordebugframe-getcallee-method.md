---
title: "ICorDebugFrame::GetCallee 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 079d598e54f429fa4dd0b5c0c4cadbe2c66c1d50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="e7fea-102">ICorDebugFrame::GetCallee 方法</span><span class="sxs-lookup"><span data-stu-id="e7fea-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="e7fea-103">取得在目前的鏈結中，呼叫此框架 ICorDebugFrame 物件指標。</span><span class="sxs-lookup"><span data-stu-id="e7fea-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7fea-104">語法</span><span class="sxs-lookup"><span data-stu-id="e7fea-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7fea-105">參數</span><span class="sxs-lookup"><span data-stu-id="e7fea-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="e7fea-106">[out]位址指標`ICorDebugFrame`物件，表示呼叫的框架。</span><span class="sxs-lookup"><span data-stu-id="e7fea-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="e7fea-107">此值為 null，如果呼叫的畫面格是目前鏈結中最內層的框架。</span><span class="sxs-lookup"><span data-stu-id="e7fea-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7fea-108">需求</span><span class="sxs-lookup"><span data-stu-id="e7fea-108">Requirements</span></span>  
 <span data-ttu-id="e7fea-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7fea-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7fea-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7fea-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7fea-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7fea-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7fea-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7fea-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
