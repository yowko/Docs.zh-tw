---
title: CorSymVarFlag 列舉
ms.date: 03/30/2017
api_name:
- CorSymVarFlag
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymVarFlag
helpviewer_keywords:
- CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c797378f5e13f39c1c786237a3a7b9cf577fccc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198851"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="9b5e3-102">CorSymVarFlag 列舉</span><span class="sxs-lookup"><span data-stu-id="9b5e3-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="9b5e3-103">指出變數是否為編譯器所產生。</span><span class="sxs-lookup"><span data-stu-id="9b5e3-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b5e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="9b5e3-104">Syntax</span></span>  
  
```  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="9b5e3-105">成員</span><span class="sxs-lookup"><span data-stu-id="9b5e3-105">Members</span></span>  
  
|<span data-ttu-id="9b5e3-106">成員</span><span class="sxs-lookup"><span data-stu-id="9b5e3-106">Member</span></span>|<span data-ttu-id="9b5e3-107">描述</span><span class="sxs-lookup"><span data-stu-id="9b5e3-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="9b5e3-108">指出指定的變數是由編譯器產生。</span><span class="sxs-lookup"><span data-stu-id="9b5e3-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b5e3-109">需求</span><span class="sxs-lookup"><span data-stu-id="9b5e3-109">Requirements</span></span>  
 <span data-ttu-id="9b5e3-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9b5e3-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b5e3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b5e3-111">See also</span></span>

- [<span data-ttu-id="9b5e3-112">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="9b5e3-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
