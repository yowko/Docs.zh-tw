---
title: "ICorDebugCode2::GetCompilerFlags 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode2.GetCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode2::GetCompilerFlags
helpviewer_keywords:
- GetCompilerFlags method [.NET Framework debugging]
- ICorDebugCode2::GetCompilerFlags method [.NET Framework debugging]
ms.assetid: 532e9dfd-d114-4c75-b952-1accce102643
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42a4b8e54bd1ca7706be7e23653681430fb41a8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcode2getcompilerflags-method"></a><span data-ttu-id="34f2a-102">ICorDebugCode2::GetCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="34f2a-102">ICorDebugCode2::GetCompilerFlags Method</span></span>
<span data-ttu-id="34f2a-103">取得指定的程式碼已此物件可能是在 just-in-time (JIT) 編譯，或使用原生映像產生器 (Ngen.exe) 產生之條件的旗標。</span><span class="sxs-lookup"><span data-stu-id="34f2a-103">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34f2a-104">語法</span><span class="sxs-lookup"><span data-stu-id="34f2a-104">Syntax</span></span>  
  
```  
HRESULT GetCompilerFlags (  
    [out] DWORD *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34f2a-105">參數</span><span class="sxs-lookup"><span data-stu-id="34f2a-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="34f2a-106">[out]值的指標[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列舉，指定 JIT 編譯器或原生映像產生器的行為。</span><span class="sxs-lookup"><span data-stu-id="34f2a-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the behavior of the JIT compiler or the native image generator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34f2a-107">需求</span><span class="sxs-lookup"><span data-stu-id="34f2a-107">Requirements</span></span>  
 <span data-ttu-id="34f2a-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="34f2a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34f2a-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34f2a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34f2a-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34f2a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34f2a-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34f2a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34f2a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34f2a-112">See Also</span></span>  
 
