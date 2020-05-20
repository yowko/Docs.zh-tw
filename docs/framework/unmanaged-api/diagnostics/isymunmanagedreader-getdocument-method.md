---
title: ISymUnmanagedReader::GetDocument 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type:
- apiref
ms.openlocfilehash: 950fb3b9c51ae2c9470b5aadd31c877d7aa6b6f6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615055"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="05e02-102">ISymUnmanagedReader::GetDocument 方法</span><span class="sxs-lookup"><span data-stu-id="05e02-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="05e02-103">尋找檔。</span><span class="sxs-lookup"><span data-stu-id="05e02-103">Finds a document.</span></span> <span data-ttu-id="05e02-104">檔語言、廠商和類型都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="05e02-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05e02-105">語法</span><span class="sxs-lookup"><span data-stu-id="05e02-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05e02-106">參數</span><span class="sxs-lookup"><span data-stu-id="05e02-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="05e02-107">在識別檔的 URL。</span><span class="sxs-lookup"><span data-stu-id="05e02-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="05e02-108">在檔語言。</span><span class="sxs-lookup"><span data-stu-id="05e02-108">[in] The document language.</span></span> <span data-ttu-id="05e02-109">此為選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="05e02-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="05e02-110">在檔語言的廠商身分識別。</span><span class="sxs-lookup"><span data-stu-id="05e02-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="05e02-111">此為選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="05e02-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="05e02-112">在檔的類型。</span><span class="sxs-lookup"><span data-stu-id="05e02-112">[in] The type of the document.</span></span> <span data-ttu-id="05e02-113">此為選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="05e02-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="05e02-114">脫銷傳回之介面的指標。</span><span class="sxs-lookup"><span data-stu-id="05e02-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05e02-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="05e02-115">Return Value</span></span>  
 <span data-ttu-id="05e02-116">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="05e02-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05e02-117">需求</span><span class="sxs-lookup"><span data-stu-id="05e02-117">Requirements</span></span>  
 <span data-ttu-id="05e02-118">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="05e02-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05e02-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05e02-119">See also</span></span>

- [<span data-ttu-id="05e02-120">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="05e02-120">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
