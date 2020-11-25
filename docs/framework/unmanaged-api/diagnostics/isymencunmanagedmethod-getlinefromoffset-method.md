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
ms.openlocfilehash: 196993df9058d3eb8167e0144255c5fe366c54f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707356"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="8fe4f-102">ISymENCUnmanagedMethod::GetLineFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="8fe4f-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>

<span data-ttu-id="8fe4f-103">取得與位移相關聯的行資訊。</span><span class="sxs-lookup"><span data-stu-id="8fe4f-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="8fe4f-104">如果 (`dwOffset`) 不是序列點的 offset 參數，這個方法會取得與先前位移相關聯的行資訊。</span><span class="sxs-lookup"><span data-stu-id="8fe4f-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fe4f-105">語法</span><span class="sxs-lookup"><span data-stu-id="8fe4f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fe4f-106">參數</span><span class="sxs-lookup"><span data-stu-id="8fe4f-106">Parameters</span></span>  

 `dwOffset`  
 <span data-ttu-id="8fe4f-107">在 `ULONG32` 包含位移的。</span><span class="sxs-lookup"><span data-stu-id="8fe4f-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="8fe4f-108">擴展接收該行之的指標 `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="8fe4f-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="8fe4f-109">擴展接收資料行之的指標 `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="8fe4f-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="8fe4f-110">擴展 `ULONG32` 接收結束行之的指標。</span><span class="sxs-lookup"><span data-stu-id="8fe4f-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="8fe4f-111">擴展的指標 `ULONG32` ，會接收 end 資料行。</span><span class="sxs-lookup"><span data-stu-id="8fe4f-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="8fe4f-112">擴展的指標 `ULONG32` ，會接收相關聯的序列點。</span><span class="sxs-lookup"><span data-stu-id="8fe4f-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8fe4f-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="8fe4f-113">Return Value</span></span>  

 <span data-ttu-id="8fe4f-114">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8fe4f-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fe4f-115">需求</span><span class="sxs-lookup"><span data-stu-id="8fe4f-115">Requirements</span></span>  

 <span data-ttu-id="8fe4f-116">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="8fe4f-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe4f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fe4f-117">See also</span></span>

- [<span data-ttu-id="8fe4f-118">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="8fe4f-118">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
