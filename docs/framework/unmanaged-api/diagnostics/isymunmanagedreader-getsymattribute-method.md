---
title: ISymUnmanagedReader::GetSymAttribute 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 26458e2512f331ff7a8c41868c99d092cfd30977
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737231"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="716f7-102">ISymUnmanagedReader::GetSymAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="716f7-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>
<span data-ttu-id="716f7-103">取得自訂屬性，根據其名稱。</span><span class="sxs-lookup"><span data-stu-id="716f7-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="716f7-104">不同於中繼資料的自訂屬性，這些自訂屬性會保存在符號存放區。</span><span class="sxs-lookup"><span data-stu-id="716f7-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="716f7-105">語法</span><span class="sxs-lookup"><span data-stu-id="716f7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="716f7-106">參數</span><span class="sxs-lookup"><span data-stu-id="716f7-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="716f7-107">[in]屬性要求的物件之中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="716f7-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="716f7-108">[in]表示要擷取的屬性變數的指標。</span><span class="sxs-lookup"><span data-stu-id="716f7-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="716f7-109">[in] `buffer` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="716f7-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="716f7-110">[out]接收屬性資料的長度變數的指標。</span><span class="sxs-lookup"><span data-stu-id="716f7-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="716f7-111">[out]此變數會接收屬性的資料指標。</span><span class="sxs-lookup"><span data-stu-id="716f7-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="716f7-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="716f7-112">Return Value</span></span>  
 <span data-ttu-id="716f7-113">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="716f7-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="716f7-114">需求</span><span class="sxs-lookup"><span data-stu-id="716f7-114">Requirements</span></span>  
 <span data-ttu-id="716f7-115">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="716f7-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="716f7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="716f7-116">See also</span></span>

- [<span data-ttu-id="716f7-117">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="716f7-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
