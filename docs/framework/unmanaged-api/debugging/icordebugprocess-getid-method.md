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
ms.openlocfilehash: 8cd40ffb60bf837a9aa3b0db34892350a05964d7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213279"
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="491fc-102">ICorDebugProcess::GetID 方法</span><span class="sxs-lookup"><span data-stu-id="491fc-102">ICorDebugProcess::GetID Method</span></span>
<span data-ttu-id="491fc-103">取得進程的作業系統（OS）識別碼。</span><span class="sxs-lookup"><span data-stu-id="491fc-103">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="491fc-104">語法</span><span class="sxs-lookup"><span data-stu-id="491fc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="491fc-105">參數</span><span class="sxs-lookup"><span data-stu-id="491fc-105">Parameters</span></span>  
 `pdwProcessId`  
 <span data-ttu-id="491fc-106">脫銷進程的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="491fc-106">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="491fc-107">需求</span><span class="sxs-lookup"><span data-stu-id="491fc-107">Requirements</span></span>  
 <span data-ttu-id="491fc-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="491fc-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="491fc-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="491fc-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="491fc-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="491fc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="491fc-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="491fc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
