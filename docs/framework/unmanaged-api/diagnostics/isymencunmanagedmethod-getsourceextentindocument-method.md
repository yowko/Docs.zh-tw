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
ms.openlocfilehash: 5f29111fd68d9a47cd90687cc6aa2743968e727d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484598"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="d1bc9-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument 方法</span><span class="sxs-lookup"><span data-stu-id="d1bc9-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="d1bc9-103">取得最小起始行和最大的結尾行方法特定的文件中。</span><span class="sxs-lookup"><span data-stu-id="d1bc9-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1bc9-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1bc9-104">Syntax</span></span>  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1bc9-105">參數</span><span class="sxs-lookup"><span data-stu-id="d1bc9-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="d1bc9-106">[in]文件指標。</span><span class="sxs-lookup"><span data-stu-id="d1bc9-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="d1bc9-107">[out]指標`ULONG32`接收之起始行。</span><span class="sxs-lookup"><span data-stu-id="d1bc9-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="d1bc9-108">[out]指標`ULONG32`接收之結尾行。</span><span class="sxs-lookup"><span data-stu-id="d1bc9-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1bc9-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="d1bc9-109">Return Value</span></span>  
 <span data-ttu-id="d1bc9-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="d1bc9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1bc9-111">需求</span><span class="sxs-lookup"><span data-stu-id="d1bc9-111">Requirements</span></span>  
 <span data-ttu-id="d1bc9-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d1bc9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1bc9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1bc9-113">See also</span></span>
- [<span data-ttu-id="d1bc9-114">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="d1bc9-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
