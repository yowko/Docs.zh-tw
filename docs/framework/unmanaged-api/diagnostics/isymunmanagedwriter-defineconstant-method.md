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
ms.openlocfilehash: 7f470dbe4ef2ef0d5f2204ccbdd5fb64730f9a2c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159753"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="d2092-102">ISymUnmanagedWriter::DefineConstant 方法</span><span class="sxs-lookup"><span data-stu-id="d2092-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="d2092-103">定義常值的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2092-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2092-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2092-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2092-105">參數</span><span class="sxs-lookup"><span data-stu-id="d2092-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d2092-106">[in]指標`WCHAR`定義常數的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2092-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="d2092-107">[in]常數的值。</span><span class="sxs-lookup"><span data-stu-id="d2092-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="d2092-108">[in] `signature` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="d2092-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="d2092-109">[in]常數類型簽章。</span><span class="sxs-lookup"><span data-stu-id="d2092-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d2092-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="d2092-110">Return Value</span></span>  
 <span data-ttu-id="d2092-111">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="d2092-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2092-112">需求</span><span class="sxs-lookup"><span data-stu-id="d2092-112">Requirements</span></span>  
 <span data-ttu-id="d2092-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d2092-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2092-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2092-114">See also</span></span>

- [<span data-ttu-id="d2092-115">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="d2092-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="d2092-116">DefineConstant2 方法</span><span class="sxs-lookup"><span data-stu-id="d2092-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
