---
title: "ICorDebugModule::GetSize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetSize
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetSize method [.NET Framework debugging]
ms.assetid: 5c68375d-145d-46ef-a7c8-2dc4257472de
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d9474b48526e2ba6292c28e5e66eb97f8e57f2a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="de7a5-102">ICorDebugModule::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="de7a5-102">ICorDebugModule::GetSize Method</span></span>
<span data-ttu-id="de7a5-103">取得大小，以位元組為單位的模組。</span><span class="sxs-lookup"><span data-stu-id="de7a5-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de7a5-104">語法</span><span class="sxs-lookup"><span data-stu-id="de7a5-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de7a5-105">參數</span><span class="sxs-lookup"><span data-stu-id="de7a5-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="de7a5-106">[out]以位元組為單位之模組的大小。</span><span class="sxs-lookup"><span data-stu-id="de7a5-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="de7a5-107">如果從原生映像產生器 (NGen.exe) 產生的模組，模組的大小將是零。</span><span class="sxs-lookup"><span data-stu-id="de7a5-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de7a5-108">需求</span><span class="sxs-lookup"><span data-stu-id="de7a5-108">Requirements</span></span>  
 <span data-ttu-id="de7a5-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="de7a5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de7a5-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de7a5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de7a5-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de7a5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de7a5-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de7a5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
