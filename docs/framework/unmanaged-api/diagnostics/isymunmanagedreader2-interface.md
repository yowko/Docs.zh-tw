---
title: ISymUnmanagedReader2 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
ms.openlocfilehash: d4c5ff46d37b1292059b18920abd8042c18bbf31
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615393"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="68156-102">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="68156-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="68156-103">表示符號讀取器，可讓您存取符號存放區中的檔、方法和變數。</span><span class="sxs-lookup"><span data-stu-id="68156-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="68156-104">這個介面會擴充[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="68156-104">This interface extends the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68156-105">方法</span><span class="sxs-lookup"><span data-stu-id="68156-105">Methods</span></span>  
  
|<span data-ttu-id="68156-106">方法</span><span class="sxs-lookup"><span data-stu-id="68156-106">Method</span></span>|<span data-ttu-id="68156-107">描述</span><span class="sxs-lookup"><span data-stu-id="68156-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68156-108">GetMethodByVersionPreRemap 方法</span><span class="sxs-lookup"><span data-stu-id="68156-108">GetMethodByVersionPreRemap Method</span></span>](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="68156-109">取得符號讀取器方法，並指定方法權杖和編輯後繼續版本號碼。</span><span class="sxs-lookup"><span data-stu-id="68156-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="68156-110">GetMethodsInDocument 方法</span><span class="sxs-lookup"><span data-stu-id="68156-110">GetMethodsInDocument Method</span></span>](isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="68156-111">取得提供的檔中具有行資訊的每一個方法。</span><span class="sxs-lookup"><span data-stu-id="68156-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="68156-112">GetSymAttributePreRemap 方法</span><span class="sxs-lookup"><span data-stu-id="68156-112">GetSymAttributePreRemap Method</span></span>](isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="68156-113">依據名稱取得自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="68156-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="68156-114">需求</span><span class="sxs-lookup"><span data-stu-id="68156-114">Requirements</span></span>  
 <span data-ttu-id="68156-115">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="68156-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68156-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68156-116">See also</span></span>

- [<span data-ttu-id="68156-117">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="68156-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="68156-118">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="68156-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
