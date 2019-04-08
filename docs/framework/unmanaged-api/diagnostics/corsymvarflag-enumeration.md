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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198851"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="e8e80-102">CorSymVarFlag 列舉</span><span class="sxs-lookup"><span data-stu-id="e8e80-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="e8e80-103">指出變數是否為編譯器所產生。</span><span class="sxs-lookup"><span data-stu-id="e8e80-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8e80-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8e80-104">Syntax</span></span>  
  
```  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="e8e80-105">成員</span><span class="sxs-lookup"><span data-stu-id="e8e80-105">Members</span></span>  
  
|<span data-ttu-id="e8e80-106">成員</span><span class="sxs-lookup"><span data-stu-id="e8e80-106">Member</span></span>|<span data-ttu-id="e8e80-107">描述</span><span class="sxs-lookup"><span data-stu-id="e8e80-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="e8e80-108">指出指定的變數是由編譯器產生。</span><span class="sxs-lookup"><span data-stu-id="e8e80-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8e80-109">需求</span><span class="sxs-lookup"><span data-stu-id="e8e80-109">Requirements</span></span>  
 <span data-ttu-id="e8e80-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e8e80-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e80-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8e80-111">See also</span></span>

- [<span data-ttu-id="e8e80-112">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="e8e80-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
