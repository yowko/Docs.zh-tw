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
ms.openlocfilehash: ca64e392b930ed57691f05ae771bbaf305df8eb3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754070"
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="847da-102">ICorDebugFrame::GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="847da-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="847da-103">取得此堆疊框架相關聯的程式碼的指標。</span><span class="sxs-lookup"><span data-stu-id="847da-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="847da-104">語法</span><span class="sxs-lookup"><span data-stu-id="847da-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="847da-105">參數</span><span class="sxs-lookup"><span data-stu-id="847da-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="847da-106">[out]ICorDebugCode 物件，表示與這個畫面格相關聯的程式碼的位址指標。</span><span class="sxs-lookup"><span data-stu-id="847da-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="847da-107">需求</span><span class="sxs-lookup"><span data-stu-id="847da-107">Requirements</span></span>  
 <span data-ttu-id="847da-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="847da-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="847da-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="847da-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="847da-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="847da-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="847da-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="847da-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
