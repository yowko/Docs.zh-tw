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
ms.openlocfilehash: 3dbe5b4e57f21970b518e4974707175f4bdcf02a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778227"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="f704b-102">ISymUnmanagedVariable::GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="f704b-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="f704b-103">取得這個變數，其父系內的起始位移。</span><span class="sxs-lookup"><span data-stu-id="f704b-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="f704b-104">如果這是本機變數的範圍內，起始位移會落在定義範圍的位移。</span><span class="sxs-lookup"><span data-stu-id="f704b-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f704b-105">語法</span><span class="sxs-lookup"><span data-stu-id="f704b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f704b-106">參數</span><span class="sxs-lookup"><span data-stu-id="f704b-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="f704b-107">[out]指標`ULONG32`接收的開始位移。</span><span class="sxs-lookup"><span data-stu-id="f704b-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f704b-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="f704b-108">Return Value</span></span>  
 <span data-ttu-id="f704b-109">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="f704b-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f704b-110">需求</span><span class="sxs-lookup"><span data-stu-id="f704b-110">Requirements</span></span>  
 <span data-ttu-id="f704b-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f704b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f704b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f704b-112">See also</span></span>

- [<span data-ttu-id="f704b-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="f704b-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="f704b-114">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="f704b-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
