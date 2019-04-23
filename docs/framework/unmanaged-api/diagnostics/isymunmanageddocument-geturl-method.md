---
title: ISymUnmanagedDocument::GetURL 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15b42bb72975fad4c1830a961f83d9e3065d055b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187456"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="94784-102">ISymUnmanagedDocument::GetURL 方法</span><span class="sxs-lookup"><span data-stu-id="94784-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="94784-103">傳回統一資源定位器 (URL)，這份文件。</span><span class="sxs-lookup"><span data-stu-id="94784-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94784-104">語法</span><span class="sxs-lookup"><span data-stu-id="94784-104">Syntax</span></span>  
  
```  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94784-105">參數</span><span class="sxs-lookup"><span data-stu-id="94784-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="94784-106">[in]大小，以字元為單位的`szURL`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="94784-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="94784-107">[out]此變數會接收的 URL，包括 null 終止的大小指標。</span><span class="sxs-lookup"><span data-stu-id="94784-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="94784-108">[out]包含之 URL 的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="94784-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94784-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="94784-109">Return Value</span></span>  
 <span data-ttu-id="94784-110">如果方法成功，則為 S_OK否則，出現錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="94784-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94784-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94784-111">See also</span></span>

- [<span data-ttu-id="94784-112">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="94784-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
