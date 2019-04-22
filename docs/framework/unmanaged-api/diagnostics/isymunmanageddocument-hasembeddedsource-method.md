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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d6c79be95ff80c8de9b07cb33be46a5f5db22b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094264"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="805fe-102">ISymUnmanagedDocument::HasEmbeddedSource 方法</span><span class="sxs-lookup"><span data-stu-id="805fe-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="805fe-103">會傳回`true`文件具有來源內嵌在偵錯的符號; 否則會傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="805fe-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="805fe-104">語法</span><span class="sxs-lookup"><span data-stu-id="805fe-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="805fe-105">參數</span><span class="sxs-lookup"><span data-stu-id="805fe-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="805fe-106">[out]此變數會指出是否有來源文件的指標會內嵌在偵錯符號。</span><span class="sxs-lookup"><span data-stu-id="805fe-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="805fe-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="805fe-107">Return Value</span></span>  
 <span data-ttu-id="805fe-108">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="805fe-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="805fe-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="805fe-109">See also</span></span>

- [<span data-ttu-id="805fe-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="805fe-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
