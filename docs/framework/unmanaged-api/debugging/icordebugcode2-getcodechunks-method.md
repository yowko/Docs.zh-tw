---
title: ICorDebugCode2::GetCodeChunks 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf8bc747f643819eb82448b4ad6b7fab696c9c91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572496"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="48aca-102">ICorDebugCode2::GetCodeChunks 方法</span><span class="sxs-lookup"><span data-stu-id="48aca-102">ICorDebugCode2::GetCodeChunks Method</span></span>
<span data-ttu-id="48aca-103">取得這個程式碼物件組成的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="48aca-103">Gets the chunks of code that this code object is composed of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48aca-104">語法</span><span class="sxs-lookup"><span data-stu-id="48aca-104">Syntax</span></span>  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48aca-105">參數</span><span class="sxs-lookup"><span data-stu-id="48aca-105">Parameters</span></span>  
 `cbufSize`  
 <span data-ttu-id="48aca-106">[in]大小`chunks`陣列。</span><span class="sxs-lookup"><span data-stu-id="48aca-106">[in] Size of the `chunks` array.</span></span>  
  
 `pcnumChunks`  
 <span data-ttu-id="48aca-107">[out]傳入的區塊數目`chunks`陣列。</span><span class="sxs-lookup"><span data-stu-id="48aca-107">[out] The number of chunks returned in the `chunks` array.</span></span>  
  
 `chunks`  
 <span data-ttu-id="48aca-108">[out]結構的陣列 」 CodeChunkInfo 」，每一個都代表單一的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="48aca-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="48aca-109">如果值`cbufSize`為 0，這個參數可以是 null。</span><span class="sxs-lookup"><span data-stu-id="48aca-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48aca-110">備註</span><span class="sxs-lookup"><span data-stu-id="48aca-110">Remarks</span></span>  
 <span data-ttu-id="48aca-111">程式碼區塊 （chunk） 將會永遠不會重疊，以及它們會依的序執行所在串連這些區塊會有已由[icordebugcode:: Getcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)。</span><span class="sxs-lookup"><span data-stu-id="48aca-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="48aca-112">在.NET Framework 2.0 版的 Microsoft intermediate language (MSIL) 程式碼物件會構成單一的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="48aca-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48aca-113">需求</span><span class="sxs-lookup"><span data-stu-id="48aca-113">Requirements</span></span>  
 <span data-ttu-id="48aca-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="48aca-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48aca-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48aca-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48aca-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48aca-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48aca-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48aca-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48aca-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48aca-118">See also</span></span>

