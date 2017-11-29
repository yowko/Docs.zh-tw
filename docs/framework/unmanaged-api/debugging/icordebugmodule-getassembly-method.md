---
title: "ICorDebugModule::GetAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetAssembly
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetAssembly
helpviewer_keywords:
- ICorDebugModule::GetAssembly method [.NET Framework debugging]
- GetAssembly method [.NET Framework debugging]
ms.assetid: 989762c4-3d15-4485-b8ee-69e0fa8ec895
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 98d4670fc1d571d2a959b2a69ea8619bd8b40007
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="d8ec8-102">ICorDebugModule::GetAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="d8ec8-102">ICorDebugModule::GetAssembly Method</span></span>
<span data-ttu-id="d8ec8-103">取得針對此模組包含組件。</span><span class="sxs-lookup"><span data-stu-id="d8ec8-103">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8ec8-104">語法</span><span class="sxs-lookup"><span data-stu-id="d8ec8-104">Syntax</span></span>  
  
```  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8ec8-105">參數</span><span class="sxs-lookup"><span data-stu-id="d8ec8-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="d8ec8-106">[out]ICorDebugAssembly 物件，代表包含此模組的組件的指標。</span><span class="sxs-lookup"><span data-stu-id="d8ec8-106">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8ec8-107">需求</span><span class="sxs-lookup"><span data-stu-id="d8ec8-107">Requirements</span></span>  
 <span data-ttu-id="d8ec8-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8ec8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ec8-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8ec8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8ec8-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8ec8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8ec8-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ec8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
