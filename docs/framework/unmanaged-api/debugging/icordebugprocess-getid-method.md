---
title: ICorDebugProcess::GetID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetID
helpviewer_keywords:
- GetID method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetID method [.NET Framework debugging]
ms.assetid: b0ba8453-fa7e-4c14-93e5-335409cd4a47
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d752eb17b956e2367e8b191080a370506a61ff34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416663"
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="3e1e1-102">ICorDebugProcess::GetID 方法</span><span class="sxs-lookup"><span data-stu-id="3e1e1-102">ICorDebugProcess::GetID Method</span></span>
<span data-ttu-id="3e1e1-103">取得處理序的作業系統 (OS) 識別碼。</span><span class="sxs-lookup"><span data-stu-id="3e1e1-103">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e1e1-104">語法</span><span class="sxs-lookup"><span data-stu-id="3e1e1-104">Syntax</span></span>  
  
```  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e1e1-105">參數</span><span class="sxs-lookup"><span data-stu-id="3e1e1-105">Parameters</span></span>  
 `pdwProcessId`  
 <span data-ttu-id="3e1e1-106">[out]處理序的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="3e1e1-106">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e1e1-107">需求</span><span class="sxs-lookup"><span data-stu-id="3e1e1-107">Requirements</span></span>  
 <span data-ttu-id="3e1e1-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e1e1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e1e1-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e1e1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e1e1-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e1e1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e1e1-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e1e1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
