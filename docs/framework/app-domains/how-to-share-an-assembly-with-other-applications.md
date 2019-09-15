---
title: HOW TO：與其他應用程式共用元件
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b1ef195458dd2de95eeb5e25089339e55d9e3fbb
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972946"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a><span data-ttu-id="78681-102">作法：與其他應用程式共用元件</span><span class="sxs-lookup"><span data-stu-id="78681-102">How to: Share an assembly with other applications</span></span>
<span data-ttu-id="78681-103">組件可以是私用或共用的︰根據預設，大多數簡單的程式由於不會供其他應用程式使用，因此只會包含一個私用組件。</span><span class="sxs-lookup"><span data-stu-id="78681-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  

<span data-ttu-id="78681-104">若要與其他應用程式共用元件，必須將它放在[全域組件快取（GAC）](gac.md)中。</span><span class="sxs-lookup"><span data-stu-id="78681-104">In order to share an assembly with other applications, it must be placed in the [global assembly cache (GAC)](gac.md).</span></span>  
  
<span data-ttu-id="78681-105">若要共用元件：</span><span class="sxs-lookup"><span data-stu-id="78681-105">To share an assembly:</span></span>
  
1. <span data-ttu-id="78681-106">建立您的組件。</span><span class="sxs-lookup"><span data-stu-id="78681-106">Create your assembly.</span></span> <span data-ttu-id="78681-107">如需詳細資訊，請參閱[建立元件](../../standard/assembly/create.md)。</span><span class="sxs-lookup"><span data-stu-id="78681-107">For more information, see [Create assemblies](../../standard/assembly/create.md).</span></span>  
  
2. <span data-ttu-id="78681-108">為您的組件指派強式名稱。</span><span class="sxs-lookup"><span data-stu-id="78681-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="78681-109">如需詳細資訊，請參閱[如何：使用強式名稱簽署組件](../../standard/assembly/sign-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="78681-109">For more information, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>  
  
3. <span data-ttu-id="78681-110">將版本資訊指派給您的組件。</span><span class="sxs-lookup"><span data-stu-id="78681-110">Assign version information to your assembly.</span></span> <span data-ttu-id="78681-111">如需詳細資訊，請參閱[元件版本控制](../../standard/assembly/versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="78681-111">For more information, see [Assembly versioning](../../standard/assembly/versioning.md).</span></span>  
  
4. <span data-ttu-id="78681-112">將您的元件加入至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="78681-112">Add your assembly to the global assembly cache.</span></span> <span data-ttu-id="78681-113">如需詳細資訊，請參閱[如何：將元件安裝到全域組件快取](install-assembly-into-gac.md)中。</span><span class="sxs-lookup"><span data-stu-id="78681-113">For more information, see [How to: Install an assembly into the global assembly cache](install-assembly-into-gac.md).</span></span>  
  
5. <span data-ttu-id="78681-114">從其他應用程式存取元件中包含的類型。</span><span class="sxs-lookup"><span data-stu-id="78681-114">Access the types contained in the assembly from other applications.</span></span> <span data-ttu-id="78681-115">如需詳細資訊，請參閱[如何：參考強式名稱的元件](../../standard/assembly/reference-strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="78681-115">For more information, see [How to: Reference a strong-named assembly](../../standard/assembly/reference-strong-named.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78681-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78681-116">See also</span></span>

- [<span data-ttu-id="78681-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="78681-117">C# programming guide</span></span>](../../../api/index.md)
- [<span data-ttu-id="78681-118">程式設計概念（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="78681-118">Programming concepts (Visual Basic)</span></span>](../../../api/index.md)
- [<span data-ttu-id="78681-119">具有元件的程式</span><span class="sxs-lookup"><span data-stu-id="78681-119">Program with assemblies</span></span>](../../standard/assembly/program.md)
