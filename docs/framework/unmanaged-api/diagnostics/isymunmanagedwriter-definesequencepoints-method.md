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
ms.openlocfilehash: 8889c412f414f38d1d18d33ec297e82fd052280d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614795"
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="d4841-102">ISymUnmanagedWriter::DefineSequencePoints 方法</span><span class="sxs-lookup"><span data-stu-id="d4841-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="d4841-103">在目前的方法內定義一組序列點。</span><span class="sxs-lookup"><span data-stu-id="d4841-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="d4841-104">每個起始行和起始欄都會定義方法內的語句開頭。</span><span class="sxs-lookup"><span data-stu-id="d4841-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="d4841-105">每個結尾行和結束資料行都會定義方法內的語句結尾。</span><span class="sxs-lookup"><span data-stu-id="d4841-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="d4841-106">陣列應該以遞增的位移順序排序。</span><span class="sxs-lookup"><span data-stu-id="d4841-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="d4841-107">一定會從方法的開頭來測量位移（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="d4841-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4841-108">語法</span><span class="sxs-lookup"><span data-stu-id="d4841-108">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d4841-109">參數</span><span class="sxs-lookup"><span data-stu-id="d4841-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="d4841-110">在要定義序列點的檔物件。</span><span class="sxs-lookup"><span data-stu-id="d4841-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="d4841-111">在， `ULONG32` 表示每個 `offsets` 、 `lines` 、 `columns` 、 `endLines` 和 `endColumns` 緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="d4841-111">[in] A `ULONG32` that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="d4841-112">在從方法開頭測量之序列點的位移。</span><span class="sxs-lookup"><span data-stu-id="d4841-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="d4841-113">在序列點的起始行號。</span><span class="sxs-lookup"><span data-stu-id="d4841-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="d4841-114">在序列點的起始欄號。</span><span class="sxs-lookup"><span data-stu-id="d4841-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="d4841-115">在序列點的結束行號。</span><span class="sxs-lookup"><span data-stu-id="d4841-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="d4841-116">此為選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="d4841-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="d4841-117">在序列點的結束欄號。</span><span class="sxs-lookup"><span data-stu-id="d4841-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="d4841-118">此為選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="d4841-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4841-119">傳回值</span><span class="sxs-lookup"><span data-stu-id="d4841-119">Return Value</span></span>  
 <span data-ttu-id="d4841-120">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d4841-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4841-121">需求</span><span class="sxs-lookup"><span data-stu-id="d4841-121">Requirements</span></span>  
 <span data-ttu-id="d4841-122">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d4841-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4841-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4841-123">See also</span></span>

- [<span data-ttu-id="d4841-124">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="d4841-124">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
