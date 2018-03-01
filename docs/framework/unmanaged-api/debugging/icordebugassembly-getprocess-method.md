---
title: "ICorDebugAssembly::GetProcess 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fbb62bb6d2731c5bc2618de0a71f75e0979808c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="83886-102">ICorDebugAssembly::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="83886-102">ICorDebugAssembly::GetProcess Method</span></span>
<span data-ttu-id="83886-103">取得這個 ICorDebugAssembly 執行個體正在執行的程序的介面指標。</span><span class="sxs-lookup"><span data-stu-id="83886-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83886-104">語法</span><span class="sxs-lookup"><span data-stu-id="83886-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83886-105">參數</span><span class="sxs-lookup"><span data-stu-id="83886-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="83886-106">[out]ICorDebugProcess 介面代表程序的指標。</span><span class="sxs-lookup"><span data-stu-id="83886-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83886-107">需求</span><span class="sxs-lookup"><span data-stu-id="83886-107">Requirements</span></span>  
 <span data-ttu-id="83886-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83886-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83886-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83886-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83886-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83886-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83886-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83886-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
