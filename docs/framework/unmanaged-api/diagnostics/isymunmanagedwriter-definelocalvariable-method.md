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
ms.openlocfilehash: 5730cdd910257d762230f5e54576d5e0a7ac1adb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614821"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a><span data-ttu-id="549a3-102">ISymUnmanagedWriter::DefineLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="549a3-102">ISymUnmanagedWriter::DefineLocalVariable Method</span></span>
<span data-ttu-id="549a3-103">在目前的語彙範圍中定義單一變數。</span><span class="sxs-lookup"><span data-stu-id="549a3-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="549a3-104">這個方法可以針對相同名稱的變數多次呼叫，其具有整個範圍中的多個家庭。</span><span class="sxs-lookup"><span data-stu-id="549a3-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="549a3-105">不過，在此情況下， `startOffset` 和參數的值不能重 `endOffset` 迭。</span><span class="sxs-lookup"><span data-stu-id="549a3-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="549a3-106">語法</span><span class="sxs-lookup"><span data-stu-id="549a3-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="549a3-107">參數</span><span class="sxs-lookup"><span data-stu-id="549a3-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="549a3-108">在`WCHAR`的指標，定義本機變數名稱。</span><span class="sxs-lookup"><span data-stu-id="549a3-108">[in] A pointer to a `WCHAR` that defines the local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="549a3-109">在區域變數屬性。</span><span class="sxs-lookup"><span data-stu-id="549a3-109">[in] The local variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="549a3-110">在`ULONG32`，表示緩衝區的大小（以位元組為單位） `signature` 。</span><span class="sxs-lookup"><span data-stu-id="549a3-110">[in] A `ULONG32` that indicates the size, in bytes, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="549a3-111">在區域變數簽章。</span><span class="sxs-lookup"><span data-stu-id="549a3-111">[in] The local variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="549a3-112">在網址類別型。</span><span class="sxs-lookup"><span data-stu-id="549a3-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="549a3-113">在參數規格的第一個位址。</span><span class="sxs-lookup"><span data-stu-id="549a3-113">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="549a3-114">在參數規格的第二個位址。</span><span class="sxs-lookup"><span data-stu-id="549a3-114">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="549a3-115">在參數規格的第三個位址。</span><span class="sxs-lookup"><span data-stu-id="549a3-115">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="549a3-116">在變數的開始位移。</span><span class="sxs-lookup"><span data-stu-id="549a3-116">[in] The start offset for the variable.</span></span> <span data-ttu-id="549a3-117">此為選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="549a3-117">This parameter is optional.</span></span> <span data-ttu-id="549a3-118">如果為0，則會忽略此參數，並在整個範圍中定義變數。</span><span class="sxs-lookup"><span data-stu-id="549a3-118">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="549a3-119">如果是非零值，則變數會落在目前範圍的位移內。</span><span class="sxs-lookup"><span data-stu-id="549a3-119">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="549a3-120">在變數的結束位移。</span><span class="sxs-lookup"><span data-stu-id="549a3-120">[in] The end offset for the variable.</span></span> <span data-ttu-id="549a3-121">此為選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="549a3-121">This parameter is optional.</span></span> <span data-ttu-id="549a3-122">如果為0，則會忽略此參數，並在整個範圍中定義變數。</span><span class="sxs-lookup"><span data-stu-id="549a3-122">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="549a3-123">如果是非零值，則變數會落在目前範圍的位移內。</span><span class="sxs-lookup"><span data-stu-id="549a3-123">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="549a3-124">傳回值</span><span class="sxs-lookup"><span data-stu-id="549a3-124">Return Value</span></span>  
 <span data-ttu-id="549a3-125">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="549a3-125">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="549a3-126">需求</span><span class="sxs-lookup"><span data-stu-id="549a3-126">Requirements</span></span>  
 <span data-ttu-id="549a3-127">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="549a3-127">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="549a3-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="549a3-128">See also</span></span>

- [<span data-ttu-id="549a3-129">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="549a3-129">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="549a3-130">DefineGlobalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="549a3-130">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)
- [<span data-ttu-id="549a3-131">DefineLocalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="549a3-131">DefineLocalVariable2 Method</span></span>](isymunmanagedwriter2-definelocalvariable2-method.md)
