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
ms.openlocfilehash: 50722bb855c8bc8bcfdc1b405a5bbc2fa057c52c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129524"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="a9a07-102">ICorDebugModule::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="a9a07-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="a9a07-103">取得此模組的包含進程。</span><span class="sxs-lookup"><span data-stu-id="a9a07-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9a07-104">語法</span><span class="sxs-lookup"><span data-stu-id="a9a07-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9a07-105">參數</span><span class="sxs-lookup"><span data-stu-id="a9a07-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="a9a07-106">脫銷ICorDebugProcess 物件位址的指標，表示包含此模組的進程。</span><span class="sxs-lookup"><span data-stu-id="a9a07-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9a07-107">需求</span><span class="sxs-lookup"><span data-stu-id="a9a07-107">Requirements</span></span>  
 <span data-ttu-id="a9a07-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a9a07-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9a07-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9a07-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9a07-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9a07-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9a07-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9a07-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
