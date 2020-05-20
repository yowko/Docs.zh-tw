---
title: ISymUnmanagedReader::GetMethodFromDocumentPosition 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type:
- apiref
ms.openlocfilehash: 8015056b110fe8a5b5122b1bc81143980b780047
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614977"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="780e6-102">ISymUnmanagedReader::GetMethodFromDocumentPosition 方法</span><span class="sxs-lookup"><span data-stu-id="780e6-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="780e6-103">傳回方法，其中包含檔中指定位置的中斷點。</span><span class="sxs-lookup"><span data-stu-id="780e6-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="780e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="780e6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="780e6-105">參數</span><span class="sxs-lookup"><span data-stu-id="780e6-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="780e6-106">在指定的檔。</span><span class="sxs-lookup"><span data-stu-id="780e6-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="780e6-107">在指定檔的行。</span><span class="sxs-lookup"><span data-stu-id="780e6-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="780e6-108">在指定檔的資料行。</span><span class="sxs-lookup"><span data-stu-id="780e6-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="780e6-109">脫銷[ISymUnmanagedMethod 介面](isymunmanagedmethod-interface.md)物件位址的指標，表示包含中斷點的方法。</span><span class="sxs-lookup"><span data-stu-id="780e6-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="780e6-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="780e6-110">Return Value</span></span>  
 <span data-ttu-id="780e6-111">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="780e6-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="780e6-112">需求</span><span class="sxs-lookup"><span data-stu-id="780e6-112">Requirements</span></span>  
 <span data-ttu-id="780e6-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="780e6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="780e6-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="780e6-114">See also</span></span>

- [<span data-ttu-id="780e6-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="780e6-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
