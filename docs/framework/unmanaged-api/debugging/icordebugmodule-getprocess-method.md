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
ms.openlocfilehash: c10c45c4450e02d633ebeeca15da95b7c95ff0b4
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212525"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="7b4fa-102">ICorDebugModule::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="7b4fa-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="7b4fa-103">取得此模組的包含進程。</span><span class="sxs-lookup"><span data-stu-id="7b4fa-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b4fa-104">語法</span><span class="sxs-lookup"><span data-stu-id="7b4fa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b4fa-105">參數</span><span class="sxs-lookup"><span data-stu-id="7b4fa-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="7b4fa-106">脫銷ICorDebugProcess 物件位址的指標，表示包含此模組的進程。</span><span class="sxs-lookup"><span data-stu-id="7b4fa-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b4fa-107">需求</span><span class="sxs-lookup"><span data-stu-id="7b4fa-107">Requirements</span></span>  
 <span data-ttu-id="7b4fa-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7b4fa-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b4fa-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b4fa-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b4fa-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b4fa-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b4fa-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b4fa-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
