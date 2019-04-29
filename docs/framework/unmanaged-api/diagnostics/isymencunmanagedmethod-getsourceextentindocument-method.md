---
title: ISymENCUnmanagedMethod::GetSourceExtentInDocument 方法
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 442584cffe4b4ae44702892587e261d41abf4e8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940240"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="946e5-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument 方法</span><span class="sxs-lookup"><span data-stu-id="946e5-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="946e5-103">取得最小起始行和最大的結尾行方法特定的文件中。</span><span class="sxs-lookup"><span data-stu-id="946e5-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="946e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="946e5-104">Syntax</span></span>  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="946e5-105">參數</span><span class="sxs-lookup"><span data-stu-id="946e5-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="946e5-106">[in]文件指標。</span><span class="sxs-lookup"><span data-stu-id="946e5-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="946e5-107">[out]指標`ULONG32`接收之起始行。</span><span class="sxs-lookup"><span data-stu-id="946e5-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="946e5-108">[out]指標`ULONG32`接收之結尾行。</span><span class="sxs-lookup"><span data-stu-id="946e5-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="946e5-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="946e5-109">Return Value</span></span>  
 <span data-ttu-id="946e5-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="946e5-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="946e5-111">需求</span><span class="sxs-lookup"><span data-stu-id="946e5-111">Requirements</span></span>  
 <span data-ttu-id="946e5-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="946e5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="946e5-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="946e5-113">See also</span></span>

- [<span data-ttu-id="946e5-114">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="946e5-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
