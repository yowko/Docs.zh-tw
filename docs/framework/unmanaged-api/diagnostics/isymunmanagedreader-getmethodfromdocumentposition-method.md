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
ms.openlocfilehash: 417644e5d0c7af802d5266bd1825efa83c181597
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689598"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="74971-102">ISymUnmanagedReader::GetMethodFromDocumentPosition 方法</span><span class="sxs-lookup"><span data-stu-id="74971-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>

<span data-ttu-id="74971-103">傳回方法，這個方法會在檔中的指定位置包含中斷點。</span><span class="sxs-lookup"><span data-stu-id="74971-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74971-104">語法</span><span class="sxs-lookup"><span data-stu-id="74971-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74971-105">參數</span><span class="sxs-lookup"><span data-stu-id="74971-105">Parameters</span></span>  

 `document`  
 <span data-ttu-id="74971-106">在指定的檔。</span><span class="sxs-lookup"><span data-stu-id="74971-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="74971-107">在指定檔的行。</span><span class="sxs-lookup"><span data-stu-id="74971-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="74971-108">在指定檔的資料行。</span><span class="sxs-lookup"><span data-stu-id="74971-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="74971-109">擴展 [ISymUnmanagedMethod 介面](isymunmanagedmethod-interface.md) 物件位址的指標，該物件表示包含中斷點的方法。</span><span class="sxs-lookup"><span data-stu-id="74971-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74971-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="74971-110">Return Value</span></span>  

 <span data-ttu-id="74971-111">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="74971-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74971-112">需求</span><span class="sxs-lookup"><span data-stu-id="74971-112">Requirements</span></span>  

 <span data-ttu-id="74971-113">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="74971-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74971-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74971-114">See also</span></span>

- [<span data-ttu-id="74971-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="74971-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
