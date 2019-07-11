---
title: ISymUnmanagedVariable::GetEndOffset 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ef32a963b73f2109b9747ef303e8ccd6a729838
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778269"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="57faa-102">ISymUnmanagedVariable::GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="57faa-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="57faa-103">取得其父系內這個變數的結束位移。</span><span class="sxs-lookup"><span data-stu-id="57faa-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="57faa-104">如果這是在範圍內的本機變數，而結束位移會落在定義範圍的位移。</span><span class="sxs-lookup"><span data-stu-id="57faa-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57faa-105">語法</span><span class="sxs-lookup"><span data-stu-id="57faa-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57faa-106">參數</span><span class="sxs-lookup"><span data-stu-id="57faa-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="57faa-107">[out]指標`ULONG32`接收的結束位移。</span><span class="sxs-lookup"><span data-stu-id="57faa-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57faa-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="57faa-108">Return Value</span></span>  
 <span data-ttu-id="57faa-109">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="57faa-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57faa-110">需求</span><span class="sxs-lookup"><span data-stu-id="57faa-110">Requirements</span></span>  
 <span data-ttu-id="57faa-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="57faa-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57faa-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57faa-112">See also</span></span>

- [<span data-ttu-id="57faa-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="57faa-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="57faa-114">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="57faa-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
