---
title: ISymENCUnmanagedMethod::GetLineFromOffset 方法
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98015af4a79a9fca4945708e6d0baeb61e46876f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531222"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="3debb-102">ISymENCUnmanagedMethod::GetLineFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="3debb-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="3debb-103">取得位移與相關聯的行資訊。</span><span class="sxs-lookup"><span data-stu-id="3debb-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="3debb-104">如果位移的參數 (`dwOffset`) 不是序列點，這個方法會取得先前的位移與相關聯的行資訊。</span><span class="sxs-lookup"><span data-stu-id="3debb-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3debb-105">語法</span><span class="sxs-lookup"><span data-stu-id="3debb-105">Syntax</span></span>  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3debb-106">參數</span><span class="sxs-lookup"><span data-stu-id="3debb-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="3debb-107">[in]A`ULONG32`包含位移。</span><span class="sxs-lookup"><span data-stu-id="3debb-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="3debb-108">[out]指標`ULONG32`接收之列。</span><span class="sxs-lookup"><span data-stu-id="3debb-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="3debb-109">[out]指標`ULONG32`接收的資料行。</span><span class="sxs-lookup"><span data-stu-id="3debb-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="3debb-110">[out]指標`ULONG32`接收之結尾行。</span><span class="sxs-lookup"><span data-stu-id="3debb-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="3debb-111">[out]指標`ULONG32`接收端資料行。</span><span class="sxs-lookup"><span data-stu-id="3debb-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="3debb-112">[out]指標`ULONG32`接收相關聯的序列點。</span><span class="sxs-lookup"><span data-stu-id="3debb-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3debb-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="3debb-113">Return Value</span></span>  
 <span data-ttu-id="3debb-114">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="3debb-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3debb-115">需求</span><span class="sxs-lookup"><span data-stu-id="3debb-115">Requirements</span></span>  
 <span data-ttu-id="3debb-116">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3debb-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3debb-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3debb-117">See also</span></span>
- [<span data-ttu-id="3debb-118">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="3debb-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
