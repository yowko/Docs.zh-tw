---
title: ISymUnmanagedDocument::GetSourceLength 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceLength
helpviewer_keywords:
- GetSourceLength method [.NET Framework debugging]
- ISymUnmanagedDocument::GetSourceLength method [.NET Framework debugging]
ms.assetid: e087dbbb-f4fb-4fbe-8292-e4f1a14d0df2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11ab9f8077a4b2a9e97c321c6edbe629dc0de19d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500729"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="ad863-102">ISymUnmanagedDocument::GetSourceLength 方法</span><span class="sxs-lookup"><span data-stu-id="ad863-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="ad863-103">取得內嵌來源的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="ad863-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad863-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad863-104">Syntax</span></span>  
  
```  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad863-105">參數</span><span class="sxs-lookup"><span data-stu-id="ad863-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ad863-106">[out]表示內嵌來源的長度，以位元組為單位，變數的指標。</span><span class="sxs-lookup"><span data-stu-id="ad863-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad863-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ad863-107">Return Value</span></span>  
 <span data-ttu-id="ad863-108">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="ad863-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad863-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad863-109">See also</span></span>
- [<span data-ttu-id="ad863-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="ad863-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
