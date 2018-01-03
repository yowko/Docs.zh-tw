---
title: "ICorDebugProcess2::GetDesiredNGENCompilerFlags 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7306174f6c60d814474d7f142da49a2a4013f19b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="de471-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="de471-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="de471-103">取得目前的編譯器，common language runtime (CLR) 用來選取正確的先行編譯的旗標設定 (也就是原生) 載入此處理序的映像。</span><span class="sxs-lookup"><span data-stu-id="de471-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de471-104">語法</span><span class="sxs-lookup"><span data-stu-id="de471-104">Syntax</span></span>  
  
```  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de471-105">參數</span><span class="sxs-lookup"><span data-stu-id="de471-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="de471-106">[out]指標的位元組合[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉值，用來選取要載入正確的先行編譯映像。</span><span class="sxs-lookup"><span data-stu-id="de471-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de471-107">備註</span><span class="sxs-lookup"><span data-stu-id="de471-107">Remarks</span></span>  
 <span data-ttu-id="de471-108">使用[icordebugprocess2:: Setdesiredngencompilerflags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)方法，以設定 CLR 將用來選取正確的先行編譯映像載入的旗標。</span><span class="sxs-lookup"><span data-stu-id="de471-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de471-109">需求</span><span class="sxs-lookup"><span data-stu-id="de471-109">Requirements</span></span>  
 <span data-ttu-id="de471-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="de471-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de471-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de471-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de471-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de471-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de471-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de471-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
