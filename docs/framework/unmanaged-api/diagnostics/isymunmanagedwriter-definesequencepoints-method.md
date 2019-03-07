---
title: ISymUnmanagedWriter::DefineSequencePoints 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4210dedd77c6ab041189fa287e192bb7038080b2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491400"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="7d331-102">ISymUnmanagedWriter::DefineSequencePoints 方法</span><span class="sxs-lookup"><span data-stu-id="7d331-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="7d331-103">在目前的方法內定義一組序列點。</span><span class="sxs-lookup"><span data-stu-id="7d331-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="7d331-104">每個起始行和起始資料行定義中方法的陳述式開頭。</span><span class="sxs-lookup"><span data-stu-id="7d331-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="7d331-105">每個結束行和結束資料行定義方法內的陳述式的結尾。</span><span class="sxs-lookup"><span data-stu-id="7d331-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="7d331-106">要以位移的遞增順序排序的陣列。</span><span class="sxs-lookup"><span data-stu-id="7d331-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="7d331-107">位移一律是從方法，以位元組為單位的開頭進行測量。</span><span class="sxs-lookup"><span data-stu-id="7d331-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d331-108">語法</span><span class="sxs-lookup"><span data-stu-id="7d331-108">Syntax</span></span>  
  
```  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d331-109">參數</span><span class="sxs-lookup"><span data-stu-id="7d331-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="7d331-110">[in]文件物件，其定義序列點。</span><span class="sxs-lookup"><span data-stu-id="7d331-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="7d331-111">[in]A`ULONG32`表示的每個大小`offsets`， `lines`， `columns`， `endLines`，和`endColumns`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="7d331-111">[in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="7d331-112">[in]從方法開頭進行測量之序列點的位移。</span><span class="sxs-lookup"><span data-stu-id="7d331-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="7d331-113">[in]序列點的起始行號。</span><span class="sxs-lookup"><span data-stu-id="7d331-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="7d331-114">[in]序列點的起始欄號。</span><span class="sxs-lookup"><span data-stu-id="7d331-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="7d331-115">[in]序列點結束的行號。</span><span class="sxs-lookup"><span data-stu-id="7d331-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="7d331-116">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="7d331-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="7d331-117">[in]序列點結束欄號。</span><span class="sxs-lookup"><span data-stu-id="7d331-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="7d331-118">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="7d331-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d331-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="7d331-119">Return Value</span></span>  
 <span data-ttu-id="7d331-120">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="7d331-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d331-121">需求</span><span class="sxs-lookup"><span data-stu-id="7d331-121">Requirements</span></span>  
 <span data-ttu-id="7d331-122">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7d331-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d331-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d331-123">See also</span></span>
- [<span data-ttu-id="7d331-124">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="7d331-124">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
