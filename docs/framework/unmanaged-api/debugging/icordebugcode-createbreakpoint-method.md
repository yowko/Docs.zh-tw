---
title: ICorDebugCode::CreateBreakpoint 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.CreateBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d193f9aa4d051baa73944545d28a455495aeda40
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185766"
---
# <a name="icordebugcodecreatebreakpoint-method"></a><span data-ttu-id="b4572-102">ICorDebugCode::CreateBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="b4572-102">ICorDebugCode::CreateBreakpoint Method</span></span>
<span data-ttu-id="b4572-103">建立指定之位移此程式碼區段中的中斷點。</span><span class="sxs-lookup"><span data-stu-id="b4572-103">Creates a breakpoint in this code segment at the specified offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4572-104">語法</span><span class="sxs-lookup"><span data-stu-id="b4572-104">Syntax</span></span>  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4572-105">參數</span><span class="sxs-lookup"><span data-stu-id="b4572-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="b4572-106">[in]要建立的中斷點處的位移。</span><span class="sxs-lookup"><span data-stu-id="b4572-106">[in] The offset at which to create the breakpoint.</span></span>  
  
 `ppBreakpoint`  
 <span data-ttu-id="b4572-107">[out]「 ICorDebugFunctionBreakpoint 」 物件，表示中斷點的位址指標。</span><span class="sxs-lookup"><span data-stu-id="b4572-107">[out] A pointer to the address of an "ICorDebugFunctionBreakpoint" object that represents the breakpoint.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4572-108">備註</span><span class="sxs-lookup"><span data-stu-id="b4572-108">Remarks</span></span>  
 <span data-ttu-id="b4572-109">中斷點為作用中之前，必須先新增至處理程序物件。</span><span class="sxs-lookup"><span data-stu-id="b4572-109">Before the breakpoint is active, it must be added to the process object.</span></span>  
  
 <span data-ttu-id="b4572-110">如果此程式碼是 Microsoft intermediate language (MSIL) 程式碼，而且沒有在 just-in-time (JIT)-JIT 編譯程式碼中也將套用原生編譯版本的程式碼中斷點。</span><span class="sxs-lookup"><span data-stu-id="b4572-110">If this code is Microsoft intermediate language (MSIL) code, and there is a just-in-time (JIT)-compiled, native version of the code, the breakpoint will be applied in the JIT-compiled code as well.</span></span> <span data-ttu-id="b4572-111">（這也為 true，如果程式碼為 JIT 編譯更新版本。）</span><span class="sxs-lookup"><span data-stu-id="b4572-111">(The same is true if the code is JIT-compiled later.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4572-112">需求</span><span class="sxs-lookup"><span data-stu-id="b4572-112">Requirements</span></span>  
 <span data-ttu-id="b4572-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4572-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4572-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4572-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4572-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4572-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b4572-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="b4572-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b4572-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4572-117">See also</span></span>
