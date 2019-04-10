---
title: SYMLINEDELTA 結構
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fabc8f77b12865d0d971b5934d7de27b52f3e813
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159480"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="58d5f-102">SYMLINEDELTA 結構</span><span class="sxs-lookup"><span data-stu-id="58d5f-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="58d5f-103">提供符號處理常式已因編輯而移動的方法相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="58d5f-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58d5f-104">語法</span><span class="sxs-lookup"><span data-stu-id="58d5f-104">Syntax</span></span>  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="58d5f-105">成員</span><span class="sxs-lookup"><span data-stu-id="58d5f-105">Members</span></span>  
  
|<span data-ttu-id="58d5f-106">成員</span><span class="sxs-lookup"><span data-stu-id="58d5f-106">Member</span></span>|<span data-ttu-id="58d5f-107">描述</span><span class="sxs-lookup"><span data-stu-id="58d5f-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="58d5f-108">方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="58d5f-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="58d5f-109">此方法已移動的行數。</span><span class="sxs-lookup"><span data-stu-id="58d5f-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="58d5f-110">需求</span><span class="sxs-lookup"><span data-stu-id="58d5f-110">Requirements</span></span>  
 <span data-ttu-id="58d5f-111">**標頭：** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="58d5f-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58d5f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58d5f-112">See also</span></span>

- [<span data-ttu-id="58d5f-113">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="58d5f-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
