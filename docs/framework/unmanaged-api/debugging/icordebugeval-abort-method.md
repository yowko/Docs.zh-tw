---
title: "ICorDebugEval::Abort 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.Abort
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::Abort
helpviewer_keywords:
- Abort method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::Abort method [.NET Framework debugging]
ms.assetid: 7070b6d0-f2e0-44ff-b124-0944cd807e69
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a53597067d14c5b3dc1f8829b8ea0a0df07de25a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="d7254-102">ICorDebugEval::Abort 方法</span><span class="sxs-lookup"><span data-stu-id="d7254-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="d7254-103">中止目前正在這個 ICorDebugEval 物件的計算。</span><span class="sxs-lookup"><span data-stu-id="d7254-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7254-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7254-104">Syntax</span></span>  
  
```  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="d7254-105">備註</span><span class="sxs-lookup"><span data-stu-id="d7254-105">Remarks</span></span>  
 <span data-ttu-id="d7254-106">如果評估為巢狀，而且它不是最新的工作，`Abort`方法可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="d7254-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7254-107">需求</span><span class="sxs-lookup"><span data-stu-id="d7254-107">Requirements</span></span>  
 <span data-ttu-id="d7254-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7254-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7254-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7254-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7254-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7254-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7254-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7254-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
