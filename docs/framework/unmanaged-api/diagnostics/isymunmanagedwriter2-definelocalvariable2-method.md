---
title: "ISymUnmanagedWriter2::DefineLocalVariable2 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1124b57bed16e349c753be872c1b709a287e6237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="b2e3f-102">ISymUnmanagedWriter2::DefineLocalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="b2e3f-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="b2e3f-103">在目前的語彙範圍中定義單一變數。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="b2e3f-104">可以多次呼叫這個方法在範圍中有多個定義域的相同名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="b2e3f-105">在此情況下，不過，值`startOffset`和`endOffset`參數不能重疊。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2e3f-106">語法</span><span class="sxs-lookup"><span data-stu-id="b2e3f-106">Syntax</span></span>  
  
```  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2e3f-107">參數</span><span class="sxs-lookup"><span data-stu-id="b2e3f-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b2e3f-108">[in]本機變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="b2e3f-109">[in]本機變數的屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="b2e3f-110">[in]簽章的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="b2e3f-111">[in]地址類型。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="b2e3f-112">[in]參數規格的第一個位址。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="b2e3f-113">[in]參數規格的第二個位址。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="b2e3f-114">[in]參數規格的第三個位址。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="b2e3f-115">[in]變數的起始位移。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="b2e3f-116">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-116">This parameter is optional.</span></span> <span data-ttu-id="b2e3f-117">如果是 0，會忽略這個參數，並會在整個範圍中定義變數。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="b2e3f-118">如果它是非零值，變數會落在目前範圍的位移之內。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="b2e3f-119">[in]變數的結束位移。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="b2e3f-120">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-120">This parameter is optional.</span></span> <span data-ttu-id="b2e3f-121">如果是 0，會忽略這個參數，並會在整個範圍中定義變數。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="b2e3f-122">如果它是非零值，變數會落在目前範圍的位移之內。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2e3f-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="b2e3f-123">Return Value</span></span>  
 <span data-ttu-id="b2e3f-124">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="b2e3f-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2e3f-125">需求</span><span class="sxs-lookup"><span data-stu-id="b2e3f-125">Requirements</span></span>  
 <span data-ttu-id="b2e3f-126">**標頭：**於 CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="b2e3f-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e3f-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="b2e3f-127">See Also</span></span>  
 [<span data-ttu-id="b2e3f-128">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="b2e3f-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="b2e3f-129">DefineLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="b2e3f-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
