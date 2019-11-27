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
ms.openlocfilehash: f6a741df3ea57b5e9b4fa8bc5d304bfedd1d6c15
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428017"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="01557-102">ISymUnmanagedWriter::DefineLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="01557-102">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>
<span data-ttu-id="01557-103">在目前的語彙範圍中定義單一變數。</span><span class="sxs-lookup"><span data-stu-id="01557-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="01557-104">這個方法可以針對相同名稱的變數多次呼叫，其具有整個範圍中的多個家庭。</span><span class="sxs-lookup"><span data-stu-id="01557-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="01557-105">不過，在此情況下，`startOffset` 和 `endOffset` 參數的值不得重迭。</span><span class="sxs-lookup"><span data-stu-id="01557-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01557-106">語法</span><span class="sxs-lookup"><span data-stu-id="01557-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="01557-107">參數</span><span class="sxs-lookup"><span data-stu-id="01557-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="01557-108">在定義本機變數名稱之 `WCHAR` 的指標。</span><span class="sxs-lookup"><span data-stu-id="01557-108">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="01557-109">在區域變數屬性。</span><span class="sxs-lookup"><span data-stu-id="01557-109">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="01557-110">在`ULONG32`，表示 `signature` 緩衝區的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="01557-110">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="01557-111">在區域變數簽章。</span><span class="sxs-lookup"><span data-stu-id="01557-111">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="01557-112">在網址類別型。</span><span class="sxs-lookup"><span data-stu-id="01557-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="01557-113">在參數規格的第一個位址。</span><span class="sxs-lookup"><span data-stu-id="01557-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="01557-114">在參數規格的第二個位址。</span><span class="sxs-lookup"><span data-stu-id="01557-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="01557-115">在參數規格的第三個位址。</span><span class="sxs-lookup"><span data-stu-id="01557-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="01557-116">在變數的開始位移。</span><span class="sxs-lookup"><span data-stu-id="01557-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="01557-117">這個參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="01557-117">This parameter is optional.</span></span> <span data-ttu-id="01557-118">如果為0，則會忽略此參數，並在整個範圍中定義變數。</span><span class="sxs-lookup"><span data-stu-id="01557-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="01557-119">如果是非零值，則變數會落在目前範圍的位移內。</span><span class="sxs-lookup"><span data-stu-id="01557-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="01557-120">在變數的結束位移。</span><span class="sxs-lookup"><span data-stu-id="01557-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="01557-121">這個參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="01557-121">This parameter is optional.</span></span> <span data-ttu-id="01557-122">如果為0，則會忽略此參數，並在整個範圍中定義變數。</span><span class="sxs-lookup"><span data-stu-id="01557-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="01557-123">如果是非零值，則變數會落在目前範圍的位移內。</span><span class="sxs-lookup"><span data-stu-id="01557-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01557-124">傳回值</span><span class="sxs-lookup"><span data-stu-id="01557-124">Return Value</span></span>  
 <span data-ttu-id="01557-125">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="01557-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01557-126">需求</span><span class="sxs-lookup"><span data-stu-id="01557-126">Requirements</span></span>  
 <span data-ttu-id="01557-127">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="01557-127">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01557-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01557-128">See also</span></span>

- [<span data-ttu-id="01557-129">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="01557-129">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="01557-130">DefineGlobalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="01557-130">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
- [<span data-ttu-id="01557-131">DefineLocalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="01557-131">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)
