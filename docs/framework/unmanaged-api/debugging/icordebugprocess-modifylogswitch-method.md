---
title: ICorDebugProcess::ModifyLogSwitch 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ModifyLogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ModifyLogSwitch
helpviewer_keywords:
- ICorDebugProcess::ModifyLogSwitch method [.NET Framework debugging]
- ModifyLogSwitch method [.NET Framework debugging]
ms.assetid: 5fd30875-555e-4e96-877b-5dd266cde7c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20ceed164631169b3a47809381b2cc4e630ae718
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418613"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="5c7f4-102">ICorDebugProcess::ModifyLogSwitch 方法</span><span class="sxs-lookup"><span data-stu-id="5c7f4-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>
<span data-ttu-id="5c7f4-103">設定參數，因為指定的記錄檔的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="5c7f4-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c7f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="5c7f4-104">Syntax</span></span>  
  
```  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c7f4-105">參數</span><span class="sxs-lookup"><span data-stu-id="5c7f4-105">Parameters</span></span>  
 `pLogSwitchName`  
 <span data-ttu-id="5c7f4-106">[in]指定記錄參數名稱的字串指標。</span><span class="sxs-lookup"><span data-stu-id="5c7f4-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="5c7f4-107">[in]嚴重性層級設為指定的記錄參數。</span><span class="sxs-lookup"><span data-stu-id="5c7f4-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c7f4-108">備註</span><span class="sxs-lookup"><span data-stu-id="5c7f4-108">Remarks</span></span>  
 <span data-ttu-id="5c7f4-109">這個方法是之後才有效[icordebugmanagedcallback:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回呼發生。</span><span class="sxs-lookup"><span data-stu-id="5c7f4-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c7f4-110">需求</span><span class="sxs-lookup"><span data-stu-id="5c7f4-110">Requirements</span></span>  
 <span data-ttu-id="5c7f4-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c7f4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c7f4-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c7f4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c7f4-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c7f4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c7f4-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c7f4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
