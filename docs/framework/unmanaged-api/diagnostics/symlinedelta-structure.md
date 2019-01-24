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
ms.openlocfilehash: 2d534ae381e0dc105731cf0a537f81afe80d87e0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732735"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="5af6b-102">SYMLINEDELTA 結構</span><span class="sxs-lookup"><span data-stu-id="5af6b-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="5af6b-103">提供符號處理常式已因編輯而移動的方法相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="5af6b-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5af6b-104">語法</span><span class="sxs-lookup"><span data-stu-id="5af6b-104">Syntax</span></span>  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="5af6b-105">成員</span><span class="sxs-lookup"><span data-stu-id="5af6b-105">Members</span></span>  
  
|<span data-ttu-id="5af6b-106">成員</span><span class="sxs-lookup"><span data-stu-id="5af6b-106">Member</span></span>|<span data-ttu-id="5af6b-107">描述</span><span class="sxs-lookup"><span data-stu-id="5af6b-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="5af6b-108">方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5af6b-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="5af6b-109">此方法已移動的行數。</span><span class="sxs-lookup"><span data-stu-id="5af6b-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5af6b-110">需求</span><span class="sxs-lookup"><span data-stu-id="5af6b-110">Requirements</span></span>  
 <span data-ttu-id="5af6b-111">**標頭：** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="5af6b-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5af6b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5af6b-112">See also</span></span>
- [<span data-ttu-id="5af6b-113">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="5af6b-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
