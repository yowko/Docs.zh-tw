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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf6a08b17819e3d3cdaa62b0e209fc2064de4a4a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688697"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a><span data-ttu-id="8fc34-102">ISymUnmanagedReader::GetDocumentVersion 方法</span><span class="sxs-lookup"><span data-stu-id="8fc34-102">ISymUnmanagedReader::GetDocumentVersion Method</span></span>
<span data-ttu-id="8fc34-103">取得指定的文件的指定的版本。</span><span class="sxs-lookup"><span data-stu-id="8fc34-103">Gets the specified version of the specified document.</span></span> <span data-ttu-id="8fc34-104">文件版本從 1 開始，就會遞增每次更新文件時使用[UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="8fc34-104">The document version starts at 1 and is incremented each time the document is updated using the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method.</span></span> <span data-ttu-id="8fc34-105">如果`pbCurrent`參數是`true`，這是最新版本的文件。</span><span class="sxs-lookup"><span data-stu-id="8fc34-105">If the `pbCurrent` parameter is `true`, this is the latest version of the document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc34-106">語法</span><span class="sxs-lookup"><span data-stu-id="8fc34-106">Syntax</span></span>  
  
```  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8fc34-107">參數</span><span class="sxs-lookup"><span data-stu-id="8fc34-107">Parameters</span></span>  
 `pDoc`  
 <span data-ttu-id="8fc34-108">[in]指定的文件。</span><span class="sxs-lookup"><span data-stu-id="8fc34-108">[in] The specified document.</span></span>  
  
 `version`  
 <span data-ttu-id="8fc34-109">[out]緩衝區的指標，此變數會接收指定的文件的版本。</span><span class="sxs-lookup"><span data-stu-id="8fc34-109">[out] A pointer to a variable that receives the version of the specified document.</span></span>  
  
 `pbCurrent`  
 <span data-ttu-id="8fc34-110">[out]接收變數的指標`true`如果這是最新版本的文件或`false`如果不是最新版本。</span><span class="sxs-lookup"><span data-stu-id="8fc34-110">[out] A pointer to a variable that receives `true` if this is the latest version of the document, or `false` if it isn't the latest version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8fc34-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="8fc34-111">Return Value</span></span>  
 <span data-ttu-id="8fc34-112">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="8fc34-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fc34-113">需求</span><span class="sxs-lookup"><span data-stu-id="8fc34-113">Requirements</span></span>  
 <span data-ttu-id="8fc34-114">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8fc34-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc34-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fc34-115">See also</span></span>
- [<span data-ttu-id="8fc34-116">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="8fc34-116">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
