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
ms.openlocfilehash: 134a89d62a0fc455a9579de1e577103f1fe6abcf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449130"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="f2421-102">ISymUnmanagedDocument::GetURL 方法</span><span class="sxs-lookup"><span data-stu-id="f2421-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="f2421-103">傳回此檔的統一資源定位器（URL）。</span><span class="sxs-lookup"><span data-stu-id="f2421-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2421-104">語法</span><span class="sxs-lookup"><span data-stu-id="f2421-104">Syntax</span></span>  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2421-105">參數</span><span class="sxs-lookup"><span data-stu-id="f2421-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="f2421-106">在`szURL` 緩衝區的大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="f2421-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="f2421-107">脫銷接收 URL 大小之變數的指標，包括 null 終止。</span><span class="sxs-lookup"><span data-stu-id="f2421-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="f2421-108">脫銷包含 URL 的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f2421-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2421-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="f2421-109">Return Value</span></span>  
 <span data-ttu-id="f2421-110">如果方法成功，則 S_OK;否則，錯誤碼為。</span><span class="sxs-lookup"><span data-stu-id="f2421-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2421-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2421-111">See also</span></span>

- [<span data-ttu-id="f2421-112">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="f2421-112">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
