---
title: ISymUnmanagedDocument::FindClosestLine 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.FindClosestLine
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96ad0e34bf638c378f37e317f790696c2ac7cb25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519693"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="3505d-102">ISymUnmanagedDocument::FindClosestLine 方法</span><span class="sxs-lookup"><span data-stu-id="3505d-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="3505d-103">在此可能會或可能不是序列點的文件中會傳回是序列點，最接近的一行。</span><span class="sxs-lookup"><span data-stu-id="3505d-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3505d-104">語法</span><span class="sxs-lookup"><span data-stu-id="3505d-104">Syntax</span></span>  
  
```  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3505d-105">參數</span><span class="sxs-lookup"><span data-stu-id="3505d-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="3505d-106">[in]這份文件中的資料行。</span><span class="sxs-lookup"><span data-stu-id="3505d-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="3505d-107">[out]此變數會接收列指標。</span><span class="sxs-lookup"><span data-stu-id="3505d-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3505d-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="3505d-108">Return Value</span></span>  
 <span data-ttu-id="3505d-109">如果方法成功，則為 S_OK否則，出現錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="3505d-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3505d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3505d-110">See also</span></span>
- [<span data-ttu-id="3505d-111">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="3505d-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
