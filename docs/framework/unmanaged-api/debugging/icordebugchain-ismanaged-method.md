---
title: "ICorDebugChain::IsManaged 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.IsManaged
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fe5736a1ca420eb361e062743ed93982e7ec3f29
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="c8dc0-102">ICorDebugChain::IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="c8dc0-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="c8dc0-103">取得值，指出這個鏈結是否正在執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="c8dc0-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8dc0-104">語法</span><span class="sxs-lookup"><span data-stu-id="c8dc0-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8dc0-105">參數</span><span class="sxs-lookup"><span data-stu-id="c8dc0-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="c8dc0-106">[out]`true`如果這個鏈結執行 managed 程式碼; 否則`false`。</span><span class="sxs-lookup"><span data-stu-id="c8dc0-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8dc0-107">需求</span><span class="sxs-lookup"><span data-stu-id="c8dc0-107">Requirements</span></span>  
 <span data-ttu-id="c8dc0-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8dc0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8dc0-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8dc0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8dc0-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8dc0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8dc0-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8dc0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
