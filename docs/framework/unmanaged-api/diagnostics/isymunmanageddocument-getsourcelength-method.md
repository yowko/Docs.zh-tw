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
ms.openlocfilehash: edafb60e5b6f9b913e89f4785dc34a58bf390f2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638765"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="21734-102">ISymUnmanagedDocument::GetSourceLength 方法</span><span class="sxs-lookup"><span data-stu-id="21734-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="21734-103">取得內嵌來源的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="21734-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21734-104">語法</span><span class="sxs-lookup"><span data-stu-id="21734-104">Syntax</span></span>  
  
```  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21734-105">參數</span><span class="sxs-lookup"><span data-stu-id="21734-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="21734-106">[out]表示內嵌來源的長度，以位元組為單位，變數的指標。</span><span class="sxs-lookup"><span data-stu-id="21734-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21734-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="21734-107">Return Value</span></span>  
 <span data-ttu-id="21734-108">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="21734-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21734-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21734-109">See also</span></span>
- [<span data-ttu-id="21734-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="21734-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
