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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1c3bcc0ed22fa970d92e2384277d0786016db19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402105"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="f74d7-102">ICorDebugAssembly::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="f74d7-102">ICorDebugAssembly::GetProcess Method</span></span>
<span data-ttu-id="f74d7-103">取得這個 ICorDebugAssembly 執行個體正在執行的程序的介面指標。</span><span class="sxs-lookup"><span data-stu-id="f74d7-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f74d7-104">語法</span><span class="sxs-lookup"><span data-stu-id="f74d7-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f74d7-105">參數</span><span class="sxs-lookup"><span data-stu-id="f74d7-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="f74d7-106">[out]ICorDebugProcess 介面代表程序的指標。</span><span class="sxs-lookup"><span data-stu-id="f74d7-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f74d7-107">需求</span><span class="sxs-lookup"><span data-stu-id="f74d7-107">Requirements</span></span>  
 <span data-ttu-id="f74d7-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f74d7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f74d7-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f74d7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f74d7-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f74d7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f74d7-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f74d7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
