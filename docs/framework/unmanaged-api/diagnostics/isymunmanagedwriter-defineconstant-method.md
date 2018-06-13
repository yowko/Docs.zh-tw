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
ms.openlocfilehash: 0c7cf800dafa9f3e213a012f49c73d51c78e7074
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427401"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="ab2b2-102">ISymUnmanagedWriter::DefineConstant 方法</span><span class="sxs-lookup"><span data-stu-id="ab2b2-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="ab2b2-103">定義常數值的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab2b2-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab2b2-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab2b2-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab2b2-105">參數</span><span class="sxs-lookup"><span data-stu-id="ab2b2-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="ab2b2-106">[in]指標`WCHAR`定義常數的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab2b2-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="ab2b2-107">[in]常數的值。</span><span class="sxs-lookup"><span data-stu-id="ab2b2-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="ab2b2-108">[in] `signature` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="ab2b2-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="ab2b2-109">[in]常數類型簽章。</span><span class="sxs-lookup"><span data-stu-id="ab2b2-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab2b2-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="ab2b2-110">Return Value</span></span>  
 <span data-ttu-id="ab2b2-111">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="ab2b2-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab2b2-112">需求</span><span class="sxs-lookup"><span data-stu-id="ab2b2-112">Requirements</span></span>  
 <span data-ttu-id="ab2b2-113">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ab2b2-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab2b2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab2b2-114">See Also</span></span>  
 [<span data-ttu-id="ab2b2-115">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="ab2b2-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="ab2b2-116">DefineConstant2 方法</span><span class="sxs-lookup"><span data-stu-id="ab2b2-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
