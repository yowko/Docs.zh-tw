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
ms.openlocfilehash: da532ee1b5909a68bedbb9e6f6c96333e88002a8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109719"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="0e5d1-102">ICorDebugModule::EnableJITDebugging 方法</span><span class="sxs-lookup"><span data-stu-id="0e5d1-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="0e5d1-103">控制即時（JIT）編譯器是否保留此模組內之方法的偵錯工具資訊。</span><span class="sxs-lookup"><span data-stu-id="0e5d1-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e5d1-104">語法</span><span class="sxs-lookup"><span data-stu-id="0e5d1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e5d1-105">參數</span><span class="sxs-lookup"><span data-stu-id="0e5d1-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="0e5d1-106">在將此值設定為 `true`，讓 JIT 編譯程式能夠保留此模組中每個方法的 Microsoft 中繼語言（MSIL）版本與 JIT 編譯版本之間的對應資訊。</span><span class="sxs-lookup"><span data-stu-id="0e5d1-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="0e5d1-107">在將此值設定為 `true`，讓 JIT 編譯程式能夠使用特定的 JIT 特定優化來產生程式碼以進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="0e5d1-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e5d1-108">備註</span><span class="sxs-lookup"><span data-stu-id="0e5d1-108">Remarks</span></span>  
 <span data-ttu-id="0e5d1-109">當偵錯工具作用中時，所有載入的模組預設會啟用 JIT 偵錯程式。</span><span class="sxs-lookup"><span data-stu-id="0e5d1-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="0e5d1-110">以程式設計方式啟用或停用設定會覆寫全域設定。</span><span class="sxs-lookup"><span data-stu-id="0e5d1-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e5d1-111">需求</span><span class="sxs-lookup"><span data-stu-id="0e5d1-111">Requirements</span></span>  
 <span data-ttu-id="0e5d1-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0e5d1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e5d1-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e5d1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e5d1-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e5d1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e5d1-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e5d1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
