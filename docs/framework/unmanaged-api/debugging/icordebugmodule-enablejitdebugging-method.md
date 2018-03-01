---
title: "ICorDebugModule::EnableJITDebugging 方法"
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
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7a699f32d8ec4b2418c6af815c22f35470bede3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="0ce8d-102">ICorDebugModule::EnableJITDebugging 方法</span><span class="sxs-lookup"><span data-stu-id="0ce8d-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="0ce8d-103">控制是否在 just-in-time (JIT) 編譯器會保留在這個模組中方法的偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="0ce8d-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ce8d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ce8d-104">Syntax</span></span>  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ce8d-105">參數</span><span class="sxs-lookup"><span data-stu-id="0ce8d-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="0ce8d-106">[in]將此值設定為`true`以啟用 JIT 編譯器保留的 Microsoft intermediate language (MSIL) 版本與此模組中的每個方法的 JIT 編譯版本之間的對應資訊。</span><span class="sxs-lookup"><span data-stu-id="0ce8d-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="0ce8d-107">[in]將此值設定為`true`以啟用 JIT 編譯器產生的程式碼與偵錯特定特定的 JIT 最佳化。</span><span class="sxs-lookup"><span data-stu-id="0ce8d-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ce8d-108">備註</span><span class="sxs-lookup"><span data-stu-id="0ce8d-108">Remarks</span></span>  
 <span data-ttu-id="0ce8d-109">偵錯工具為作用中時，會載入的所有模組的預設會啟用 JIT 偵錯。</span><span class="sxs-lookup"><span data-stu-id="0ce8d-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="0ce8d-110">以程式設計方式啟用或停用這些設定會覆寫全域設定。</span><span class="sxs-lookup"><span data-stu-id="0ce8d-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ce8d-111">需求</span><span class="sxs-lookup"><span data-stu-id="0ce8d-111">Requirements</span></span>  
 <span data-ttu-id="0ce8d-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ce8d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ce8d-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ce8d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ce8d-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ce8d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ce8d-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ce8d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
