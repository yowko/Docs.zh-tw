---
title: "ISymUnmanagedReader::GetSymAttribute 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedReader.GetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9795d5c7937f3c66c799665ba0e07e70c2be0b66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="e6b74-102">ISymUnmanagedReader::GetSymAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="e6b74-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>
<span data-ttu-id="e6b74-103">取得其名稱為基礎的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="e6b74-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="e6b74-104">不同於中繼資料的自訂屬性，這些自訂屬性是存放在符號存放區。</span><span class="sxs-lookup"><span data-stu-id="e6b74-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b74-105">語法</span><span class="sxs-lookup"><span data-stu-id="e6b74-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6b74-106">參數</span><span class="sxs-lookup"><span data-stu-id="e6b74-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="e6b74-107">[in]屬性要求的物件中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e6b74-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="e6b74-108">[in]要擷取的屬性會指出變數的指標。</span><span class="sxs-lookup"><span data-stu-id="e6b74-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="e6b74-109">[in] `buffer` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="e6b74-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="e6b74-110">[out]接收屬性資料的長度變數的指標。</span><span class="sxs-lookup"><span data-stu-id="e6b74-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="e6b74-111">[out]此變數會接收屬性資料指標。</span><span class="sxs-lookup"><span data-stu-id="e6b74-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6b74-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="e6b74-112">Return Value</span></span>  
 <span data-ttu-id="e6b74-113">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼...</span><span class="sxs-lookup"><span data-stu-id="e6b74-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code..</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6b74-114">需求</span><span class="sxs-lookup"><span data-stu-id="e6b74-114">Requirements</span></span>  
 <span data-ttu-id="e6b74-115">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e6b74-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6b74-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="e6b74-116">See Also</span></span>  
 [<span data-ttu-id="e6b74-117">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="e6b74-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
