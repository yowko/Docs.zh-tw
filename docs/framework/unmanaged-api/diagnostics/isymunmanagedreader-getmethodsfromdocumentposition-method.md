---
title: ISymUnmanagedReader::GetMethodsFromDocumentPosition 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
ms.openlocfilehash: bba0fc039c403d45e8a5b60f2b0231eb24226280
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614951"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="699cc-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition 方法</span><span class="sxs-lookup"><span data-stu-id="699cc-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>
<span data-ttu-id="699cc-103">傳回方法的陣列，其中每一個都包含檔中指定位置的中斷點。</span><span class="sxs-lookup"><span data-stu-id="699cc-103">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="699cc-104">語法</span><span class="sxs-lookup"><span data-stu-id="699cc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="699cc-105">參數</span><span class="sxs-lookup"><span data-stu-id="699cc-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="699cc-106">在指定的檔。</span><span class="sxs-lookup"><span data-stu-id="699cc-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="699cc-107">在指定檔的行。</span><span class="sxs-lookup"><span data-stu-id="699cc-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="699cc-108">在指定檔的資料行。</span><span class="sxs-lookup"><span data-stu-id="699cc-108">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="699cc-109">[in] `pRetVal` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="699cc-109">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="699cc-110">脫銷變數的指標，可接收陣列中傳回的元素數目 `pRetVal` 。</span><span class="sxs-lookup"><span data-stu-id="699cc-110">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="699cc-111">脫銷指標陣列，其中每一個都會指向代表包含中斷點之方法的[ISymUnmanagedMethod](isymunmanagedmethod-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="699cc-111">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="699cc-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="699cc-112">Return Value</span></span>  
 <span data-ttu-id="699cc-113">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="699cc-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="699cc-114">需求</span><span class="sxs-lookup"><span data-stu-id="699cc-114">Requirements</span></span>  
 <span data-ttu-id="699cc-115">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="699cc-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="699cc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="699cc-116">See also</span></span>

- [<span data-ttu-id="699cc-117">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="699cc-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
