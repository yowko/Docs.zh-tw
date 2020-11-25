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
ms.openlocfilehash: 075d46b0bbc68add0203daf7430afb712c998fe0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700973"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="d45af-102">ISymUnmanagedDocument::GetLanguage 方法</span><span class="sxs-lookup"><span data-stu-id="d45af-102">ISymUnmanagedDocument::GetLanguage Method</span></span>

<span data-ttu-id="d45af-103">取得此檔的語言識別項</span><span class="sxs-lookup"><span data-stu-id="d45af-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d45af-104">語法</span><span class="sxs-lookup"><span data-stu-id="d45af-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d45af-105">參數</span><span class="sxs-lookup"><span data-stu-id="d45af-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="d45af-106">擴展接收語言識別項之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="d45af-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d45af-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d45af-107">Return Value</span></span>  

 <span data-ttu-id="d45af-108">如果方法成功，則為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="d45af-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d45af-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d45af-109">See also</span></span>

- [<span data-ttu-id="d45af-110">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="d45af-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
