---
title: "CorSymVarFlag 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSymVarFlag
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSymVarFlag
helpviewer_keywords: CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: edbbc8109eb44494c7f4fac0ed8756e23bdc955b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="abb18-102">CorSymVarFlag 列舉</span><span class="sxs-lookup"><span data-stu-id="abb18-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="abb18-103">指出變數是否為編譯器產生。</span><span class="sxs-lookup"><span data-stu-id="abb18-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abb18-104">語法</span><span class="sxs-lookup"><span data-stu-id="abb18-104">Syntax</span></span>  
  
```  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="abb18-105">成員</span><span class="sxs-lookup"><span data-stu-id="abb18-105">Members</span></span>  
  
|<span data-ttu-id="abb18-106">成員</span><span class="sxs-lookup"><span data-stu-id="abb18-106">Member</span></span>|<span data-ttu-id="abb18-107">說明</span><span class="sxs-lookup"><span data-stu-id="abb18-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="abb18-108">指出指定的變數是由編譯器產生。</span><span class="sxs-lookup"><span data-stu-id="abb18-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="abb18-109">需求</span><span class="sxs-lookup"><span data-stu-id="abb18-109">Requirements</span></span>  
 <span data-ttu-id="abb18-110">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="abb18-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abb18-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abb18-111">See Also</span></span>  
 [<span data-ttu-id="abb18-112">診斷符號存放區列舉型別</span><span class="sxs-lookup"><span data-stu-id="abb18-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
