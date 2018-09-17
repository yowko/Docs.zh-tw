---
title: 如何：與其他應用程式共用組件 (C#)
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: a5b20061c759fd914193f24aa123317f13d31dce
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45638392"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a><span data-ttu-id="2de04-102">如何：與其他應用程式共用組件 (C#)</span><span class="sxs-lookup"><span data-stu-id="2de04-102">How to: Share an Assembly with Other Applications (C#)</span></span>
<span data-ttu-id="2de04-103">組件可以是私用或共用的︰根據預設，大多數簡單的程式由於不會供其他應用程式使用，因此只會包含一個私用組件。</span><span class="sxs-lookup"><span data-stu-id="2de04-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="2de04-104">為了與其他應用程式共用組件，必須將該組件放在[全域組件快取](../../../../framework/app-domains/gac.md) (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="2de04-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="2de04-105">共用組件</span><span class="sxs-lookup"><span data-stu-id="2de04-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="2de04-106">建立您的組件。</span><span class="sxs-lookup"><span data-stu-id="2de04-106">Create your assembly.</span></span> <span data-ttu-id="2de04-107">如需詳細資訊，請參閱[建立組件](../../../../framework/app-domains/create-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="2de04-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="2de04-108">為您的組件指派強式名稱。</span><span class="sxs-lookup"><span data-stu-id="2de04-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="2de04-109">如需詳細資訊，請參閱[如何：使用強式名稱簽署組件](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="2de04-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="2de04-110">將版本資訊指派給您的組件。</span><span class="sxs-lookup"><span data-stu-id="2de04-110">Assign version information to your assembly.</span></span> <span data-ttu-id="2de04-111">如需詳細資訊，請參閱[組件版本控制](../../../../../docs/framework/app-domains/assembly-versioning.md)。</span><span class="sxs-lookup"><span data-stu-id="2de04-111">For more information, see [Assembly Versioning](../../../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="2de04-112">將您的組件新增至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="2de04-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="2de04-113">如需詳細資訊，請參閱[如何：將組件安裝到全域組件快取](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="2de04-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="2de04-114">從其他應用程式存取組件內含的類型。</span><span class="sxs-lookup"><span data-stu-id="2de04-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="2de04-115">如需詳細資訊，請參閱[如何：參考以強式名稱命名的組件](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="2de04-115">For more information, see [How to: Reference a Strong-Named Assembly](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2de04-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="2de04-116">See Also</span></span>

- [<span data-ttu-id="2de04-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2de04-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2de04-118">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="2de04-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
