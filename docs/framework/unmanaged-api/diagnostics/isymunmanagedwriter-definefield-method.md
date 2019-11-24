---
title: ISymUnmanagedWriter::DefineField 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
ms.openlocfilehash: 7eea63cae27c08260177dfc7746046b975434611
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428044"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="2edb3-102">ISymUnmanagedWriter::DefineField 方法</span><span class="sxs-lookup"><span data-stu-id="2edb3-102">ISymUnmanagedWriter::DefineField Method</span></span>
<span data-ttu-id="2edb3-103">Defines a single variable that is not within a method.</span><span class="sxs-lookup"><span data-stu-id="2edb3-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="2edb3-104">This method is used for certain fields in classes, bit fields, and so on.</span><span class="sxs-lookup"><span data-stu-id="2edb3-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2edb3-105">語法</span><span class="sxs-lookup"><span data-stu-id="2edb3-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2edb3-106">參數</span><span class="sxs-lookup"><span data-stu-id="2edb3-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="2edb3-107">[in] The metadata type or method token.</span><span class="sxs-lookup"><span data-stu-id="2edb3-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="2edb3-108">[in] The field name.</span><span class="sxs-lookup"><span data-stu-id="2edb3-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="2edb3-109">[in] The field attributes.</span><span class="sxs-lookup"><span data-stu-id="2edb3-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="2edb3-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span><span class="sxs-lookup"><span data-stu-id="2edb3-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="2edb3-111">[in] The array of field signatures.</span><span class="sxs-lookup"><span data-stu-id="2edb3-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="2edb3-112">[in] The address type.</span><span class="sxs-lookup"><span data-stu-id="2edb3-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="2edb3-113">[in] The first address for the field specification.</span><span class="sxs-lookup"><span data-stu-id="2edb3-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="2edb3-114">[in] The second address for the field specification.</span><span class="sxs-lookup"><span data-stu-id="2edb3-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="2edb3-115">[in] The third address for the field specification.</span><span class="sxs-lookup"><span data-stu-id="2edb3-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2edb3-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="2edb3-116">Return Value</span></span>  
 <span data-ttu-id="2edb3-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="2edb3-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2edb3-118">需求</span><span class="sxs-lookup"><span data-stu-id="2edb3-118">Requirements</span></span>  
 <span data-ttu-id="2edb3-119">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2edb3-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2edb3-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="2edb3-120">See also</span></span>

- [<span data-ttu-id="2edb3-121">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="2edb3-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
