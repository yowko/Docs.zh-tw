---
title: ISymUnmanagedWriter::DefineConstant 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineConstant
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a04bf93a2b2809198673d15f29714f52c9435b68
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767836"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="b1146-102">ISymUnmanagedWriter::DefineConstant 方法</span><span class="sxs-lookup"><span data-stu-id="b1146-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="b1146-103">定義常值的名稱。</span><span class="sxs-lookup"><span data-stu-id="b1146-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1146-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1146-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1146-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1146-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b1146-106">[in]指標`WCHAR`定義常數的名稱。</span><span class="sxs-lookup"><span data-stu-id="b1146-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="b1146-107">[in]常數的值。</span><span class="sxs-lookup"><span data-stu-id="b1146-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="b1146-108">[in] `signature` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="b1146-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="b1146-109">[in]常數類型簽章。</span><span class="sxs-lookup"><span data-stu-id="b1146-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1146-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="b1146-110">Return Value</span></span>  
 <span data-ttu-id="b1146-111">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="b1146-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1146-112">需求</span><span class="sxs-lookup"><span data-stu-id="b1146-112">Requirements</span></span>  
 <span data-ttu-id="b1146-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b1146-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1146-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1146-114">See also</span></span>

- [<span data-ttu-id="b1146-115">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="b1146-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="b1146-116">DefineConstant2 方法</span><span class="sxs-lookup"><span data-stu-id="b1146-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
