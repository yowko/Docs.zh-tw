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
ms.openlocfilehash: e84639c1d63e6935b9b363f01c12bf0fbd3390e3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615614"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="3a684-102">ISymUnmanagedDocument::GetSourceLength 方法</span><span class="sxs-lookup"><span data-stu-id="3a684-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="3a684-103">取得內嵌來源的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="3a684-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a684-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a684-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a684-105">參數</span><span class="sxs-lookup"><span data-stu-id="3a684-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="3a684-106">脫銷變數的指標，指出內嵌來源的長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="3a684-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a684-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="3a684-107">Return Value</span></span>  
 <span data-ttu-id="3a684-108">如果方法成功，則 S_OK。</span><span class="sxs-lookup"><span data-stu-id="3a684-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a684-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a684-109">See also</span></span>

- [<span data-ttu-id="3a684-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="3a684-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
