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
ms.openlocfilehash: c2cc541b2a78f16d5ca6b19405794faa825a9d72
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615029"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="d6dd3-102">ISymUnmanagedReader::GetDocumentVersion 方法</span><span class="sxs-lookup"><span data-stu-id="d6dd3-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="d6dd3-103">取得指定檔的指定版本。</span><span class="sxs-lookup"><span data-stu-id="d6dd3-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="d6dd3-104">檔版本從1開始，而且每次使用[UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md)方法更新檔時，都會遞增。</span><span class="sxs-lookup"><span data-stu-id="d6dd3-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="d6dd3-105">如果 `pbCurrent` 參數為 `true` ，則這是檔的最新版本。</span><span class="sxs-lookup"><span data-stu-id="d6dd3-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6dd3-106">語法</span><span class="sxs-lookup"><span data-stu-id="d6dd3-106">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6dd3-107">參數</span><span class="sxs-lookup"><span data-stu-id="d6dd3-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="d6dd3-108">在指定的檔。</span><span class="sxs-lookup"><span data-stu-id="d6dd3-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="d6dd3-109">脫銷接收指定檔之版本之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="d6dd3-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="d6dd3-110">脫銷`true`如果這是檔的最新版本，或 `false` 如果不是最新版本，則為所接收之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="d6dd3-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6dd3-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="d6dd3-111">Return Value</span></span>  
 <span data-ttu-id="d6dd3-112">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d6dd3-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6dd3-113">需求</span><span class="sxs-lookup"><span data-stu-id="d6dd3-113">Requirements</span></span>  
 <span data-ttu-id="d6dd3-114">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d6dd3-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6dd3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6dd3-115">See also</span></span>

- [<span data-ttu-id="d6dd3-116">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="d6dd3-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
