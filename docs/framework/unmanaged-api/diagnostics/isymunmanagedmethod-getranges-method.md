---
title: ISymUnmanagedMethod::GetRanges 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRanges
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94ca1db2bf85f42117f686a8cb483907003927c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939590"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="106e3-102">ISymUnmanagedMethod::GetRanges 方法</span><span class="sxs-lookup"><span data-stu-id="106e3-102">ISymUnmanagedMethod::GetRanges Method</span></span>
<span data-ttu-id="106e3-103">指定的文件中的位置，傳回陣列的開始和結束位移組對應的 Microsoft intermediate language (MSIL，其中涵蓋在這個方法內的位置) 範圍。</span><span class="sxs-lookup"><span data-stu-id="106e3-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="106e3-104">陣列是一個整數的陣列，並具有 [開始、 結束、 開始、 結束] 格式。</span><span class="sxs-lookup"><span data-stu-id="106e3-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="106e3-105">範圍組的數目會除以 2 陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="106e3-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="106e3-106">語法</span><span class="sxs-lookup"><span data-stu-id="106e3-106">Syntax</span></span>  
  
```  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="106e3-107">參數</span><span class="sxs-lookup"><span data-stu-id="106e3-107">Parameters</span></span>  
 `document`  
 <span data-ttu-id="106e3-108">[in]要求位移的文件。</span><span class="sxs-lookup"><span data-stu-id="106e3-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="106e3-109">[in]對應到範圍的文件行。</span><span class="sxs-lookup"><span data-stu-id="106e3-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="106e3-110">[in]對應到範圍的文件的資料行。</span><span class="sxs-lookup"><span data-stu-id="106e3-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="106e3-111">[in] `ranges` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="106e3-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="106e3-112">[out]指標`ULONG32`接收包含範圍所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="106e3-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="106e3-113">[out]接收範圍緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="106e3-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="106e3-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="106e3-114">Return Value</span></span>  
 <span data-ttu-id="106e3-115">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="106e3-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="106e3-116">需求</span><span class="sxs-lookup"><span data-stu-id="106e3-116">Requirements</span></span>  
 <span data-ttu-id="106e3-117">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="106e3-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="106e3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="106e3-118">See also</span></span>

- [<span data-ttu-id="106e3-119">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="106e3-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
