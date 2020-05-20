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
ms.openlocfilehash: 3685707f1983ffec413e9cea2df5034ac53f643a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615588"
---
# <a name="isymunmanageddocumentgeturl-method"></a><span data-ttu-id="c540c-102">ISymUnmanagedDocument::GetURL 方法</span><span class="sxs-lookup"><span data-stu-id="c540c-102">ISymUnmanagedDocument::GetURL Method</span></span>
<span data-ttu-id="c540c-103">傳回此檔的統一資源定位器（URL）。</span><span class="sxs-lookup"><span data-stu-id="c540c-103">Returns the uniform resource locator (URL) for this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c540c-104">語法</span><span class="sxs-lookup"><span data-stu-id="c540c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c540c-105">參數</span><span class="sxs-lookup"><span data-stu-id="c540c-105">Parameters</span></span>  
 `cchUrl`  
 <span data-ttu-id="c540c-106">在緩衝區的大小（以字元為單位） `szURL` 。</span><span class="sxs-lookup"><span data-stu-id="c540c-106">[in] The size, in characters, of the `szURL` buffer.</span></span>  
  
 `pcchUrl`  
 <span data-ttu-id="c540c-107">脫銷接收 URL 大小之變數的指標，包括 null 終止。</span><span class="sxs-lookup"><span data-stu-id="c540c-107">[out] A pointer to a variable that receives the size of the URL, including the null termination.</span></span>  
  
 `szUrl`  
 <span data-ttu-id="c540c-108">脫銷包含 URL 的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c540c-108">[out] The buffer containing the URL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c540c-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="c540c-109">Return Value</span></span>  
 <span data-ttu-id="c540c-110">如果方法成功，則 S_OK;否則，錯誤碼為。</span><span class="sxs-lookup"><span data-stu-id="c540c-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c540c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c540c-111">See also</span></span>

- [<span data-ttu-id="c540c-112">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="c540c-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
