---
title: "ISymUnmanagedDocument::GetLanguage 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetLanguage
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: af0ffb422ec677997b6e2b6323b975ba4d69e5ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="5fb89-102">ISymUnmanagedDocument::GetLanguage 方法</span><span class="sxs-lookup"><span data-stu-id="5fb89-102">ISymUnmanagedDocument::GetLanguage Method</span></span>
<span data-ttu-id="5fb89-103">取得這份文件的語言識別項</span><span class="sxs-lookup"><span data-stu-id="5fb89-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fb89-104">語法</span><span class="sxs-lookup"><span data-stu-id="5fb89-104">Syntax</span></span>  
  
```  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5fb89-105">參數</span><span class="sxs-lookup"><span data-stu-id="5fb89-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="5fb89-106">[out]此變數會接收的語言識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="5fb89-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5fb89-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5fb89-107">Return Value</span></span>  
 <span data-ttu-id="5fb89-108">如果此方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="5fb89-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fb89-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fb89-109">See Also</span></span>  
 [<span data-ttu-id="5fb89-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="5fb89-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
