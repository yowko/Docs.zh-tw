---
title: ICorDebugILFrame::GetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd421d705a96778159cb80ad92d9ac654e88985f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414062"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="53b06-102">ICorDebugILFrame::GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="53b06-102">ICorDebugILFrame::GetIP Method</span></span>
<span data-ttu-id="53b06-103">取得指令指標的值以及說明如何取得指令指標的值的位元組合值。</span><span class="sxs-lookup"><span data-stu-id="53b06-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53b06-104">語法</span><span class="sxs-lookup"><span data-stu-id="53b06-104">Syntax</span></span>  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53b06-105">參數</span><span class="sxs-lookup"><span data-stu-id="53b06-105">Parameters</span></span>  
 `pnOffset`  
 <span data-ttu-id="53b06-106">[out]指令指標的值。</span><span class="sxs-lookup"><span data-stu-id="53b06-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="53b06-107">[out]CorDebugMappingResult 列舉值，描述如何取得指令指標的值的位元組合指標。</span><span class="sxs-lookup"><span data-stu-id="53b06-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53b06-108">備註</span><span class="sxs-lookup"><span data-stu-id="53b06-108">Remarks</span></span>  
 <span data-ttu-id="53b06-109">指令指標的值是函式的 Microsoft intermediate language (MSIL) 程式碼中堆疊框架的位移。</span><span class="sxs-lookup"><span data-stu-id="53b06-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="53b06-110">是否在作用中堆疊框架，此地址是要執行的下一個指令。</span><span class="sxs-lookup"><span data-stu-id="53b06-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="53b06-111">如果堆疊框架不是作用中，此位址就是下一個堆疊框架就會重新啟動時要執行指令。</span><span class="sxs-lookup"><span data-stu-id="53b06-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="53b06-112">如果這是在 just-in-time (JIT) 編譯的框架，指令指標的值取決於從實際的原生指令指標使用，因此值可能只是近似反向對應。</span><span class="sxs-lookup"><span data-stu-id="53b06-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53b06-113">需求</span><span class="sxs-lookup"><span data-stu-id="53b06-113">Requirements</span></span>  
 <span data-ttu-id="53b06-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53b06-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53b06-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53b06-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53b06-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53b06-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53b06-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53b06-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
