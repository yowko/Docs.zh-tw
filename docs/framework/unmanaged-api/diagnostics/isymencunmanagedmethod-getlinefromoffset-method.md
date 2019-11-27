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
ms.openlocfilehash: 94a571a4bc01b805387aebe5a6e23bad0b735313
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448646"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="39a91-102">ISymENCUnmanagedMethod::GetLineFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="39a91-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="39a91-103">取得與位移相關聯的線條資訊。</span><span class="sxs-lookup"><span data-stu-id="39a91-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="39a91-104">如果 offset 參數（`dwOffset`）不是序列點，這個方法會取得與上一個位移相關聯的行資訊。</span><span class="sxs-lookup"><span data-stu-id="39a91-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39a91-105">語法</span><span class="sxs-lookup"><span data-stu-id="39a91-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39a91-106">參數</span><span class="sxs-lookup"><span data-stu-id="39a91-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="39a91-107">在包含位移的 `ULONG32`。</span><span class="sxs-lookup"><span data-stu-id="39a91-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="39a91-108">脫銷接收行之 `ULONG32` 的指標。</span><span class="sxs-lookup"><span data-stu-id="39a91-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="39a91-109">脫銷接收資料行之 `ULONG32` 的指標。</span><span class="sxs-lookup"><span data-stu-id="39a91-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="39a91-110">脫銷接收結束行之 `ULONG32` 的指標。</span><span class="sxs-lookup"><span data-stu-id="39a91-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="39a91-111">脫銷接收結尾資料行之 `ULONG32` 的指標。</span><span class="sxs-lookup"><span data-stu-id="39a91-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="39a91-112">脫銷接收相關聯序列點之 `ULONG32` 的指標。</span><span class="sxs-lookup"><span data-stu-id="39a91-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39a91-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="39a91-113">Return Value</span></span>  
 <span data-ttu-id="39a91-114">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="39a91-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39a91-115">需求</span><span class="sxs-lookup"><span data-stu-id="39a91-115">Requirements</span></span>  
 <span data-ttu-id="39a91-116">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="39a91-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39a91-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="39a91-117">See also</span></span>

- [<span data-ttu-id="39a91-118">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="39a91-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
