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
ms.openlocfilehash: 760a6feb8400e60b7e14bf244d66c9026031e5dc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474233"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="a7a3e-102">ISymUnmanagedDocument::FindClosestLine 方法</span><span class="sxs-lookup"><span data-stu-id="a7a3e-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="a7a3e-103">在此可能會或可能不是序列點的文件中會傳回是序列點，最接近的一行。</span><span class="sxs-lookup"><span data-stu-id="a7a3e-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7a3e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7a3e-104">Syntax</span></span>  
  
```  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7a3e-105">參數</span><span class="sxs-lookup"><span data-stu-id="a7a3e-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="a7a3e-106">[in]這份文件中的資料行。</span><span class="sxs-lookup"><span data-stu-id="a7a3e-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a7a3e-107">[out]此變數會接收列指標。</span><span class="sxs-lookup"><span data-stu-id="a7a3e-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7a3e-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a7a3e-108">Return Value</span></span>  
 <span data-ttu-id="a7a3e-109">如果方法成功，則為 S_OK否則，出現錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="a7a3e-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a3e-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7a3e-110">See also</span></span>
- [<span data-ttu-id="a7a3e-111">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="a7a3e-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
