---
title: ISymUnmanagedReader::ReplaceSymbolStore 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 34d93c6956ff391e4d8726d8e45265c96947ad4c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154761"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="f56fb-102">ISymUnmanagedReader::ReplaceSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="f56fb-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="f56fb-103">以差異符號存放區來取代現有的符號存放區。</span><span class="sxs-lookup"><span data-stu-id="f56fb-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="f56fb-104">這個方法很類似[UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)方法，不同之處在於指定的差異可做為完全取代，而不是更新。</span><span class="sxs-lookup"><span data-stu-id="f56fb-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f56fb-105">您需要指定的其中之一`filename`或`pIStream`不可同時為兩者的參數。</span><span class="sxs-lookup"><span data-stu-id="f56fb-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="f56fb-106">如果`filename`指定符號存放區將會更新該檔案中的符號。</span><span class="sxs-lookup"><span data-stu-id="f56fb-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="f56fb-107">如果`pIStream`未指定，將使用中的資料更新存放區<xref:System.Runtime.InteropServices.ComTypes.IStream>。</span><span class="sxs-lookup"><span data-stu-id="f56fb-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f56fb-108">語法</span><span class="sxs-lookup"><span data-stu-id="f56fb-108">Syntax</span></span>  
  
```  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f56fb-109">參數</span><span class="sxs-lookup"><span data-stu-id="f56fb-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="f56fb-110">[in]包含符號存放區的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f56fb-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="f56fb-111">[in]檔案資料流，做為替代`filename`參數。</span><span class="sxs-lookup"><span data-stu-id="f56fb-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f56fb-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="f56fb-112">Return Value</span></span>  
 <span data-ttu-id="f56fb-113">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="f56fb-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f56fb-114">需求</span><span class="sxs-lookup"><span data-stu-id="f56fb-114">Requirements</span></span>  
 <span data-ttu-id="f56fb-115">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f56fb-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f56fb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f56fb-116">See also</span></span>

- [<span data-ttu-id="f56fb-117">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="f56fb-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
