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
ms.openlocfilehash: 620d303bcd33a4d04155850ec2c1b6293bf788d1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493254"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="b68a7-102">ISymUnmanagedDocument::HasEmbeddedSource 方法</span><span class="sxs-lookup"><span data-stu-id="b68a7-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="b68a7-103">會傳回`true`文件具有來源內嵌在偵錯的符號; 否則會傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="b68a7-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b68a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="b68a7-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b68a7-105">參數</span><span class="sxs-lookup"><span data-stu-id="b68a7-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="b68a7-106">[out]此變數會指出是否有來源文件的指標會內嵌在偵錯符號。</span><span class="sxs-lookup"><span data-stu-id="b68a7-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b68a7-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b68a7-107">Return Value</span></span>  
 <span data-ttu-id="b68a7-108">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="b68a7-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b68a7-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b68a7-109">See also</span></span>
- [<span data-ttu-id="b68a7-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="b68a7-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
