---
title: HOW TO：與其他應用程式共用組件 (C#)
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: d440000ef509199bf69f06c2f3b5d0819e48f724
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713573"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a><span data-ttu-id="a0890-102">HOW TO：與其他應用程式共用組件 (C#)</span><span class="sxs-lookup"><span data-stu-id="a0890-102">How to: Share an Assembly with Other Applications (C#)</span></span>
<span data-ttu-id="a0890-103">組件可以是私用或共用的︰根據預設，大多數簡單的程式由於不會供其他應用程式使用，因此只會包含一個私用組件。</span><span class="sxs-lookup"><span data-stu-id="a0890-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="a0890-104">為了與其他應用程式共用組件，必須將該組件放在[全域組件快取](../../../../framework/app-domains/gac.md) (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="a0890-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="a0890-105">共用組件</span><span class="sxs-lookup"><span data-stu-id="a0890-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="a0890-106">建立您的組件。</span><span class="sxs-lookup"><span data-stu-id="a0890-106">Create your assembly.</span></span> <span data-ttu-id="a0890-107">如需詳細資訊，請參閱[建立組件](../../../../framework/app-domains/create-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="a0890-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="a0890-108">為您的組件指派強式名稱。</span><span class="sxs-lookup"><span data-stu-id="a0890-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="a0890-109">如需詳細資訊，請參閱[＜How to：使用強式名稱簽署組件](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="a0890-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="a0890-110">將版本資訊指派給您的組件。</span><span class="sxs-lookup"><span data-stu-id="a0890-110">Assign version information to your assembly.</span></span> <span data-ttu-id="a0890-111">如需詳細資訊，請參閱[組件版本控制](../../../../../docs/framework/app-domains/assembly-versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="a0890-111">For more information, see [Assembly Versioning](../../../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="a0890-112">將您的組件新增至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="a0890-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="a0890-113">如需詳細資訊，請參閱[＜How to：在全域組件快取中安裝單一組件](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="a0890-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="a0890-114">從其他應用程式存取組件內含的類型。</span><span class="sxs-lookup"><span data-stu-id="a0890-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="a0890-115">如需詳細資訊，請參閱[＜How to：參考以強式名稱命名的組件](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="a0890-115">For more information, see [How to: Reference a Strong-Named Assembly](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0890-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0890-116">See also</span></span>

- [<span data-ttu-id="a0890-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a0890-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a0890-118">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="a0890-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
