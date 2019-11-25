---
title: 自訂專案和擴充 My 物件
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 06ca80b9-1192-4eb5-8537-8ef5edfb9be0
ms.openlocfilehash: e6ed43aeff90295f71590bcee180ca1e0f88e5ff
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330332"
---
# <a name="customizing-projects-and-extending-my-with-visual-basic"></a><span data-ttu-id="801ad-102">使用 Visual Basic 自訂專案和擴充 My 物件</span><span class="sxs-lookup"><span data-stu-id="801ad-102">Customizing Projects and Extending My with Visual Basic</span></span>

<span data-ttu-id="801ad-103">You can customize project templates to provide additional `My` objects.</span><span class="sxs-lookup"><span data-stu-id="801ad-103">You can customize project templates to provide additional `My` objects.</span></span> <span data-ttu-id="801ad-104">This makes it easy for other developers to find and use your objects.</span><span class="sxs-lookup"><span data-stu-id="801ad-104">This makes it easy for other developers to find and use your objects.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="801ad-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="801ad-105">In this section</span></span>

- [<span data-ttu-id="801ad-106">擴充 Visual Basic 中的 My 命名空間</span><span class="sxs-lookup"><span data-stu-id="801ad-106">Extending the My Namespace in Visual Basic</span></span>](extending-the-my-namespace.md)  
 <span data-ttu-id="801ad-107">Describes how to add custom members and values to the `My` namespace in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="801ad-107">Describes how to add custom members and values to the `My` namespace in Visual Basic.</span></span>
- [<span data-ttu-id="801ad-108">封裝和部署自訂的 My 擴充</span><span class="sxs-lookup"><span data-stu-id="801ad-108">Packaging and Deploying Custom My Extensions</span></span>](packaging-and-deploying-custom-my-extensions.md)  
 <span data-ttu-id="801ad-109">Describes how to publish custom `My` namespace extensions by using Visual Studio templates.</span><span class="sxs-lookup"><span data-stu-id="801ad-109">Describes how to publish custom `My` namespace extensions by using Visual Studio templates.</span></span>
- [<span data-ttu-id="801ad-110">擴充 Visual Basic 應用程式模型</span><span class="sxs-lookup"><span data-stu-id="801ad-110">Extending the Visual Basic Application Model</span></span>](extending-the-visual-basic-application-model.md)  
 <span data-ttu-id="801ad-111">Describes how to specify your own extensions to the application model by overriding members of the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class.</span><span class="sxs-lookup"><span data-stu-id="801ad-111">Describes how to specify your own extensions to the application model by overriding members of the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class.</span></span>
- [<span data-ttu-id="801ad-112">自訂 My 中可用的物件</span><span class="sxs-lookup"><span data-stu-id="801ad-112">Customizing Which Objects are Available in My</span></span>](customizing-which-objects-are-available-in-my.md)  
 <span data-ttu-id="801ad-113">Describes how to control which `My` objects are enabled by setting your project's \_MYTYPE conditional-compilation constant.</span><span class="sxs-lookup"><span data-stu-id="801ad-113">Describes how to control which `My` objects are enabled by setting your project's \_MYTYPE conditional-compilation constant.</span></span>

## <a name="related-sections"></a><span data-ttu-id="801ad-114">相關章節</span><span class="sxs-lookup"><span data-stu-id="801ad-114">Related sections</span></span>

- [<span data-ttu-id="801ad-115">使用 My 進行開發</span><span class="sxs-lookup"><span data-stu-id="801ad-115">Development with My</span></span>](../development-with-my/index.md)  
 <span data-ttu-id="801ad-116">Describes which `My` objects are available in different project types by default.</span><span class="sxs-lookup"><span data-stu-id="801ad-116">Describes which `My` objects are available in different project types by default.</span></span>
- [<span data-ttu-id="801ad-117">Visual Basic 應用程式模型概觀</span><span class="sxs-lookup"><span data-stu-id="801ad-117">Overview of the Visual Basic Application Model</span></span>](../development-with-my/overview-of-the-visual-basic-application-model.md)  
 <span data-ttu-id="801ad-118">Describes Visual Basic's model for controlling the behavior of Windows Forms applications.</span><span class="sxs-lookup"><span data-stu-id="801ad-118">Describes Visual Basic's model for controlling the behavior of Windows Forms applications.</span></span>
- [<span data-ttu-id="801ad-119">My 如何相依於專案類型</span><span class="sxs-lookup"><span data-stu-id="801ad-119">How My Depends on Project Type</span></span>](../development-with-my/how-my-depends-on-project-type.md)  
 <span data-ttu-id="801ad-120">Describes which `My` objects are available in different project types by default.</span><span class="sxs-lookup"><span data-stu-id="801ad-120">Describes which `My` objects are available in different project types by default.</span></span>
- [<span data-ttu-id="801ad-121">條件式編譯</span><span class="sxs-lookup"><span data-stu-id="801ad-121">Conditional Compilation</span></span>](../../programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="801ad-122">Discusses how the compiler uses conditional-compilation to select particular sections of code to compile and exclude other sections.</span><span class="sxs-lookup"><span data-stu-id="801ad-122">Discusses how the compiler uses conditional-compilation to select particular sections of code to compile and exclude other sections.</span></span>
- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <span data-ttu-id="801ad-123">Describes the `My` object that provides properties, methods, and events related to the current application.</span><span class="sxs-lookup"><span data-stu-id="801ad-123">Describes the `My` object that provides properties, methods, and events related to the current application.</span></span>

## <a name="see-also"></a><span data-ttu-id="801ad-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="801ad-124">See also</span></span>

- [<span data-ttu-id="801ad-125">使用 Visual Basic 開發應用程式</span><span class="sxs-lookup"><span data-stu-id="801ad-125">Developing Applications with Visual Basic</span></span>](../index.md)
