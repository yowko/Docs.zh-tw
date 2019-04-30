---
title: ICorDebugModule::GetProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetProcess method [.NET Framework debugging]
ms.assetid: 5e13446c-0271-446c-924a-9072c0e6eeae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97cecd66462cf6a88012b13dec82dbf617891dd5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987996"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="e88f9-102">ICorDebugModule::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="e88f9-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="e88f9-103">取得包含此模組的處理序。</span><span class="sxs-lookup"><span data-stu-id="e88f9-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e88f9-104">語法</span><span class="sxs-lookup"><span data-stu-id="e88f9-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e88f9-105">參數</span><span class="sxs-lookup"><span data-stu-id="e88f9-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="e88f9-106">[out]ICorDebugProcess 物件，表示包含此模組的程序的位址指標。</span><span class="sxs-lookup"><span data-stu-id="e88f9-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e88f9-107">需求</span><span class="sxs-lookup"><span data-stu-id="e88f9-107">Requirements</span></span>  
 <span data-ttu-id="e88f9-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e88f9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e88f9-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e88f9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e88f9-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e88f9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e88f9-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e88f9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
