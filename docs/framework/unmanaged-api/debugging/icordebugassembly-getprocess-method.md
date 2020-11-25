---
title: ICorDebugAssembly::GetProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetProcess
helpviewer_keywords:
- ICorDebugAssembly::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: ea52be06-0a16-4f57-afca-4287d72e76c4
topic_type:
- apiref
ms.openlocfilehash: e8662535fb6f1aa812130d96e67678baa3c41a52
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734032"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="aec7b-102">ICorDebugAssembly::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="aec7b-102">ICorDebugAssembly::GetProcess Method</span></span>

<span data-ttu-id="aec7b-103">取得此 ICorDebugAssembly 實例執行所在之進程的介面指標。</span><span class="sxs-lookup"><span data-stu-id="aec7b-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aec7b-104">語法</span><span class="sxs-lookup"><span data-stu-id="aec7b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aec7b-105">參數</span><span class="sxs-lookup"><span data-stu-id="aec7b-105">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="aec7b-106">擴展表示處理常式之 ICorDebugProcess 介面的指標。</span><span class="sxs-lookup"><span data-stu-id="aec7b-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aec7b-107">需求</span><span class="sxs-lookup"><span data-stu-id="aec7b-107">Requirements</span></span>  

 <span data-ttu-id="aec7b-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aec7b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aec7b-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aec7b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aec7b-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aec7b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aec7b-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aec7b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
