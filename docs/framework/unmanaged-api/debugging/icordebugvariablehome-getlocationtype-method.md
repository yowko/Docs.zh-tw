---
title: "ICorDebugVariableHome::GetLocationType 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetLocationType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a600f26440e29a60d776be8679d7a298d77434f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="2a331-102">ICorDebugVariableHome::GetLocationType 方法</span><span class="sxs-lookup"><span data-stu-id="2a331-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="2a331-103">取得變數的原生位置類型。</span><span class="sxs-lookup"><span data-stu-id="2a331-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a331-104">語法</span><span class="sxs-lookup"><span data-stu-id="2a331-104">Syntax</span></span>  
  
```  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a331-105">參數</span><span class="sxs-lookup"><span data-stu-id="2a331-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="2a331-106">[out]變數的原生位置的類型的指標。</span><span class="sxs-lookup"><span data-stu-id="2a331-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="2a331-107">請參閱[VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)列舉型別，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2a331-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a331-108">需求</span><span class="sxs-lookup"><span data-stu-id="2a331-108">Requirements</span></span>  
 <span data-ttu-id="2a331-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a331-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a331-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a331-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a331-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a331-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a331-112">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a331-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a331-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a331-113">See Also</span></span>  
 [<span data-ttu-id="2a331-114">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="2a331-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 [<span data-ttu-id="2a331-115">VariableLocationType 列舉</span><span class="sxs-lookup"><span data-stu-id="2a331-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
