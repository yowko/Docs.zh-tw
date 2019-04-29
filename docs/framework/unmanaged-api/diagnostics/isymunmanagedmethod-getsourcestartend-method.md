---
title: ISymUnmanagedMethod::GetSourceStartEnd 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d32e3ac0ff3179a9bb32f82e5ca33fd89c4ec410
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939551"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="16413-102">ISymUnmanagedMethod::GetSourceStartEnd 方法</span><span class="sxs-lookup"><span data-stu-id="16413-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="16413-103">取得這個方法的來源的開始和結束文件位置。</span><span class="sxs-lookup"><span data-stu-id="16413-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="16413-104">第一個陣列位置是起點，而第二個陣列位置是結束。</span><span class="sxs-lookup"><span data-stu-id="16413-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16413-105">語法</span><span class="sxs-lookup"><span data-stu-id="16413-105">Syntax</span></span>  
  
```  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16413-106">參數</span><span class="sxs-lookup"><span data-stu-id="16413-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="16413-107">[in]開始和結束的來源文件。</span><span class="sxs-lookup"><span data-stu-id="16413-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="16413-108">[in]開始和結束行在對應來源文件。</span><span class="sxs-lookup"><span data-stu-id="16413-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="16413-109">[in]開始和結束資料行中對應的來源文件。</span><span class="sxs-lookup"><span data-stu-id="16413-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="16413-110">[out]`true`位置所定義; 否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="16413-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16413-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="16413-111">Return Value</span></span>  
 <span data-ttu-id="16413-112">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="16413-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16413-113">需求</span><span class="sxs-lookup"><span data-stu-id="16413-113">Requirements</span></span>  
 <span data-ttu-id="16413-114">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="16413-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16413-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16413-115">See also</span></span>

- [<span data-ttu-id="16413-116">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="16413-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
