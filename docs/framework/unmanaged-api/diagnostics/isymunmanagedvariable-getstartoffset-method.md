---
title: ISymUnmanagedVariable::GetStartOffset 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f551e2f8a89cf2988ce43bf72a1e87e0ddaf713
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543207"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="a409a-102">ISymUnmanagedVariable::GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="a409a-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="a409a-103">取得這個變數，其父系內的起始位移。</span><span class="sxs-lookup"><span data-stu-id="a409a-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="a409a-104">如果這是本機變數的範圍內，起始位移會落在定義範圍的位移。</span><span class="sxs-lookup"><span data-stu-id="a409a-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a409a-105">語法</span><span class="sxs-lookup"><span data-stu-id="a409a-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a409a-106">參數</span><span class="sxs-lookup"><span data-stu-id="a409a-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a409a-107">[out]指標`ULONG32`接收的開始位移。</span><span class="sxs-lookup"><span data-stu-id="a409a-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a409a-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a409a-108">Return Value</span></span>  
 <span data-ttu-id="a409a-109">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="a409a-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a409a-110">需求</span><span class="sxs-lookup"><span data-stu-id="a409a-110">Requirements</span></span>  
 <span data-ttu-id="a409a-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a409a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a409a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a409a-112">See also</span></span>
- [<span data-ttu-id="a409a-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="a409a-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="a409a-114">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="a409a-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
