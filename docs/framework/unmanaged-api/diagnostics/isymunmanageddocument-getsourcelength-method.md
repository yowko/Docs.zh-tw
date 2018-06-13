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
ms.openlocfilehash: 3341159600c85915cd3c1a138265dc386edbb766
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424114"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="03941-102">ISymUnmanagedDocument::GetSourceLength 方法</span><span class="sxs-lookup"><span data-stu-id="03941-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="03941-103">取得內嵌來源的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="03941-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03941-104">語法</span><span class="sxs-lookup"><span data-stu-id="03941-104">Syntax</span></span>  
  
```  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03941-105">參數</span><span class="sxs-lookup"><span data-stu-id="03941-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="03941-106">[out]指出內嵌來源的長度，以位元組為單位，變數的指標。</span><span class="sxs-lookup"><span data-stu-id="03941-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03941-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="03941-107">Return Value</span></span>  
 <span data-ttu-id="03941-108">如果此方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="03941-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03941-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03941-109">See Also</span></span>  
 [<span data-ttu-id="03941-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="03941-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
