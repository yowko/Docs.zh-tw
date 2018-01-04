---
title: "ISymUnmanagedWriter::DefineLocalVariable 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineLocalVariable
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89ea3e23166b4745b34b7c2af498d29564cdd68d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="b4ccf-102">ISymUnmanagedWriter::DefineLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="b4ccf-102">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>
<span data-ttu-id="b4ccf-103">在目前的語彙範圍中定義單一變數。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="b4ccf-104">可以多次呼叫這個方法在範圍中有多個定義域的相同名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="b4ccf-105">在此情況下，不過，值`startOffset`和`endOffset`參數不能重疊。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4ccf-106">語法</span><span class="sxs-lookup"><span data-stu-id="b4ccf-106">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="b4ccf-107">參數</span><span class="sxs-lookup"><span data-stu-id="b4ccf-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b4ccf-108">[in]指標`WCHAR`定義本機變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-108">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="b4ccf-109">[in]本機變數的屬性。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-109">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="b4ccf-110">[in]A`ULONG32`指出的大小，以位元組為單位，`signature`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-110">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="b4ccf-111">[in]區域變數簽章。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-111">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="b4ccf-112">[in]地址類型。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="b4ccf-113">[in]參數規格的第一個位址。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="b4ccf-114">[in]參數規格的第二個位址。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="b4ccf-115">[in]參數規格的第三個位址。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="b4ccf-116">[in]變數的起始位移。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="b4ccf-117">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-117">This parameter is optional.</span></span> <span data-ttu-id="b4ccf-118">如果是 0，會忽略這個參數，並會在整個範圍中定義變數。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="b4ccf-119">如果它是非零值，變數會落在目前範圍的位移之內。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="b4ccf-120">[in]變數的結束位移。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="b4ccf-121">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-121">This parameter is optional.</span></span> <span data-ttu-id="b4ccf-122">如果是 0，會忽略這個參數，並會在整個範圍中定義變數。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="b4ccf-123">如果它是非零值，變數會落在目前範圍的位移之內。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4ccf-124">傳回值</span><span class="sxs-lookup"><span data-stu-id="b4ccf-124">Return Value</span></span>  
 <span data-ttu-id="b4ccf-125">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="b4ccf-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4ccf-126">需求</span><span class="sxs-lookup"><span data-stu-id="b4ccf-126">Requirements</span></span>  
 <span data-ttu-id="b4ccf-127">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b4ccf-127">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ccf-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="b4ccf-128">See Also</span></span>  
 [<span data-ttu-id="b4ccf-129">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="b4ccf-129">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="b4ccf-130">DefineGlobalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="b4ccf-130">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)  
 [<span data-ttu-id="b4ccf-131">DefineLocalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="b4ccf-131">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
