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
ms.openlocfilehash: c862b6d3bfa415b622b68898db1ff30c6759e8f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726934"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="17db3-102">ISymUnmanagedDocument::GetURL 方法</span><span class="sxs-lookup"><span data-stu-id="17db3-102">ISymUnmanagedDocument::GetURL Method</span></span>

<span data-ttu-id="17db3-103">傳回此檔 (URL) 的統一資源定位器。</span><span class="sxs-lookup"><span data-stu-id="17db3-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17db3-104">語法</span><span class="sxs-lookup"><span data-stu-id="17db3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17db3-105">參數</span><span class="sxs-lookup"><span data-stu-id="17db3-105">Parameters</span></span>  

 `cchUrl`  
 <span data-ttu-id="17db3-106">在緩衝區的大小（以字元為單位） `szURL` 。</span><span class="sxs-lookup"><span data-stu-id="17db3-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="17db3-107">擴展變數的指標，此變數會接收 URL 的大小，包括 null 終止。</span><span class="sxs-lookup"><span data-stu-id="17db3-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="17db3-108">擴展包含 URL 的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="17db3-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17db3-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="17db3-109">Return Value</span></span>  

 <span data-ttu-id="17db3-110">如果方法成功，則為 S_OK;否則為錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="17db3-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17db3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17db3-111">See also</span></span>

- [<span data-ttu-id="17db3-112">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="17db3-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
