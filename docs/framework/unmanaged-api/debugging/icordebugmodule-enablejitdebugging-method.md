---
title: ICorDebugModule::EnableJITDebugging 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 642c4fd600d10ef89a08aa32bef5c8e7455552c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937172"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="e5c79-102">ICorDebugModule::EnableJITDebugging 方法</span><span class="sxs-lookup"><span data-stu-id="e5c79-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="e5c79-103">控制在 just-in-time (JIT) 編譯器是否會保留在這個模組中方法的偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="e5c79-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5c79-104">語法</span><span class="sxs-lookup"><span data-stu-id="e5c79-104">Syntax</span></span>  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5c79-105">參數</span><span class="sxs-lookup"><span data-stu-id="e5c79-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="e5c79-106">[in]將此值設定為`true`若要啟用 JIT 編譯器保留的 Microsoft intermediate language (MSIL) 版本和 JIT 編譯的版本在此模組中的每個方法之間的對應資訊。</span><span class="sxs-lookup"><span data-stu-id="e5c79-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="e5c79-107">[in]將此值設定為`true`若要啟用 JIT 編譯器產生偵錯特定 JIT 特定最佳化的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e5c79-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5c79-108">備註</span><span class="sxs-lookup"><span data-stu-id="e5c79-108">Remarks</span></span>  
 <span data-ttu-id="e5c79-109">啟用偵錯工具時載入的所有模組的預設會啟用 JIT 偵錯。</span><span class="sxs-lookup"><span data-stu-id="e5c79-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="e5c79-110">以程式設計方式啟用或停用這些設定會覆寫全域設定。</span><span class="sxs-lookup"><span data-stu-id="e5c79-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5c79-111">需求</span><span class="sxs-lookup"><span data-stu-id="e5c79-111">Requirements</span></span>  
 <span data-ttu-id="e5c79-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e5c79-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5c79-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5c79-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5c79-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5c79-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5c79-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5c79-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
