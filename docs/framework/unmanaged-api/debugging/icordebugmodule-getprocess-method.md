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
ms.openlocfilehash: add7239feb1cf6dab0fabe12e178336921211190
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414202"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="0bc3a-102">ICorDebugModule::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="0bc3a-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="0bc3a-103">取得包含此模組的處理序。</span><span class="sxs-lookup"><span data-stu-id="0bc3a-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bc3a-104">語法</span><span class="sxs-lookup"><span data-stu-id="0bc3a-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0bc3a-105">參數</span><span class="sxs-lookup"><span data-stu-id="0bc3a-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="0bc3a-106">[out]ICorDebugProcess 物件，代表包含此模組的程序的位址指標。</span><span class="sxs-lookup"><span data-stu-id="0bc3a-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bc3a-107">需求</span><span class="sxs-lookup"><span data-stu-id="0bc3a-107">Requirements</span></span>  
 <span data-ttu-id="0bc3a-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0bc3a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bc3a-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0bc3a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bc3a-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bc3a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bc3a-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bc3a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
