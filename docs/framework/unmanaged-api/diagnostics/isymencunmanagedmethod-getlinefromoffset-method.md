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
ms.openlocfilehash: 29990ad6a94f063577236bdbc84d02d4d2b4b2f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426129"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="4fa25-102">ISymENCUnmanagedMethod::GetLineFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="4fa25-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>
<span data-ttu-id="4fa25-103">取得相關聯的位移的行資訊。</span><span class="sxs-lookup"><span data-stu-id="4fa25-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="4fa25-104">如果位移的參數 (`dwOffset`) 不是序列點，這個方法會取得相關聯的上一個位移的行資訊。</span><span class="sxs-lookup"><span data-stu-id="4fa25-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fa25-105">語法</span><span class="sxs-lookup"><span data-stu-id="4fa25-105">Syntax</span></span>  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4fa25-106">參數</span><span class="sxs-lookup"><span data-stu-id="4fa25-106">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="4fa25-107">[in]A`ULONG32`包含位移。</span><span class="sxs-lookup"><span data-stu-id="4fa25-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="4fa25-108">[out]指標`ULONG32`接收之列。</span><span class="sxs-lookup"><span data-stu-id="4fa25-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="4fa25-109">[out]指標`ULONG32`接收的資料行。</span><span class="sxs-lookup"><span data-stu-id="4fa25-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="4fa25-110">[out]指標`ULONG32`接收之結尾行。</span><span class="sxs-lookup"><span data-stu-id="4fa25-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="4fa25-111">[out]指標`ULONG32`接收結束資料行。</span><span class="sxs-lookup"><span data-stu-id="4fa25-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="4fa25-112">[out]指標`ULONG32`接收相關聯的序列點。</span><span class="sxs-lookup"><span data-stu-id="4fa25-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4fa25-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="4fa25-113">Return Value</span></span>  
 <span data-ttu-id="4fa25-114">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="4fa25-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fa25-115">需求</span><span class="sxs-lookup"><span data-stu-id="4fa25-115">Requirements</span></span>  
 <span data-ttu-id="4fa25-116">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4fa25-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa25-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fa25-117">See Also</span></span>  
 [<span data-ttu-id="4fa25-118">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="4fa25-118">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
