---
title: ISymUnmanagedDocument::HasEmbeddedSource 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
ms.openlocfilehash: d654f6d57bd784063fc7f87dd9767bdc27ad2776
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615575"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="57aa5-102">ISymUnmanagedDocument::HasEmbeddedSource 方法</span><span class="sxs-lookup"><span data-stu-id="57aa5-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="57aa5-103">`true`如果檔的來源內嵌在偵錯工具符號中，則傳回，否則傳回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="57aa5-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57aa5-104">語法</span><span class="sxs-lookup"><span data-stu-id="57aa5-104">Syntax</span></span>  
  
```cpp  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57aa5-105">參數</span><span class="sxs-lookup"><span data-stu-id="57aa5-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="57aa5-106">脫銷變數的指標，指出檔是否有內嵌在偵錯工具符號中的來源。</span><span class="sxs-lookup"><span data-stu-id="57aa5-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57aa5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="57aa5-107">Return Value</span></span>  
 <span data-ttu-id="57aa5-108">如果方法成功，則 S_OK。</span><span class="sxs-lookup"><span data-stu-id="57aa5-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57aa5-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57aa5-109">See also</span></span>

- [<span data-ttu-id="57aa5-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="57aa5-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
