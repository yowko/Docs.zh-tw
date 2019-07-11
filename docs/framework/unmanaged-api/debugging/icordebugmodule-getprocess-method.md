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
ms.openlocfilehash: ff7c77a27e9be58e9702c3a5e3f990863dc83901
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763632"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="fdb27-102">ICorDebugModule::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="fdb27-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="fdb27-103">取得包含此模組的處理序。</span><span class="sxs-lookup"><span data-stu-id="fdb27-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdb27-104">語法</span><span class="sxs-lookup"><span data-stu-id="fdb27-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdb27-105">參數</span><span class="sxs-lookup"><span data-stu-id="fdb27-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="fdb27-106">[out]ICorDebugProcess 物件，表示包含此模組的程序的位址指標。</span><span class="sxs-lookup"><span data-stu-id="fdb27-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdb27-107">需求</span><span class="sxs-lookup"><span data-stu-id="fdb27-107">Requirements</span></span>  
 <span data-ttu-id="fdb27-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fdb27-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdb27-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fdb27-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fdb27-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdb27-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdb27-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdb27-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
