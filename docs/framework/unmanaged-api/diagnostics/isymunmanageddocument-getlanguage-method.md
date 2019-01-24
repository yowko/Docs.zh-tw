---
title: ISymUnmanagedDocument::GetLanguage 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguage
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 186ea5fd46ca5c6205ff1f98d8964e656655a2ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666029"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="db12b-102">ISymUnmanagedDocument::GetLanguage 方法</span><span class="sxs-lookup"><span data-stu-id="db12b-102">ISymUnmanagedDocument::GetLanguage Method</span></span>
<span data-ttu-id="db12b-103">取得這份文件的語言識別碼</span><span class="sxs-lookup"><span data-stu-id="db12b-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db12b-104">語法</span><span class="sxs-lookup"><span data-stu-id="db12b-104">Syntax</span></span>  
  
```  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db12b-105">參數</span><span class="sxs-lookup"><span data-stu-id="db12b-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="db12b-106">[out]接收的語言識別碼的變數指標。</span><span class="sxs-lookup"><span data-stu-id="db12b-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db12b-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="db12b-107">Return Value</span></span>  
 <span data-ttu-id="db12b-108">如果方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="db12b-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db12b-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db12b-109">See also</span></span>
- [<span data-ttu-id="db12b-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="db12b-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
