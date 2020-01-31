---
title: ICorDebugVariableHome：： GetCode 方法
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
ms.openlocfilehash: fdfa38a4cdbbaad2fc2c987a10a122af4a1fc9a9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791030"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="dfc8a-102">ICorDebugVariableHome：： GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="dfc8a-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="dfc8a-103">取得包含這個[ICorDebugVariableHome](icordebugvariablehome-interface.md)物件的 "ICorDebugCode" 實例。</span><span class="sxs-lookup"><span data-stu-id="dfc8a-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfc8a-104">語法</span><span class="sxs-lookup"><span data-stu-id="dfc8a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfc8a-105">參數</span><span class="sxs-lookup"><span data-stu-id="dfc8a-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="dfc8a-106">脫銷包含這個[ICorDebugVariableHome](icordebugvariablehome-interface.md)物件之 "ICorDebugCode" 實例位址的指標。</span><span class="sxs-lookup"><span data-stu-id="dfc8a-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfc8a-107">需求</span><span class="sxs-lookup"><span data-stu-id="dfc8a-107">Requirements</span></span>  
 <span data-ttu-id="dfc8a-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dfc8a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfc8a-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfc8a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfc8a-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfc8a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfc8a-111">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfc8a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfc8a-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="dfc8a-112">See also</span></span>

- [<span data-ttu-id="dfc8a-113">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="dfc8a-113">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
