---
title: "ISymUnmanagedDocument::FindClosestLine 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.FindClosestLine
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8a4fff5ce5cdcde35c8483136cf4c3cd75854f6c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="05d96-102">ISymUnmanagedDocument::FindClosestLine 方法</span><span class="sxs-lookup"><span data-stu-id="05d96-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="05d96-103">傳回最接近的一行，也就是序列點，在本文件也可能不是序列點中。</span><span class="sxs-lookup"><span data-stu-id="05d96-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05d96-104">語法</span><span class="sxs-lookup"><span data-stu-id="05d96-104">Syntax</span></span>  
  
```  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05d96-105">參數</span><span class="sxs-lookup"><span data-stu-id="05d96-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="05d96-106">[in]這份文件中的行。</span><span class="sxs-lookup"><span data-stu-id="05d96-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="05d96-107">[out]接收行變數的指標。</span><span class="sxs-lookup"><span data-stu-id="05d96-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05d96-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="05d96-108">Return Value</span></span>  
 <span data-ttu-id="05d96-109">如果方法成功則為 S_OK否則，錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="05d96-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05d96-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05d96-110">See Also</span></span>  
 [<span data-ttu-id="05d96-111">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="05d96-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
