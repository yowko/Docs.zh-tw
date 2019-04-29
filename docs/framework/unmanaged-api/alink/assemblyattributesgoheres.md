---
title: AssemblyAttributesGoHereS
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereS
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereS
helpviewer_keywords:
- AssemblyAttributesGoHereS type
- Alink API, AssemblyAttributesGoHereS type
ms.assetid: 4e817f35-a2bc-4403-9e6f-f731e6b9fe23
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74447f52c75ae22e513c6f07950630d37bad191a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790113"
---
# <a name="assemblyattributesgoheres"></a><span data-ttu-id="75d17-102">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="75d17-102">AssemblyAttributesGoHereS</span></span>

<span data-ttu-id="75d17-103">供 ALink 用來做為儲存自訂屬性相關資訊的預留位置。</span><span class="sxs-lookup"><span data-stu-id="75d17-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="75d17-104">語法</span><span class="sxs-lookup"><span data-stu-id="75d17-104">Syntax</span></span>

```
internal sealed class AssemblyAttributesGoHereS
```

## <a name="remarks"></a><span data-ttu-id="75d17-105">備註</span><span class="sxs-lookup"><span data-stu-id="75d17-105">Remarks</span></span>

<span data-ttu-id="75d17-106">這個類型的參考可能會內嵌在來源中包含組件自訂屬性的 netmodule 中。</span><span class="sxs-lookup"><span data-stu-id="75d17-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="75d17-107">從一個或多個包含這些類型參考的 netmodule 建置組件資訊清單時，ALink 會使用附加至這些參考的資訊來發出真正的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="75d17-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="75d17-108">因此，這個類型永遠不會具現化，而其參考只會用來做為建置流程的一部分，在最後的組件中並沒有任何用途。</span><span class="sxs-lookup"><span data-stu-id="75d17-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="75d17-109">這個類型的參考會指出與安全性相關且不是多用途的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="75d17-109">References to this type indicate custom attributes that are security related and are not multiple-use.</span></span>

<span data-ttu-id="75d17-110">這些類型會標示 「 內部 」 在.NET Framework 中，位於<xref:System.Runtime.CompilerServices>命名空間。</span><span class="sxs-lookup"><span data-stu-id="75d17-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="75d17-111">需求</span><span class="sxs-lookup"><span data-stu-id="75d17-111">Requirements</span></span>

<span data-ttu-id="75d17-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="75d17-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="75d17-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75d17-113">See also</span></span>

- [<span data-ttu-id="75d17-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="75d17-114">AssemblyAttributesGoHere</span></span>](assemblyattributesgohere.md)
- [<span data-ttu-id="75d17-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="75d17-115">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="75d17-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="75d17-116">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
