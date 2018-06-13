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
ms.openlocfilehash: 15206fbd7724383b1ec6df123790d3171e58e9f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411914"
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="d3383-102">ICorDebugFrame::GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="d3383-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="d3383-103">取得此堆疊框架相關聯的程式碼的指標。</span><span class="sxs-lookup"><span data-stu-id="d3383-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3383-104">語法</span><span class="sxs-lookup"><span data-stu-id="d3383-104">Syntax</span></span>  
  
```  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3383-105">參數</span><span class="sxs-lookup"><span data-stu-id="d3383-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="d3383-106">[out]ICorDebugCode 物件，表示這個畫面格相關聯的程式碼的位址指標。</span><span class="sxs-lookup"><span data-stu-id="d3383-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3383-107">需求</span><span class="sxs-lookup"><span data-stu-id="d3383-107">Requirements</span></span>  
 <span data-ttu-id="d3383-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3383-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3383-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3383-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3383-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3383-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3383-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3383-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
