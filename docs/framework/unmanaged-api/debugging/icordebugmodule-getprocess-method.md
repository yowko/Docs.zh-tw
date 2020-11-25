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
ms.openlocfilehash: 8f4b9e73e0d716561dd64bc0df702d835e0eee06
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709956"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="b0ac0-102">ICorDebugModule::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="b0ac0-102">ICorDebugModule::GetProcess Method</span></span>

<span data-ttu-id="b0ac0-103">取得此模組的包含處理常式。</span><span class="sxs-lookup"><span data-stu-id="b0ac0-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0ac0-104">語法</span><span class="sxs-lookup"><span data-stu-id="b0ac0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0ac0-105">參數</span><span class="sxs-lookup"><span data-stu-id="b0ac0-105">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="b0ac0-106">擴展ICorDebugProcess 物件位址的指標，代表包含此模組的進程。</span><span class="sxs-lookup"><span data-stu-id="b0ac0-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0ac0-107">需求</span><span class="sxs-lookup"><span data-stu-id="b0ac0-107">Requirements</span></span>  

 <span data-ttu-id="b0ac0-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b0ac0-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0ac0-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0ac0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0ac0-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0ac0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0ac0-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0ac0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
