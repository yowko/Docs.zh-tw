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
ms.openlocfilehash: 1e15bab136540c73f8e1cff0e6bb52ec1d6c0063
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426220"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="6a6e6-102">ISymUnmanagedMethod::GetSourceStartEnd 方法</span><span class="sxs-lookup"><span data-stu-id="6a6e6-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="6a6e6-103">取得這個方法來源的開始和結束文件位置。</span><span class="sxs-lookup"><span data-stu-id="6a6e6-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="6a6e6-104">第一個陣列位置是開始時，而第二個陣列位置為結尾。</span><span class="sxs-lookup"><span data-stu-id="6a6e6-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a6e6-105">語法</span><span class="sxs-lookup"><span data-stu-id="6a6e6-105">Syntax</span></span>  
  
```  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a6e6-106">參數</span><span class="sxs-lookup"><span data-stu-id="6a6e6-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="6a6e6-107">[in]開始和結束的來源文件。</span><span class="sxs-lookup"><span data-stu-id="6a6e6-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="6a6e6-108">[in]開始和結束行中對應的來源文件。</span><span class="sxs-lookup"><span data-stu-id="6a6e6-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="6a6e6-109">[in]開始和結束資料行中對應的來源文件。</span><span class="sxs-lookup"><span data-stu-id="6a6e6-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6a6e6-110">[out]`true`位置所定義; 否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="6a6e6-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a6e6-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="6a6e6-111">Return Value</span></span>  
 <span data-ttu-id="6a6e6-112">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="6a6e6-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a6e6-113">需求</span><span class="sxs-lookup"><span data-stu-id="6a6e6-113">Requirements</span></span>  
 <span data-ttu-id="6a6e6-114">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6a6e6-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a6e6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a6e6-115">See Also</span></span>  
 [<span data-ttu-id="6a6e6-116">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="6a6e6-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
