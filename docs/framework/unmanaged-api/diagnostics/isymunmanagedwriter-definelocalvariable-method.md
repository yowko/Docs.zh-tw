---
title: ISymUnmanagedWriter::DefineLocalVariable 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9466df3f6413f86eb8558f0037b96c254b2a2e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777335"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="d6095-102">ISymUnmanagedWriter::DefineLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="d6095-102">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>
<span data-ttu-id="d6095-103">在目前的語彙範圍中定義單一變數。</span><span class="sxs-lookup"><span data-stu-id="d6095-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="d6095-104">可以多次呼叫這個方法在範圍中有多個定義域的相同名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="d6095-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="d6095-105">在此情況下，不過，值`startOffset`和`endOffset`參數不得重疊。</span><span class="sxs-lookup"><span data-stu-id="d6095-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6095-106">語法</span><span class="sxs-lookup"><span data-stu-id="d6095-106">Syntax</span></span>  
  
```cpp  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6095-107">參數</span><span class="sxs-lookup"><span data-stu-id="d6095-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d6095-108">[in]指標`WCHAR`定義本機變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="d6095-108">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="d6095-109">[in]本機變數的屬性。</span><span class="sxs-lookup"><span data-stu-id="d6095-109">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="d6095-110">[in]A`ULONG32`表示的大小，以位元組為單位，`signature`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d6095-110">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="d6095-111">[in]區域變數簽章。</span><span class="sxs-lookup"><span data-stu-id="d6095-111">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="d6095-112">[in]位址類型。</span><span class="sxs-lookup"><span data-stu-id="d6095-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="d6095-113">[in]參數規格的第一個位址。</span><span class="sxs-lookup"><span data-stu-id="d6095-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="d6095-114">[in]參數規格的第二個位址。</span><span class="sxs-lookup"><span data-stu-id="d6095-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="d6095-115">[in]參數規格的第三個位址。</span><span class="sxs-lookup"><span data-stu-id="d6095-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="d6095-116">[in]變數的起始位移。</span><span class="sxs-lookup"><span data-stu-id="d6095-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="d6095-117">這個參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="d6095-117">This parameter is optional.</span></span> <span data-ttu-id="d6095-118">如果是 0，會忽略這個參數，並在整個範圍定義的變數。</span><span class="sxs-lookup"><span data-stu-id="d6095-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="d6095-119">如果它是非零值時，變數會落在目前的範圍的位移。</span><span class="sxs-lookup"><span data-stu-id="d6095-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="d6095-120">[in]變數的結束位移。</span><span class="sxs-lookup"><span data-stu-id="d6095-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="d6095-121">這個參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="d6095-121">This parameter is optional.</span></span> <span data-ttu-id="d6095-122">如果是 0，會忽略這個參數，並在整個範圍定義的變數。</span><span class="sxs-lookup"><span data-stu-id="d6095-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="d6095-123">如果它是非零值時，變數會落在目前的範圍的位移。</span><span class="sxs-lookup"><span data-stu-id="d6095-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6095-124">傳回值</span><span class="sxs-lookup"><span data-stu-id="d6095-124">Return Value</span></span>  
 <span data-ttu-id="d6095-125">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="d6095-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6095-126">需求</span><span class="sxs-lookup"><span data-stu-id="d6095-126">Requirements</span></span>  
 <span data-ttu-id="d6095-127">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d6095-127">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6095-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6095-128">See also</span></span>

- [<span data-ttu-id="d6095-129">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="d6095-129">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="d6095-130">DefineGlobalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="d6095-130">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
- [<span data-ttu-id="d6095-131">DefineLocalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="d6095-131">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
