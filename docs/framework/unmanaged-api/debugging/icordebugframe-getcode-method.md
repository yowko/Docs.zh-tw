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
ms.openlocfilehash: c8914ba1090ec5fd6540e9ead302675cb44f37e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208599"
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="84f3d-102">ICorDebugFrame::GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="84f3d-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="84f3d-103">取得與這個堆疊框架相關聯之程式碼的指標。</span><span class="sxs-lookup"><span data-stu-id="84f3d-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84f3d-104">語法</span><span class="sxs-lookup"><span data-stu-id="84f3d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84f3d-105">參數</span><span class="sxs-lookup"><span data-stu-id="84f3d-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="84f3d-106">脫銷ICorDebugCode 物件位址的指標，表示與此框架相關聯的程式碼。</span><span class="sxs-lookup"><span data-stu-id="84f3d-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84f3d-107">需求</span><span class="sxs-lookup"><span data-stu-id="84f3d-107">Requirements</span></span>  
 <span data-ttu-id="84f3d-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84f3d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84f3d-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84f3d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84f3d-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84f3d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84f3d-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84f3d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
