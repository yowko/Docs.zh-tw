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
ms.openlocfilehash: db2137146ded5200e05bbf88e23ae599f3eb7dec
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615445"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="b6d88-102">ISymUnmanagedReader::ReplaceSymbolStore 方法</span><span class="sxs-lookup"><span data-stu-id="b6d88-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="b6d88-103">以差異符號存放區來取代現有的符號存放區。</span><span class="sxs-lookup"><span data-stu-id="b6d88-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="b6d88-104">這個方法類似于[UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md)方法，不同之處在于指定的差異會作為完整取代，而不是更新。</span><span class="sxs-lookup"><span data-stu-id="b6d88-104">This method is similar to the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6d88-105">您只需要指定其中一個 `filename` 或 `pIStream` 參數，而不是兩者。</span><span class="sxs-lookup"><span data-stu-id="b6d88-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="b6d88-106">如果 `filename` 指定了，符號存放區將會以該檔案中的符號進行更新。</span><span class="sxs-lookup"><span data-stu-id="b6d88-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="b6d88-107">如果 `pIStream` 指定了，則會使用中的資料來更新存放區 <xref:System.Runtime.InteropServices.ComTypes.IStream> 。</span><span class="sxs-lookup"><span data-stu-id="b6d88-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6d88-108">語法</span><span class="sxs-lookup"><span data-stu-id="b6d88-108">Syntax</span></span>  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6d88-109">參數</span><span class="sxs-lookup"><span data-stu-id="b6d88-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="b6d88-110">在包含符號存放區的檔案名。</span><span class="sxs-lookup"><span data-stu-id="b6d88-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="b6d88-111">在檔案資料流程，用來做為參數的替代方法 `filename` 。</span><span class="sxs-lookup"><span data-stu-id="b6d88-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6d88-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="b6d88-112">Return Value</span></span>  
 <span data-ttu-id="b6d88-113">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="b6d88-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6d88-114">需求</span><span class="sxs-lookup"><span data-stu-id="b6d88-114">Requirements</span></span>  
 <span data-ttu-id="b6d88-115">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="b6d88-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6d88-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6d88-116">See also</span></span>

- [<span data-ttu-id="b6d88-117">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="b6d88-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
