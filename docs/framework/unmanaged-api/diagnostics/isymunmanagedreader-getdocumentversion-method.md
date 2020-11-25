---
title: ISymUnmanagedReader::GetDocumentVersion 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
ms.openlocfilehash: fc38c167b47ea72c7bc7ad81074f9cb1a0d217d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707563"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="8e0f3-102">ISymUnmanagedReader::GetDocumentVersion 方法</span><span class="sxs-lookup"><span data-stu-id="8e0f3-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>

<span data-ttu-id="8e0f3-103">取得指定之檔的指定版本。</span><span class="sxs-lookup"><span data-stu-id="8e0f3-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="8e0f3-104">檔版本從1開始，而且每次使用 [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) 方法更新檔時，都會遞增。</span><span class="sxs-lookup"><span data-stu-id="8e0f3-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="8e0f3-105">如果 `pbCurrent` 參數為 `true` ，則這是檔的最新版本。</span><span class="sxs-lookup"><span data-stu-id="8e0f3-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e0f3-106">語法</span><span class="sxs-lookup"><span data-stu-id="8e0f3-106">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e0f3-107">參數</span><span class="sxs-lookup"><span data-stu-id="8e0f3-107">Parameters</span></span>  

 `pDoc`  
 <span data-ttu-id="8e0f3-108">在指定的檔。</span><span class="sxs-lookup"><span data-stu-id="8e0f3-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="8e0f3-109">擴展變數的指標，此變數會接收指定檔的版本。</span><span class="sxs-lookup"><span data-stu-id="8e0f3-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="8e0f3-110">擴展 `true` 如果這是檔的最新版本，或 `false` 不是最新版本，則為收到之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="8e0f3-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e0f3-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="8e0f3-111">Return Value</span></span>  

 <span data-ttu-id="8e0f3-112">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8e0f3-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e0f3-113">需求</span><span class="sxs-lookup"><span data-stu-id="8e0f3-113">Requirements</span></span>  

 <span data-ttu-id="8e0f3-114">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="8e0f3-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e0f3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e0f3-115">See also</span></span>

- [<span data-ttu-id="8e0f3-116">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="8e0f3-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
