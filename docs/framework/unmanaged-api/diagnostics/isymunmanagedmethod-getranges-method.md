---
title: "ISymUnmanagedMethod::GetRanges 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetRanges
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71d24bc83d6a26c800d0d97e885b322cc2b4ccbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="0d98d-102">ISymUnmanagedMethod::GetRanges 方法</span><span class="sxs-lookup"><span data-stu-id="0d98d-102">ISymUnmanagedMethod::GetRanges Method</span></span>
<span data-ttu-id="0d98d-103">指定的文件中的位置，傳回陣列的開始和結束位移組對應的 Microsoft 中繼語言 (MSIL) 這個方法內的位置所涵蓋的範圍。</span><span class="sxs-lookup"><span data-stu-id="0d98d-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="0d98d-104">陣列是整數的陣列，而且 [開始、 結束、 開始、 結束] 的格式。</span><span class="sxs-lookup"><span data-stu-id="0d98d-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="0d98d-105">範圍組數目長度除以 2 的陣列。</span><span class="sxs-lookup"><span data-stu-id="0d98d-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d98d-106">語法</span><span class="sxs-lookup"><span data-stu-id="0d98d-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="0d98d-107">參數</span><span class="sxs-lookup"><span data-stu-id="0d98d-107">Parameters</span></span>  
 `document`  
 <span data-ttu-id="0d98d-108">[in]要求位移的文件。</span><span class="sxs-lookup"><span data-stu-id="0d98d-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="0d98d-109">[in]對應到範圍的文件行。</span><span class="sxs-lookup"><span data-stu-id="0d98d-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="0d98d-110">[in]文件資料行對應到範圍。</span><span class="sxs-lookup"><span data-stu-id="0d98d-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="0d98d-111">[in] `ranges` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="0d98d-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="0d98d-112">[out]指標`ULONG32`包含範圍所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="0d98d-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="0d98d-113">[out]接收範圍緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="0d98d-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d98d-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="0d98d-114">Return Value</span></span>  
 <span data-ttu-id="0d98d-115">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="0d98d-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d98d-116">需求</span><span class="sxs-lookup"><span data-stu-id="0d98d-116">Requirements</span></span>  
 <span data-ttu-id="0d98d-117">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0d98d-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d98d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d98d-118">See Also</span></span>  
 [<span data-ttu-id="0d98d-119">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="0d98d-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
