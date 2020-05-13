---
title: ICorDebugModule::GetSize 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetSize method [.NET Framework debugging]
ms.assetid: 5c68375d-145d-46ef-a7c8-2dc4257472de
topic_type:
- apiref
ms.openlocfilehash: 4f9818137016dc3e0522ed516c52df2550ffdfca
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212512"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="d641a-102">ICorDebugModule::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="d641a-102">ICorDebugModule::GetSize Method</span></span>
<span data-ttu-id="d641a-103">取得模組的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="d641a-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d641a-104">語法</span><span class="sxs-lookup"><span data-stu-id="d641a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d641a-105">參數</span><span class="sxs-lookup"><span data-stu-id="d641a-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="d641a-106">脫銷模組的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="d641a-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="d641a-107">如果模組是從原生映射產生器（Ngen.exe）所產生，則模組的大小會是零。</span><span class="sxs-lookup"><span data-stu-id="d641a-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d641a-108">需求</span><span class="sxs-lookup"><span data-stu-id="d641a-108">Requirements</span></span>  
 <span data-ttu-id="d641a-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d641a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d641a-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d641a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d641a-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d641a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d641a-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d641a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
