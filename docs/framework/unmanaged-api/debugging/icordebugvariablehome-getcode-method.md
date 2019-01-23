---
title: ICorDebugVariableHome::GetCode 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetCode
helpviewer_keywords:
- ICorDebugVariableHome::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: ef002890-4a7b-4a5d-abbf-16c60083f794
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 216779ab03b426ceb8003accfbdd182f583b77cc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557340"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="16c6c-102">ICorDebugVariableHome::GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="16c6c-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="16c6c-103">取得"ICorDebugCode 」 執行個體，包含這個[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="16c6c-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16c6c-104">語法</span><span class="sxs-lookup"><span data-stu-id="16c6c-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16c6c-105">參數</span><span class="sxs-lookup"><span data-stu-id="16c6c-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="16c6c-106">[out]包含此 「 ICorDebugCode 」 執行個體的位址指標[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="16c6c-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16c6c-107">需求</span><span class="sxs-lookup"><span data-stu-id="16c6c-107">Requirements</span></span>  
 <span data-ttu-id="16c6c-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="16c6c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16c6c-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16c6c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16c6c-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16c6c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16c6c-111">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16c6c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c6c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16c6c-112">See also</span></span>
- [<span data-ttu-id="16c6c-113">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="16c6c-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)

