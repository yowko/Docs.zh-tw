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
ms.openlocfilehash: 625609d8632f1f73ee2ec01e3b2e0e1af7e4a134
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085710"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="b625f-102">ISymUnmanagedScope::GetLocals 方法</span><span class="sxs-lookup"><span data-stu-id="b625f-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="b625f-103">取得此範圍內定義的本機變數。</span><span class="sxs-lookup"><span data-stu-id="b625f-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b625f-104">語法</span><span class="sxs-lookup"><span data-stu-id="b625f-104">Syntax</span></span>  
  
```  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b625f-105">參數</span><span class="sxs-lookup"><span data-stu-id="b625f-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="b625f-106">[in]A`ULONG32`表示的大小`locals`陣列。</span><span class="sxs-lookup"><span data-stu-id="b625f-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="b625f-107">[out]指標`ULONG32`接收包含本機變數所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="b625f-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="b625f-108">[out]接收的本機變數的陣列。</span><span class="sxs-lookup"><span data-stu-id="b625f-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b625f-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="b625f-109">Return Value</span></span>  
 <span data-ttu-id="b625f-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="b625f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b625f-111">需求</span><span class="sxs-lookup"><span data-stu-id="b625f-111">Requirements</span></span>  
 <span data-ttu-id="b625f-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b625f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b625f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b625f-113">See also</span></span>

- [<span data-ttu-id="b625f-114">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="b625f-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
