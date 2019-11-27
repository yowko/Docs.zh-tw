---
title: ISymUnmanagedWriter2::DefineLocalVariable2 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: 73f536b4ab98aa596c2395810cb8b616ffd309e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438301"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="fbd1f-102">ISymUnmanagedWriter2::DefineLocalVariable2 方法</span><span class="sxs-lookup"><span data-stu-id="fbd1f-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="fbd1f-103">在目前的語彙範圍中定義單一變數。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="fbd1f-104">這個方法可以針對相同名稱的變數多次呼叫，其具有整個範圍中的多個家庭。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="fbd1f-105">不過，在此情況下，`startOffset` 和 `endOffset` 參數的值不得重迭。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbd1f-106">語法</span><span class="sxs-lookup"><span data-stu-id="fbd1f-106">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="fbd1f-107">參數</span><span class="sxs-lookup"><span data-stu-id="fbd1f-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="fbd1f-108">在本機變數名稱。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="fbd1f-109">在區域變數屬性。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="fbd1f-110">在簽章的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="fbd1f-111">在網址類別型。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="fbd1f-112">在參數規格的第一個位址。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="fbd1f-113">在參數規格的第二個位址。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="fbd1f-114">在參數規格的第三個位址。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="fbd1f-115">在變數的開始位移。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="fbd1f-116">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-116">This parameter is optional.</span></span> <span data-ttu-id="fbd1f-117">如果為0，則會忽略此參數，並在整個範圍中定義變數。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="fbd1f-118">如果是非零值，則變數會落在目前範圍的位移內。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="fbd1f-119">在變數的結束位移。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="fbd1f-120">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-120">This parameter is optional.</span></span> <span data-ttu-id="fbd1f-121">如果為0，則會忽略此參數，並在整個範圍中定義變數。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="fbd1f-122">如果是非零值，則變數會落在目前範圍的位移內。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbd1f-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="fbd1f-123">Return Value</span></span>  
 <span data-ttu-id="fbd1f-124">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="fbd1f-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbd1f-125">需求</span><span class="sxs-lookup"><span data-stu-id="fbd1f-125">Requirements</span></span>  
 <span data-ttu-id="fbd1f-126">**標頭：** CorSym .idl</span><span class="sxs-lookup"><span data-stu-id="fbd1f-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbd1f-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="fbd1f-127">See also</span></span>

- [<span data-ttu-id="fbd1f-128">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="fbd1f-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="fbd1f-129">DefineLocalVariable 方法</span><span class="sxs-lookup"><span data-stu-id="fbd1f-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
