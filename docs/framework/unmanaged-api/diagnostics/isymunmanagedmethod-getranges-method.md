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
ms.openlocfilehash: 1f1bd9c33f24847eae4ff7d26c5b996cd34afb72
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448934"
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="c3966-102">ISymUnmanagedMethod::GetRanges 方法</span><span class="sxs-lookup"><span data-stu-id="c3966-102">ISymUnmanagedMethod::GetRanges Method</span></span>
<span data-ttu-id="c3966-103">指定檔中的位置時，會傳回開始和結束位移組的陣列，其對應于此方法內的位置所涵蓋的 Microsoft 中繼語言（MSIL）範圍。</span><span class="sxs-lookup"><span data-stu-id="c3966-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="c3966-104">陣列是整數的陣列，其格式為 [開始]、[結束]、[開始]、[結束]。</span><span class="sxs-lookup"><span data-stu-id="c3966-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="c3966-105">範圍配對的數目是陣列的長度除以2。</span><span class="sxs-lookup"><span data-stu-id="c3966-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3966-106">語法</span><span class="sxs-lookup"><span data-stu-id="c3966-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3966-107">參數</span><span class="sxs-lookup"><span data-stu-id="c3966-107">Parameters</span></span>  
 `document`  
 <span data-ttu-id="c3966-108">在要求位移的檔。</span><span class="sxs-lookup"><span data-stu-id="c3966-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="c3966-109">在對應到範圍的檔行。</span><span class="sxs-lookup"><span data-stu-id="c3966-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="c3966-110">在對應到範圍的檔資料行。</span><span class="sxs-lookup"><span data-stu-id="c3966-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="c3966-111">[in] `ranges` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="c3966-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="c3966-112">脫銷`ULONG32` 的指標，接收包含範圍所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="c3966-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="c3966-113">脫銷接收範圍之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="c3966-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3966-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="c3966-114">Return Value</span></span>  
 <span data-ttu-id="c3966-115">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c3966-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3966-116">需求</span><span class="sxs-lookup"><span data-stu-id="c3966-116">Requirements</span></span>  
 <span data-ttu-id="c3966-117">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="c3966-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3966-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3966-118">See also</span></span>

- [<span data-ttu-id="c3966-119">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="c3966-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
