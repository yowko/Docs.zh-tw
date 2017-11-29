---
title: "ISymUnmanagedWriter::DefineSequencePoints 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineSequencePoints
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 836774114798324ac16d3263e58dd56665a9aa49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="4008c-102">ISymUnmanagedWriter::DefineSequencePoints 方法</span><span class="sxs-lookup"><span data-stu-id="4008c-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="4008c-103">在目前的方法內定義一組序列點。</span><span class="sxs-lookup"><span data-stu-id="4008c-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="4008c-104">每個起始行和起始資料行定義方法內的陳述式的開始。</span><span class="sxs-lookup"><span data-stu-id="4008c-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="4008c-105">每個結束行和結束資料行定義方法內的陳述式的結尾。</span><span class="sxs-lookup"><span data-stu-id="4008c-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="4008c-106">陣列的位移遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="4008c-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="4008c-107">永遠從開頭的方法，以位元組為單位測量位移。</span><span class="sxs-lookup"><span data-stu-id="4008c-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4008c-108">語法</span><span class="sxs-lookup"><span data-stu-id="4008c-108">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="4008c-109">參數</span><span class="sxs-lookup"><span data-stu-id="4008c-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="4008c-110">[in]文件物件為其定義序列點。</span><span class="sxs-lookup"><span data-stu-id="4008c-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="4008c-111">[in]A `ULONG32` ，表示每個的大小`offsets`， `lines`， `columns`， `endLines`，和`endColumns`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="4008c-111">[in] A `ULONG32` that that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="4008c-112">[in]從方法開頭算起的序列點的位移。</span><span class="sxs-lookup"><span data-stu-id="4008c-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="4008c-113">[in]序列點起始行號。</span><span class="sxs-lookup"><span data-stu-id="4008c-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="4008c-114">[in]序列點的起始欄號。</span><span class="sxs-lookup"><span data-stu-id="4008c-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="4008c-115">[in]序列點結束行號。</span><span class="sxs-lookup"><span data-stu-id="4008c-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="4008c-116">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="4008c-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="4008c-117">[in]序列點結束欄號。</span><span class="sxs-lookup"><span data-stu-id="4008c-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="4008c-118">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="4008c-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4008c-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="4008c-119">Return Value</span></span>  
 <span data-ttu-id="4008c-120">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="4008c-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4008c-121">需求</span><span class="sxs-lookup"><span data-stu-id="4008c-121">Requirements</span></span>  
 <span data-ttu-id="4008c-122">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4008c-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4008c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4008c-123">See Also</span></span>  
 [<span data-ttu-id="4008c-124">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="4008c-124">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
