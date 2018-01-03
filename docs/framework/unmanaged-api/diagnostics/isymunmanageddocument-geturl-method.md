---
title: "ISymUnmanagedDocument::GetURL 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetURL
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2688c2c50181c7bac7b7ee869b4e1fa5094d0ea9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="810d5-102">ISymUnmanagedDocument::GetURL 方法</span><span class="sxs-lookup"><span data-stu-id="810d5-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="810d5-103">傳回這份文件的統一資源定位器 (URL)。</span><span class="sxs-lookup"><span data-stu-id="810d5-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="810d5-104">語法</span><span class="sxs-lookup"><span data-stu-id="810d5-104">Syntax</span></span>  
  
```  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="810d5-105">參數</span><span class="sxs-lookup"><span data-stu-id="810d5-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="810d5-106">[in]大小，以字元為單位的`szURL`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="810d5-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="810d5-107">[out]大小的 URL，包括 null 結束之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="810d5-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="810d5-108">[out]包含 URL 的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="810d5-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="810d5-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="810d5-109">Return Value</span></span>  
 <span data-ttu-id="810d5-110">如果方法成功則為 S_OK否則，錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="810d5-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="810d5-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="810d5-111">See Also</span></span>  
 [<span data-ttu-id="810d5-112">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="810d5-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
