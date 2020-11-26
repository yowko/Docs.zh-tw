---
title: 作法：與其他應用程式共用組件
description: 瞭解如何在 .NET 中與其他應用程式共用元件。 元件可以是私用 (預設) 或共用。 若要共用元件，請將它放在 GAC 中。
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 1056f8b555713d5d67488537e6c06cc457c4d312
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242535"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a><span data-ttu-id="51c27-105">作法：與其他應用程式共用組件</span><span class="sxs-lookup"><span data-stu-id="51c27-105">How to: Share an assembly with other applications</span></span>

<span data-ttu-id="51c27-106">組件可以是私用或共用的︰根據預設，大多數簡單的程式由於不會供其他應用程式使用，因此只會包含一個私用組件。</span><span class="sxs-lookup"><span data-stu-id="51c27-106">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  

<span data-ttu-id="51c27-107">為了與其他應用程式共用元件，必須將它放在 [全域組件快取 (GAC) ](gac.md)中。</span><span class="sxs-lookup"><span data-stu-id="51c27-107">In order to share an assembly with other applications, it must be placed in the [global assembly cache (GAC)](gac.md).</span></span>  
  
<span data-ttu-id="51c27-108">若要共用元件：</span><span class="sxs-lookup"><span data-stu-id="51c27-108">To share an assembly:</span></span>
  
1. <span data-ttu-id="51c27-109">建立您的組件。</span><span class="sxs-lookup"><span data-stu-id="51c27-109">Create your assembly.</span></span> <span data-ttu-id="51c27-110">如需詳細資訊，請參閱 [建立元件](../../standard/assembly/create.md)。</span><span class="sxs-lookup"><span data-stu-id="51c27-110">For more information, see [Create assemblies](../../standard/assembly/create.md).</span></span>  
  
2. <span data-ttu-id="51c27-111">為您的組件指派強式名稱。</span><span class="sxs-lookup"><span data-stu-id="51c27-111">Assign a strong name to your assembly.</span></span> <span data-ttu-id="51c27-112">如需詳細資訊，請參閱 [如何：使用強式名稱簽署元件](../../standard/assembly/sign-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="51c27-112">For more information, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>  
  
3. <span data-ttu-id="51c27-113">將版本資訊指派給您的組件。</span><span class="sxs-lookup"><span data-stu-id="51c27-113">Assign version information to your assembly.</span></span> <span data-ttu-id="51c27-114">如需詳細資訊，請參閱 [元件版本控制](../../standard/assembly/versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="51c27-114">For more information, see [Assembly versioning](../../standard/assembly/versioning.md).</span></span>  
  
4. <span data-ttu-id="51c27-115">將您的元件加入至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="51c27-115">Add your assembly to the global assembly cache.</span></span> <span data-ttu-id="51c27-116">如需詳細資訊，請參閱 [如何：將元件安裝到全域組件快取](install-assembly-into-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="51c27-116">For more information, see [How to: Install an assembly into the global assembly cache](install-assembly-into-gac.md).</span></span>  
  
5. <span data-ttu-id="51c27-117">從其他應用程式存取元件中包含的類型。</span><span class="sxs-lookup"><span data-stu-id="51c27-117">Access the types contained in the assembly from other applications.</span></span> <span data-ttu-id="51c27-118">如需詳細資訊，請參閱 [如何：參考強式名稱的元件](../../standard/assembly/reference-strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="51c27-118">For more information, see [How to: Reference a strong-named assembly](../../standard/assembly/reference-strong-named.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51c27-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51c27-119">See also</span></span>

- [<span data-ttu-id="51c27-120">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="51c27-120">C# programming guide</span></span>](../../../api/index.md)
- [<span data-ttu-id="51c27-121"> (Visual Basic) 的程式設計概念 </span><span class="sxs-lookup"><span data-stu-id="51c27-121">Programming concepts (Visual Basic)</span></span>](../../../api/index.md)
- [<span data-ttu-id="51c27-122">具有組件的程式</span><span class="sxs-lookup"><span data-stu-id="51c27-122">Program with assemblies</span></span>](../../standard/assembly/index.md)
