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
ms.openlocfilehash: bf79c05b3b16bb61ac59534dd83cb8eb2bb1f823
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776710"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="96371-102">ISymUnmanagedDocument::GetSourceLength 方法</span><span class="sxs-lookup"><span data-stu-id="96371-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="96371-103">取得內嵌來源的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="96371-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96371-104">語法</span><span class="sxs-lookup"><span data-stu-id="96371-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96371-105">參數</span><span class="sxs-lookup"><span data-stu-id="96371-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="96371-106">[out]表示內嵌來源的長度，以位元組為單位，變數的指標。</span><span class="sxs-lookup"><span data-stu-id="96371-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96371-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="96371-107">Return Value</span></span>  
 <span data-ttu-id="96371-108">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="96371-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96371-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96371-109">See also</span></span>

- [<span data-ttu-id="96371-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="96371-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
