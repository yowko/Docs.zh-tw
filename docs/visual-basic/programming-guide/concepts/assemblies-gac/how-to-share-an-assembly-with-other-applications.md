---
title: 如何： 共用組件與其他應用程式 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
ms.openlocfilehash: 3d29a3558a64c02fc8c59035f2fee5c64c4a776f
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47089408"
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="73808-102">如何： 共用組件與其他應用程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73808-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="73808-103">組件可以是私用或共用的︰根據預設，大多數簡單的程式由於不會供其他應用程式使用，因此只會包含一個私用組件。</span><span class="sxs-lookup"><span data-stu-id="73808-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="73808-104">為了與其他應用程式共用組件，必須將該組件放在[全域組件快取](../../../../framework/app-domains/gac.md) (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="73808-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="73808-105">共用組件</span><span class="sxs-lookup"><span data-stu-id="73808-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="73808-106">建立您的組件。</span><span class="sxs-lookup"><span data-stu-id="73808-106">Create your assembly.</span></span> <span data-ttu-id="73808-107">如需詳細資訊，請參閱[建立組件](../../../../framework/app-domains/create-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="73808-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="73808-108">為您的組件指派強式名稱。</span><span class="sxs-lookup"><span data-stu-id="73808-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="73808-109">如需詳細資訊，請參閱[如何：使用強式名稱簽署組件](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="73808-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="73808-110">將版本資訊指派給您的組件。</span><span class="sxs-lookup"><span data-stu-id="73808-110">Assign version information to your assembly.</span></span> <span data-ttu-id="73808-111">如需詳細資訊，請參閱[組件版本控制](../../../../framework/app-domains/assembly-versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="73808-111">For more information, see [Assembly Versioning](../../../../framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="73808-112">將您的組件新增至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="73808-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="73808-113">如需詳細資訊，請參閱[如何：將組件安裝到全域組件快取](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="73808-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="73808-114">從其他應用程式存取組件內含的類型。</span><span class="sxs-lookup"><span data-stu-id="73808-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="73808-115">如需詳細資訊，請參閱[如何：參考以強式名稱命名的組件](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="73808-115">For more information, see [How to: Reference a Strong-Named Assembly](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73808-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73808-116">See also</span></span>

- [<span data-ttu-id="73808-117">程式設計概念</span><span class="sxs-lookup"><span data-stu-id="73808-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="73808-118">組件和全域組件快取 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73808-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
- [<span data-ttu-id="73808-119">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="73808-119">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
