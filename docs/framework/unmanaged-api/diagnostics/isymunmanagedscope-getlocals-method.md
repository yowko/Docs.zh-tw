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
ms.openlocfilehash: 0acd31d85504688427cace0222a657885035c537
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615380"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="221bd-102">ISymUnmanagedScope::GetLocals 方法</span><span class="sxs-lookup"><span data-stu-id="221bd-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="221bd-103">取得在此範圍內定義的區域變數。</span><span class="sxs-lookup"><span data-stu-id="221bd-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="221bd-104">語法</span><span class="sxs-lookup"><span data-stu-id="221bd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="221bd-105">參數</span><span class="sxs-lookup"><span data-stu-id="221bd-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="221bd-106">在`ULONG32`，指出陣列的大小 `locals` 。</span><span class="sxs-lookup"><span data-stu-id="221bd-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="221bd-107">脫銷的指標 `ULONG32` ，接收包含區域變數所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="221bd-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="221bd-108">脫銷接收本機變數的陣列。</span><span class="sxs-lookup"><span data-stu-id="221bd-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="221bd-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="221bd-109">Return Value</span></span>  
 <span data-ttu-id="221bd-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="221bd-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="221bd-111">需求</span><span class="sxs-lookup"><span data-stu-id="221bd-111">Requirements</span></span>  
 <span data-ttu-id="221bd-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="221bd-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="221bd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="221bd-113">See also</span></span>

- [<span data-ttu-id="221bd-114">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="221bd-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
