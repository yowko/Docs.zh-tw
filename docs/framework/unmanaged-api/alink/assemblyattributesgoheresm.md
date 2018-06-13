---
title: AssemblyAttributesGoHereSM
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHereSM
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyAttributesGoHereSM
helpviewer_keywords:
- AssemblyAttributesGoHereSM type
- Alink API, AssemblyAttributesGoHereSM type
ms.assetid: 4cf9bf39-1527-49e0-a0e9-55e7a018bf66
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bed903c7380bc73601f03a83d2c637ef34d9b9e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405210"
---
# <a name="assemblyattributesgoheresm"></a><span data-ttu-id="b6b86-102">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="b6b86-102">AssemblyAttributesGoHereSM</span></span>
<span data-ttu-id="b6b86-103">供 ALink 用來做為儲存自訂屬性相關資訊的預留位置。</span><span class="sxs-lookup"><span data-stu-id="b6b86-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6b86-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6b86-104">Syntax</span></span>  
  
```  
AssemblyAttributeGoHereSM  
```  
  
## <a name="remarks"></a><span data-ttu-id="b6b86-105">備註</span><span class="sxs-lookup"><span data-stu-id="b6b86-105">Remarks</span></span>  
 <span data-ttu-id="b6b86-106">這個類型的參考可能會內嵌在來源中包含組件自訂屬性的 netmodule 中。</span><span class="sxs-lookup"><span data-stu-id="b6b86-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="b6b86-107">從一個或多個包含這些類型參考的 netmodule 建置組件資訊清單時，ALink 會使用附加至這些參考的資訊來發出真正的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="b6b86-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="b6b86-108">因此，這個類型永遠不會具現化，而其參考只會用來做為建置流程的一部分，在最後的組件中並沒有任何用途。</span><span class="sxs-lookup"><span data-stu-id="b6b86-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="b6b86-109">這個類型的參考會指出與安全性相關且多用途的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="b6b86-109">References to this type indicate custom attributes that are security related and multiple-use.</span></span>  
  
 <span data-ttu-id="b6b86-110">這些類型會在 .NET Framework 中標示為「內部」，其位於 <xref:System.Runtime.CompilerServices>。</span><span class="sxs-lookup"><span data-stu-id="b6b86-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6b86-111">需求</span><span class="sxs-lookup"><span data-stu-id="b6b86-111">Requirements</span></span>  
 <span data-ttu-id="b6b86-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="b6b86-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b86-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6b86-113">See Also</span></span>  
 [<span data-ttu-id="b6b86-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="b6b86-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [<span data-ttu-id="b6b86-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="b6b86-115">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [<span data-ttu-id="b6b86-116">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="b6b86-116">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)
