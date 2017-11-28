---
title: "ISymUnmanagedDocument::GetLanguageVendor 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetLanguageVendor
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetLanguageVendor
helpviewer_keywords:
- GetLanguageVendor method [.NET Framework debugging]
- ISymUnmanagedDocument::GetLanguageVendor method [.NET Framework debugging]
ms.assetid: 1d4b702e-4922-441d-8b44-03804284f70b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 72fffae9995f44be9a9359c16bb876d79c9a8242
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="a2ead-102">ISymUnmanagedDocument::GetLanguageVendor 方法</span><span class="sxs-lookup"><span data-stu-id="a2ead-102">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>
<span data-ttu-id="a2ead-103">取得這份文件的語言廠商。</span><span class="sxs-lookup"><span data-stu-id="a2ead-103">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2ead-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2ead-104">Syntax</span></span>  
  
```  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2ead-105">參數</span><span class="sxs-lookup"><span data-stu-id="a2ead-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a2ead-106">[out]接收的語言廠商變數的指標。</span><span class="sxs-lookup"><span data-stu-id="a2ead-106">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2ead-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="a2ead-107">Return Value</span></span>  
 <span data-ttu-id="a2ead-108">如果此方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="a2ead-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ead-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2ead-109">See Also</span></span>  
 [<span data-ttu-id="a2ead-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="a2ead-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
