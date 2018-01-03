---
title: "ISymENCUnmanagedMethod::GetLineFromOffset 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetLineFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 535c0310a3220c5691f26c9081f6d2f747196e91
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="8ba49-102">ISymENCUnmanagedMethod::GetLineFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="8ba49-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="8ba49-103">取得相關聯的位移的行資訊。</span><span class="sxs-lookup"><span data-stu-id="8ba49-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="8ba49-104">如果位移的參數 (`dwOffset`) 不是序列點，這個方法會取得相關聯的上一個位移的行資訊。</span><span class="sxs-lookup"><span data-stu-id="8ba49-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ba49-105">語法</span><span class="sxs-lookup"><span data-stu-id="8ba49-105">Syntax</span></span>  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ba49-106">參數</span><span class="sxs-lookup"><span data-stu-id="8ba49-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="8ba49-107">[in]A`ULONG32`包含位移。</span><span class="sxs-lookup"><span data-stu-id="8ba49-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="8ba49-108">[out]指標`ULONG32`接收之列。</span><span class="sxs-lookup"><span data-stu-id="8ba49-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="8ba49-109">[out]指標`ULONG32`接收的資料行。</span><span class="sxs-lookup"><span data-stu-id="8ba49-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="8ba49-110">[out]指標`ULONG32`接收之結尾行。</span><span class="sxs-lookup"><span data-stu-id="8ba49-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="8ba49-111">[out]指標`ULONG32`接收結束資料行。</span><span class="sxs-lookup"><span data-stu-id="8ba49-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="8ba49-112">[out]指標`ULONG32`接收相關聯的序列點。</span><span class="sxs-lookup"><span data-stu-id="8ba49-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ba49-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="8ba49-113">Return Value</span></span>  
 <span data-ttu-id="8ba49-114">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="8ba49-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ba49-115">需求</span><span class="sxs-lookup"><span data-stu-id="8ba49-115">Requirements</span></span>  
 <span data-ttu-id="8ba49-116">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8ba49-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ba49-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="8ba49-117">See Also</span></span>  
 [<span data-ttu-id="8ba49-118">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="8ba49-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
