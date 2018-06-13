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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0d741bda5426dee1292df0e6fd9107cc2f44c8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413315"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="d518b-102">ICorDebugModule::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="d518b-102">ICorDebugModule::GetSize Method</span></span>
<span data-ttu-id="d518b-103">取得大小，以位元組為單位的模組。</span><span class="sxs-lookup"><span data-stu-id="d518b-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d518b-104">語法</span><span class="sxs-lookup"><span data-stu-id="d518b-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d518b-105">參數</span><span class="sxs-lookup"><span data-stu-id="d518b-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="d518b-106">[out]以位元組為單位之模組的大小。</span><span class="sxs-lookup"><span data-stu-id="d518b-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="d518b-107">如果從原生映像產生器 (NGen.exe) 產生的模組，模組的大小將是零。</span><span class="sxs-lookup"><span data-stu-id="d518b-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d518b-108">需求</span><span class="sxs-lookup"><span data-stu-id="d518b-108">Requirements</span></span>  
 <span data-ttu-id="d518b-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d518b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d518b-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d518b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d518b-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d518b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d518b-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d518b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
