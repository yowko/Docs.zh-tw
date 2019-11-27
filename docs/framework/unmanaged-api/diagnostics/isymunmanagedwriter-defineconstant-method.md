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
ms.openlocfilehash: c8d0145b9dffe1c0ff6ed3281c90f3bcec082ab8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428069"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="63632-102">ISymUnmanagedWriter::DefineConstant 方法</span><span class="sxs-lookup"><span data-stu-id="63632-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="63632-103">定義常數值的名稱。</span><span class="sxs-lookup"><span data-stu-id="63632-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63632-104">語法</span><span class="sxs-lookup"><span data-stu-id="63632-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63632-105">參數</span><span class="sxs-lookup"><span data-stu-id="63632-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="63632-106">在定義常數名稱之 `WCHAR` 的指標。</span><span class="sxs-lookup"><span data-stu-id="63632-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="63632-107">在常數的值。</span><span class="sxs-lookup"><span data-stu-id="63632-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="63632-108">[in] `signature` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="63632-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="63632-109">在常數的類型簽章。</span><span class="sxs-lookup"><span data-stu-id="63632-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63632-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="63632-110">Return Value</span></span>  
 <span data-ttu-id="63632-111">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="63632-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63632-112">需求</span><span class="sxs-lookup"><span data-stu-id="63632-112">Requirements</span></span>  
 <span data-ttu-id="63632-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="63632-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63632-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="63632-114">See also</span></span>

- [<span data-ttu-id="63632-115">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="63632-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="63632-116">DefineConstant2 方法</span><span class="sxs-lookup"><span data-stu-id="63632-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
