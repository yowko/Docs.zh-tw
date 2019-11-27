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
ms.openlocfilehash: 38c4819a375cdd94ee31c2744871c600d8de0b40
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446000"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="d06c2-102">ISymUnmanagedVariable::GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="d06c2-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="d06c2-103">取得這個變數在其父系內的起始位移。</span><span class="sxs-lookup"><span data-stu-id="d06c2-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="d06c2-104">如果這是範圍內的區域變數，開始位移會落在為範圍定義的位移內。</span><span class="sxs-lookup"><span data-stu-id="d06c2-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d06c2-105">語法</span><span class="sxs-lookup"><span data-stu-id="d06c2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d06c2-106">參數</span><span class="sxs-lookup"><span data-stu-id="d06c2-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="d06c2-107">脫銷接收開始位移之 `ULONG32` 的指標。</span><span class="sxs-lookup"><span data-stu-id="d06c2-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d06c2-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="d06c2-108">Return Value</span></span>  
 <span data-ttu-id="d06c2-109">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d06c2-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d06c2-110">需求</span><span class="sxs-lookup"><span data-stu-id="d06c2-110">Requirements</span></span>  
 <span data-ttu-id="d06c2-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d06c2-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d06c2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d06c2-112">See also</span></span>

- [<span data-ttu-id="d06c2-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="d06c2-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="d06c2-114">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="d06c2-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
