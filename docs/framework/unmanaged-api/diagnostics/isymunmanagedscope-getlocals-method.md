---
title: ISymUnmanagedScope::GetLocals 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocals
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocals
helpviewer_keywords:
- GetLocals method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocals method [.NET Framework debugging]
ms.assetid: 17c45f15-8c44-44da-b070-f902077b36e4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 781111db30ae664c9dd45744f88387e161f2716f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426795"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="d870e-102">ISymUnmanagedScope::GetLocals 方法</span><span class="sxs-lookup"><span data-stu-id="d870e-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="d870e-103">取得此範圍內定義的本機變數。</span><span class="sxs-lookup"><span data-stu-id="d870e-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d870e-104">語法</span><span class="sxs-lookup"><span data-stu-id="d870e-104">Syntax</span></span>  
  
```  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d870e-105">參數</span><span class="sxs-lookup"><span data-stu-id="d870e-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="d870e-106">[in]A`ULONG32`指出的大小`locals`陣列。</span><span class="sxs-lookup"><span data-stu-id="d870e-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="d870e-107">[out]指標`ULONG32`包含本機變數所需要的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="d870e-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="d870e-108">[out]接收的本機變數的陣列。</span><span class="sxs-lookup"><span data-stu-id="d870e-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d870e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="d870e-109">Return Value</span></span>  
 <span data-ttu-id="d870e-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="d870e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d870e-111">需求</span><span class="sxs-lookup"><span data-stu-id="d870e-111">Requirements</span></span>  
 <span data-ttu-id="d870e-112">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d870e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d870e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d870e-113">See Also</span></span>  
 [<span data-ttu-id="d870e-114">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="d870e-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
