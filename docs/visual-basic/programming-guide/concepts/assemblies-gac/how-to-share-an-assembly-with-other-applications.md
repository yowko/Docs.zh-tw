---
title: 如何： 共用組件與其他應用程式 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
ms.openlocfilehash: a7f6b49e8389108528c44d7464a2e68149dfa940
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44062893"
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="d44b5-102">如何： 共用組件與其他應用程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d44b5-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="d44b5-103">組件可以是私用或共用的︰根據預設，大多數簡單的程式由於不會供其他應用程式使用，因此只會包含一個私用組件。</span><span class="sxs-lookup"><span data-stu-id="d44b5-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="d44b5-104">為了與其他應用程式共用組件，必須將該組件放在[全域組件快取](../../../../framework/app-domains/gac.md) (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="d44b5-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="d44b5-105">共用組件</span><span class="sxs-lookup"><span data-stu-id="d44b5-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="d44b5-106">建立您的組件。</span><span class="sxs-lookup"><span data-stu-id="d44b5-106">Create your assembly.</span></span> <span data-ttu-id="d44b5-107">如需詳細資訊，請參閱[建立組件](../../../../framework/app-domains/create-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="d44b5-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="d44b5-108">為您的組件指派強式名稱。</span><span class="sxs-lookup"><span data-stu-id="d44b5-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="d44b5-109">如需詳細資訊，請參閱[如何：使用強式名稱簽署組件](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="d44b5-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="d44b5-110">將版本資訊指派給您的組件。</span><span class="sxs-lookup"><span data-stu-id="d44b5-110">Assign version information to your assembly.</span></span> <span data-ttu-id="d44b5-111">如需詳細資訊，請參閱[組件版本控制](../../../../framework/app-domains/assembly-versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="d44b5-111">For more information, see [Assembly Versioning](../../../../framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="d44b5-112">將您的組件新增至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="d44b5-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="d44b5-113">如需詳細資訊，請參閱[如何：將組件安裝到全域組件快取](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="d44b5-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="d44b5-114">從其他應用程式存取組件內含的類型。</span><span class="sxs-lookup"><span data-stu-id="d44b5-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="d44b5-115">如需詳細資訊，請參閱[如何：參考以強式名稱命名的組件](https://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813)。</span><span class="sxs-lookup"><span data-stu-id="d44b5-115">For more information, see [How to: Reference a Strong-Named Assembly](https://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d44b5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d44b5-116">See Also</span></span>  
 <span data-ttu-id="d44b5-117">[程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)[組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span><span class="sxs-lookup"><span data-stu-id="d44b5-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span></span>  
 [<span data-ttu-id="d44b5-118">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="d44b5-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
