---
title: ICorDebugFrame::GetCode 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7a4e8c6fa91ee43c33fe0f99d50bd4b1af4a0fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988776"
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="d1b1b-102">ICorDebugFrame::GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="d1b1b-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="d1b1b-103">取得此堆疊框架相關聯的程式碼的指標。</span><span class="sxs-lookup"><span data-stu-id="d1b1b-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1b1b-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1b1b-104">Syntax</span></span>  
  
```  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1b1b-105">參數</span><span class="sxs-lookup"><span data-stu-id="d1b1b-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="d1b1b-106">[out]ICorDebugCode 物件，表示與這個畫面格相關聯的程式碼的位址指標。</span><span class="sxs-lookup"><span data-stu-id="d1b1b-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1b1b-107">需求</span><span class="sxs-lookup"><span data-stu-id="d1b1b-107">Requirements</span></span>  
 <span data-ttu-id="d1b1b-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1b1b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1b1b-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1b1b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1b1b-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1b1b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1b1b-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1b1b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
