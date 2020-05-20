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
ms.openlocfilehash: 084f3ae12d906f5e80fdb86e65b09d2371fd246b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614587"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="09976-102">ISymUnmanagedDocument::GetLanguage 方法</span><span class="sxs-lookup"><span data-stu-id="09976-102">ISymUnmanagedDocument::GetLanguage Method</span></span>
<span data-ttu-id="09976-103">取得此檔的語言識別項</span><span class="sxs-lookup"><span data-stu-id="09976-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09976-104">語法</span><span class="sxs-lookup"><span data-stu-id="09976-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09976-105">參數</span><span class="sxs-lookup"><span data-stu-id="09976-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="09976-106">脫銷接收語言識別項之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="09976-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09976-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="09976-107">Return Value</span></span>  
 <span data-ttu-id="09976-108">如果方法成功，則 S_OK。</span><span class="sxs-lookup"><span data-stu-id="09976-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09976-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09976-109">See also</span></span>

- [<span data-ttu-id="09976-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="09976-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
