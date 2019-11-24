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
ms.openlocfilehash: 60c3537a80c39f758f46e6f2f0a5f2bcd27350b5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445729"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="37d45-102">ISymUnmanagedReader::ReplaceSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="37d45-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="37d45-103">以差異符號存放區來取代現有的符號存放區。</span><span class="sxs-lookup"><span data-stu-id="37d45-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="37d45-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span><span class="sxs-lookup"><span data-stu-id="37d45-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37d45-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span><span class="sxs-lookup"><span data-stu-id="37d45-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="37d45-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span><span class="sxs-lookup"><span data-stu-id="37d45-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="37d45-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="37d45-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37d45-108">語法</span><span class="sxs-lookup"><span data-stu-id="37d45-108">Syntax</span></span>  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37d45-109">參數</span><span class="sxs-lookup"><span data-stu-id="37d45-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="37d45-110">[in] The name of the file containing the symbol store.</span><span class="sxs-lookup"><span data-stu-id="37d45-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="37d45-111">[in] The file stream, used as an alternative to the `filename` parameter.</span><span class="sxs-lookup"><span data-stu-id="37d45-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37d45-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="37d45-112">Return Value</span></span>  
 <span data-ttu-id="37d45-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="37d45-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37d45-114">需求</span><span class="sxs-lookup"><span data-stu-id="37d45-114">Requirements</span></span>  
 <span data-ttu-id="37d45-115">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="37d45-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37d45-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="37d45-116">See also</span></span>

- [<span data-ttu-id="37d45-117">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="37d45-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
