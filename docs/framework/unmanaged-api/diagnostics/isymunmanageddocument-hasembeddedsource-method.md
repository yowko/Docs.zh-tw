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
ms.openlocfilehash: 350aecb9f9c99c9aa44ae6df6d31c7cb69ae5760
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430341"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="8387a-102">ISymUnmanagedDocument::HasEmbeddedSource 方法</span><span class="sxs-lookup"><span data-stu-id="8387a-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="8387a-103">傳回`true`如果文件來源內嵌在偵錯符號; 否則傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="8387a-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8387a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8387a-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8387a-105">參數</span><span class="sxs-lookup"><span data-stu-id="8387a-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="8387a-106">[out]此變數會指出是否有來源文件的指標會內嵌在偵錯符號。</span><span class="sxs-lookup"><span data-stu-id="8387a-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8387a-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="8387a-107">Return Value</span></span>  
 <span data-ttu-id="8387a-108">如果此方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="8387a-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8387a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8387a-109">See Also</span></span>  
 [<span data-ttu-id="8387a-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="8387a-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
