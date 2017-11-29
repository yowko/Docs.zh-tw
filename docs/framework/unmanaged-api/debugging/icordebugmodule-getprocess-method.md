---
title: "ICorDebugModule::GetProcess 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetProcess method [.NET Framework debugging]
ms.assetid: 5e13446c-0271-446c-924a-9072c0e6eeae
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8770a4978ba0410d6df825320446f4ea4817e04a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="ef849-102">ICorDebugModule::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="ef849-102">ICorDebugModule::GetProcess Method</span></span>
<span data-ttu-id="ef849-103">取得包含此模組的處理序。</span><span class="sxs-lookup"><span data-stu-id="ef849-103">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef849-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef849-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef849-105">參數</span><span class="sxs-lookup"><span data-stu-id="ef849-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="ef849-106">[out]ICorDebugProcess 物件，代表包含此模組的程序的位址指標。</span><span class="sxs-lookup"><span data-stu-id="ef849-106">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef849-107">需求</span><span class="sxs-lookup"><span data-stu-id="ef849-107">Requirements</span></span>  
 <span data-ttu-id="ef849-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ef849-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef849-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef849-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef849-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef849-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef849-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef849-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
