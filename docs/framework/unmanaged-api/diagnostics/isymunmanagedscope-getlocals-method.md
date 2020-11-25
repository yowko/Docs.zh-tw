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
ms.openlocfilehash: 3a2045466340f92dd8421090c74a442068e8bfaf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731406"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="dba8a-102">ISymUnmanagedScope::GetLocals 方法</span><span class="sxs-lookup"><span data-stu-id="dba8a-102">ISymUnmanagedScope::GetLocals Method</span></span>

<span data-ttu-id="dba8a-103">取得在此範圍內定義的本機變數。</span><span class="sxs-lookup"><span data-stu-id="dba8a-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba8a-104">語法</span><span class="sxs-lookup"><span data-stu-id="dba8a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dba8a-105">參數</span><span class="sxs-lookup"><span data-stu-id="dba8a-105">Parameters</span></span>  

 `cLocals`  
 <span data-ttu-id="dba8a-106">在 `ULONG32` ，指出陣列的大小 `locals` 。</span><span class="sxs-lookup"><span data-stu-id="dba8a-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="dba8a-107">擴展的指標 `ULONG32` ，會接收包含區域變數所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="dba8a-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="dba8a-108">擴展接收本機變數的陣列。</span><span class="sxs-lookup"><span data-stu-id="dba8a-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dba8a-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="dba8a-109">Return Value</span></span>  

 <span data-ttu-id="dba8a-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="dba8a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dba8a-111">需求</span><span class="sxs-lookup"><span data-stu-id="dba8a-111">Requirements</span></span>  

 <span data-ttu-id="dba8a-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="dba8a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba8a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dba8a-113">See also</span></span>

- [<span data-ttu-id="dba8a-114">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="dba8a-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
