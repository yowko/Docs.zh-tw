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
ms.openlocfilehash: bf932b63973f93c56883f099ddaadd9d1519f337
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446325"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="6ea0d-102">ISymUnmanagedScope::GetLocals 方法</span><span class="sxs-lookup"><span data-stu-id="6ea0d-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="6ea0d-103">取得在此範圍內定義的區域變數。</span><span class="sxs-lookup"><span data-stu-id="6ea0d-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ea0d-104">語法</span><span class="sxs-lookup"><span data-stu-id="6ea0d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ea0d-105">參數</span><span class="sxs-lookup"><span data-stu-id="6ea0d-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="6ea0d-106">在表示 `locals` 陣列大小的 `ULONG32`。</span><span class="sxs-lookup"><span data-stu-id="6ea0d-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="6ea0d-107">脫銷`ULONG32` 的指標，接收包含本機變數所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="6ea0d-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="6ea0d-108">脫銷接收本機變數的陣列。</span><span class="sxs-lookup"><span data-stu-id="6ea0d-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ea0d-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6ea0d-109">Return Value</span></span>  
 <span data-ttu-id="6ea0d-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="6ea0d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ea0d-111">需求</span><span class="sxs-lookup"><span data-stu-id="6ea0d-111">Requirements</span></span>  
 <span data-ttu-id="6ea0d-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="6ea0d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ea0d-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="6ea0d-113">See also</span></span>

- [<span data-ttu-id="6ea0d-114">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="6ea0d-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
