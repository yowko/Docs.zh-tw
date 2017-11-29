---
title: "ISymUnmanagedDocument::GetSourceLength 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetSourceLength
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetSourceLength
helpviewer_keywords:
- GetSourceLength method [.NET Framework debugging]
- ISymUnmanagedDocument::GetSourceLength method [.NET Framework debugging]
ms.assetid: e087dbbb-f4fb-4fbe-8292-e4f1a14d0df2
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b4bf318303b1d787df100051a5c2d3fdd0ac5918
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="db05e-102">ISymUnmanagedDocument::GetSourceLength 方法</span><span class="sxs-lookup"><span data-stu-id="db05e-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="db05e-103">取得內嵌來源的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="db05e-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db05e-104">語法</span><span class="sxs-lookup"><span data-stu-id="db05e-104">Syntax</span></span>  
  
```  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db05e-105">參數</span><span class="sxs-lookup"><span data-stu-id="db05e-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="db05e-106">[out]指出內嵌來源的長度，以位元組為單位，變數的指標。</span><span class="sxs-lookup"><span data-stu-id="db05e-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db05e-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="db05e-107">Return Value</span></span>  
 <span data-ttu-id="db05e-108">如果此方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="db05e-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db05e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db05e-109">See Also</span></span>  
 [<span data-ttu-id="db05e-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="db05e-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
