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
ms.openlocfilehash: af8beb1ec627b93faeb7329a03579319ca3880ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678320"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="ca750-102">ISymUnmanagedWriter::DefineSequencePoints 方法</span><span class="sxs-lookup"><span data-stu-id="ca750-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>

<span data-ttu-id="ca750-103">在目前的方法內定義一組序列點。</span><span class="sxs-lookup"><span data-stu-id="ca750-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="ca750-104">每個起始行和開始資料行定義方法內語句的開始。</span><span class="sxs-lookup"><span data-stu-id="ca750-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="ca750-105">每個結束行和結束資料行都會定義方法內的語句結尾。</span><span class="sxs-lookup"><span data-stu-id="ca750-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="ca750-106">陣列應以位移的遞增順序排序。</span><span class="sxs-lookup"><span data-stu-id="ca750-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="ca750-107">位移一律會從方法的開頭測量（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="ca750-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca750-108">語法</span><span class="sxs-lookup"><span data-stu-id="ca750-108">Syntax</span></span>  
  
```cpp  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca750-109">參數</span><span class="sxs-lookup"><span data-stu-id="ca750-109">Parameters</span></span>  

 `document`  
 <span data-ttu-id="ca750-110">在要為其定義序列點的檔物件。</span><span class="sxs-lookup"><span data-stu-id="ca750-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="ca750-111">在， `ULONG32` 指出每個 `offsets` 、、 `lines` `columns` 、 `endLines` 和 `endColumns` 緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="ca750-111">[in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="ca750-112">在從方法開頭測量之序列點的位移。</span><span class="sxs-lookup"><span data-stu-id="ca750-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="ca750-113">在序列點的起始行號。</span><span class="sxs-lookup"><span data-stu-id="ca750-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="ca750-114">在序列點的起始欄號。</span><span class="sxs-lookup"><span data-stu-id="ca750-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="ca750-115">在序列點的結束行號。</span><span class="sxs-lookup"><span data-stu-id="ca750-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="ca750-116">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="ca750-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="ca750-117">在序列點的結束欄號。</span><span class="sxs-lookup"><span data-stu-id="ca750-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="ca750-118">這是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="ca750-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca750-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="ca750-119">Return Value</span></span>  

 <span data-ttu-id="ca750-120">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ca750-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca750-121">需求</span><span class="sxs-lookup"><span data-stu-id="ca750-121">Requirements</span></span>  

 <span data-ttu-id="ca750-122">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="ca750-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca750-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca750-123">See also</span></span>

- [<span data-ttu-id="ca750-124">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="ca750-124">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
