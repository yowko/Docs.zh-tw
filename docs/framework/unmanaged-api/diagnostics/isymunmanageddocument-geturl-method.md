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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939811"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="519c2-102">ISymUnmanagedDocument::GetURL 方法</span><span class="sxs-lookup"><span data-stu-id="519c2-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="519c2-103">傳回統一資源定位器 (URL)，這份文件。</span><span class="sxs-lookup"><span data-stu-id="519c2-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="519c2-104">語法</span><span class="sxs-lookup"><span data-stu-id="519c2-104">Syntax</span></span>  
  
```  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="519c2-105">參數</span><span class="sxs-lookup"><span data-stu-id="519c2-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="519c2-106">[in]大小，以字元為單位的`szURL`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="519c2-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="519c2-107">[out]此變數會接收的 URL，包括 null 終止的大小指標。</span><span class="sxs-lookup"><span data-stu-id="519c2-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="519c2-108">[out]包含之 URL 的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="519c2-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="519c2-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="519c2-109">Return Value</span></span>  
 <span data-ttu-id="519c2-110">如果方法成功，則為 S_OK否則，出現錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="519c2-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="519c2-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="519c2-111">See also</span></span>

- [<span data-ttu-id="519c2-112">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="519c2-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
