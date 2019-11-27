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
ms.openlocfilehash: 3bc578be680951a1d41c92fb2169c860882b2e31
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448303"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="d1939-102">ISymUnmanagedReader::GetDocumentVersion 方法</span><span class="sxs-lookup"><span data-stu-id="d1939-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="d1939-103">取得指定檔的指定版本。</span><span class="sxs-lookup"><span data-stu-id="d1939-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="d1939-104">檔版本從1開始，而且每次使用[UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)方法更新檔時，都會遞增。</span><span class="sxs-lookup"><span data-stu-id="d1939-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="d1939-105">如果 `pbCurrent` 參數是 `true`，這就是檔的最新版本。</span><span class="sxs-lookup"><span data-stu-id="d1939-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1939-106">語法</span><span class="sxs-lookup"><span data-stu-id="d1939-106">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1939-107">參數</span><span class="sxs-lookup"><span data-stu-id="d1939-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="d1939-108">在指定的檔。</span><span class="sxs-lookup"><span data-stu-id="d1939-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="d1939-109">脫銷接收指定檔之版本之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="d1939-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="d1939-110">脫銷如果這是檔的最新版本，則為接收 `true` 之變數的指標，如果不是最新版本，則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="d1939-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1939-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="d1939-111">Return Value</span></span>  
 <span data-ttu-id="d1939-112">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d1939-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1939-113">需求</span><span class="sxs-lookup"><span data-stu-id="d1939-113">Requirements</span></span>  
 <span data-ttu-id="d1939-114">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d1939-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1939-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="d1939-115">See also</span></span>

- [<span data-ttu-id="d1939-116">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="d1939-116">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
